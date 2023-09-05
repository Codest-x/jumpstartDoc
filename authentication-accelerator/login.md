# Authentication Accelerator - Login Page

![Login Page](../assets/loginPage.png)

The Login page in the Authentication Accelerator allows users to securely log in to your application. This documentation will walk you through implementing and using the Login function, along with essential requests and dependencies.

## Login Function

The `accAuthLogin` function is responsible for user login and authentication. When a user logs in, this function is called to initiate the login process. Here's an annotated code snippet explaining how it works:

```javascript
// Construct the data object to pass to the loginRequest
let data = {
  variables: {
    email: email,
    password: password,
    authProfileId: authInfo.value.authProfileId
  }
}

try {
  // Call the login request
  const result = await accAuthLoginRequest.run(data);

  // Handle login success
  if (result) {
    // Update user information
    accAuthUserInfo.setValue({
      ...accAuthUserInfo.value,
      idToken: result.userLogin.auth.idToken,
    });

    // Store authentication tokens in local storage
    localStorage.setItem('tokenID', result.userLogin.auth.idToken)
    localStorage.setItem('refreshToken', result.userLogin.auth.refreshToken)

    // Check if the user exists
    const userExist = await accUserGet(email);

    if (userExist) {
      // Navigate to the home page
      router.navigate('/');
      // Show a welcome message
      accSnackbarState.setValue({
        open: true,
        message: `Welcome back, 
        ${JSON.parse(localStorage.getItem('userData'))?.firstName} 
        ${JSON.parse(localStorage.getItem('userData'))?.lastName}`,
        type: "default"
      });
    }
  } else {
    // Handle login failure
    accSnackbarState.setValue({
      open: true,
      message: "Email or password incorrect.",
      type: "error"
    });
    return;
  }
} catch (error) {
  // Handle errors
  accSnackbarState.setValue({
    open: true,
    message: "Email or password incorrect.",
    type: "error"
  });
  return false;
}
```


## LoginRequest

The `accAuthLoginRequest` is a GraphQL mutation used for user login. It takes the user's email, password, and authentication profile ID as input parameters and returns authentication tokens. Here's the request:

```graphql
mutation LoginRequest (
  $email: String!
  $password: String!
  $authProfileId: ID!
) {
  userLogin(
    data: {
      email: $email
      password: $password
      authProfileId: $authProfileId
    }
  ) {
    auth {
      refreshToken
      idToken
    }
  }
}
```

This request is crucial for the login process as it authenticates the user and provides the necessary tokens for subsequent API requests.

## UserGetByEmail

The `accUserGetByEmail` GraphQL query is used to retrieve user information based on their email address. It's used to check if a user with the provided email exists in your application.

```gql
query accUserGetByEmail(
  $email: String!
) {
  user(email: $email) {
    roles {
      items {
        name
      }
    }
    avatar {
      id
      downloadUrl
      filename
    }
    firstName
    id
    is8base
    lastName
    origin
    createdAt
    email
    timezone
    phoneNumber
  }
}
```
