# Authentication Accelerator - Signup Page

![Signup Page](../assets/signupPage.png)

The Signup page in the Authentication Accelerator allows new users to register and create an account. This documentation will guide you through implementing and using the Signup function, along with the necessary requests and dependencies.

## Signup Function

The `accAuthSignup` function enables users to sign up with their email and password and then logs them in. Here's an annotated code snippet explaining how it works:

```javascript
/**
 * Function to sign up a user with email and password and then log them in
 * @param {string} email - The user's email address.
 * @param {string} lastName - The user's last name.
 * @param {string} firstName - The user's first name.
 * @param {string} password - The user's chosen password.
 */
// Create a data object to pass to signUpWithPasswordRequest
const data = {
  variables: {
    email,
    lastName,
    firstName,
    password,
    authProfileId: authInfo.value.authProfileId
  }
};

// Call signUpWithPasswordRequest and then log the user in
accAuthSignupRequest.run(data)
  .then((res) => {
    if (!!res) {
      // If the signup is successful, automatically log the user in
      accAuthLogin(res?.userSignUpWithPassword?.email, password)
    } else {
      // If the signup fails, display an error message
      accSnackbarState.setValue({
        open: true,
        message: "A user with this email already exists.",
        type: "error"
      });
    }
  }).catch(() => {
    // Handle errors, typically network issues or unexpected failures
    accSnackbarState.setValue({
      open: true,
      message: "A user with this email already exists.",
      type: "error"
    });
  });
```

## Signup Request

The `accAuthSignupRequest` is a GraphQL mutation used for user signup. It takes the user's email, first name, last name, and password as input parameters and creates a new user account. Here's the request:

```gql
mutation UserSignUpWithPassword(
  $email: String!
  $password: String!
  $firstName: String!
  $lastName: String!
  $authProfileId: ID!
) {
  userSignUpWithPassword(
    user: {
      email: $email
      firstName: $firstName
      lastName: $lastName
    }
    authProfileId: $authProfileId
    password: $password
  ) {
    id
    email
  }
}

```

## Login Request

The `accAuthLoginRequest` is a GraphQL mutation used for user login. It takes the user's email, password, and authentication profile ID as input parameters and returns authentication tokens. Here's the request:

```gql
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

This request is used to log in the user after a successful signup.

By following this documentation, you can implement a secure and user-friendly signup process in your application using the Authentication Accelerator's Signup Page.
