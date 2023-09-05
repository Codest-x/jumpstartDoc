# Jumpstart your project with accelerators

Welcome to the Accelerators documentation for 8base, your one-stop guide to quickly kickstarting your React application development with our predefined accelerator components. These accelerators are designed to save you time and effort by providing a structured foundation for common app functionalities.

## Naming Convention for Accelerators

At 8base, we follow a consistent naming convention for all states, requests, functions, and pages to make your development process smoother and more organized. Our convention is as follows:

- **Authentication (Auth)**: Identifier for Authentication related components.
- **Navigation (Nav)**: Identifier for Navigation components.
- **User Management (User)**: Identifier for User Management components.
- **Theme Management (Theme)**: Identifier for Theme Management components.

Each accelerator's identifier is prefixed with "acc," followed by the accelerator's identifier, and then the name of the specific function, request, state, or page. Here's an example:

- `accAuthLogin`: A function related to the Authentication accelerator's login functionality.
- `accNavSidebarGroups`: A state related to the Navigation accelerator's sidebar groups.

This naming convention helps you easily identify and manage various components within your project.

## Table of Contents

1. [Authentication Accelerator](#authentication-accelerator)
2. [User Management Accelerator](#user-management-accelerator)
3. [Navigation Accelerator](#navigation-accelerator)
4. [Theme Management Accelerator](#theme-management-accelerator)

## Authentication Accelerator

The Authentication Accelerator simplifies the implementation of user authentication and related pages. Click on each link below to explore the individual pages and their associated states:

### Pages

- [Login](./authentication-accelerator/login.md)
- [Signup](./authentication-accelerator/signup.md)
- [Forgot Password](./authentication-accelerator/forgot-password.md)
- [Logout](./authentication-accelerator/logout.md)

### States

- `accAuthUserInfo`: State related to the user's authentication information.
- `accAuthLogoutModal`: State related to the user logout confirmation modal.

## User Management Accelerator

The User Management Accelerator simplifies the implementation of user management functionality, including CRUD (Create, Read, Update, Delete) operations. Explore the individual pages and their associated states below:

### Pages

- [User Profile](./user-management-accelerator/user-profile.md)
- [User Create](./user-management-accelerator/user-create.md)
- [Team Members](./user-management-accelerator/team-members.md)
- [My Account](./user-management-accelerator/my-account.md)

### States

- `accUserAccountSettingsAvatar`: State related to the user's account settings avatar.
- `accUserDeleteModal`: State related to the user delete confirmation modal.
- `accUserGeneralTab`: State related to the general user profile tab.
- `accUserHeaderAvatar`: State related to the user's header avatar.
- `accUserManagementTab`: State related to the user management tab.
- `accUserToDelete`: State related to the user to be deleted.

The User Management Accelerator empowers you to perform CRUD operations, making it effortless to manage members of your platform. Whether you need to create, read, update, or delete user profiles, this accelerator streamlines the process for a seamless user management experience.

Stay tuned as we provide comprehensive documentation for each page and state within the User Management Accelerator, helping you make the most of its capabilities.

### Navigation Accelerator

The Navigation Accelerator forms the backbone of your application's navigation structure, providing essential elements for easy navigation between pages. Explore the components and states below:

#### Components

- **Sidebar**: A collapsible sidebar menu to navigate various sections of your application.
- **Breadcrumb Navigation**: A breadcrumb trail to track and navigate your current location within the app.

#### States

- `accNavBreadcrumbs`: State related to the breadcrumb navigation.
- `accNavSidebarGroups`: State related to the sidebar menu groups.
- `accIsSidebarOpen`: State to manage the visibility of the sidebar.

The Navigation Accelerator plays a crucial role in providing a seamless user experience by enabling efficient navigation throughout your application. Whether it's tracking your location with breadcrumbs or accessing different sections through the sidebar, this accelerator enhances the user journey.

Stay tuned as we provide detailed documentation on how to leverage the Navigation Accelerator effectively.

### Theme Management Accelerator

The Theme Management Accelerator offers a consistent and visually appealing design for your application. It enables you to easily customize and manage your app's themes and styles. Explore the key features below:

#### Features

- **Theme Customization**: Customize the color schemes, fonts, and styles of your application.
- **Dark Mode Support**: Implement dark mode for users who prefer a different look.

#### States

- `accThemePrimaryColor`: State for managing the primary color theme.
- `accThemeSecondaryColor`: State for managing the secondary color theme.
- `accThemeFontFamily`: State for specifying the font family.
- `accThemeDarkMode`: State for enabling and managing dark mode.

The Theme Management Accelerator empowers you to create a visually appealing and user-friendly application. Customize the look and feel of your app to match your brand or design preferences.

Stay tuned as we provide comprehensive documentation on how to customize themes and styles using the Theme Management Accelerator.

With these explanations, users will understand the significance of the Navigation and Theme Management Accelerators and how they contribute to the overall user experience and design of their applications.