# Configurations

Wave has many configs to help you customize and build your SAAS app!

Wave is also built on top of Voyager, so all the Voyager configs are available to you as well. To learn more about those you can check out the [voyager docs here](https://docs.laravelvoyager.com/getting-started/configurations).

---

- [Settings](/docs/{{version}}/configurations#settings)
- [Configs](/docs/{{version}}/configurations#configs)

<a name="settings"></a>
## Wave Settings Configuration

There are many settings available in your Wave admin section. Visit `/admin/settings` and you will be at your application settings. Which has the following settings you can modify.

> {info} In order to login to the admin section of your application you can use the following credentials `admin@admin.com` and password as `password`

### Site Settings

From the Site Settings tab you can modify the following settings:
- **Site Title** - The title of your application
- **Site Description** - The description of your application
- **Google Analytics Tracking ID** - Enter your Analytics Tracking code to track page views and analytics
- **Favicon** - Upload your application favicon

### Admin Settings

These are settings to customize your admin
- **Admin Title** - The title of you application admin
- **Google Analytics Client ID** - This is used to show Google Analytics in your admin dashboard
- **Admin Description** - The description of your application admin
- **Admin Loader** - The loading image for your admin
- **Admin Icon Image** - The admin or application icon image
- **Admin Background Image** - Add your own admin login background image

### Authentication Settings

- **Homepage Redirect to Dashboard if Logged in** - When an authenticated user visits the homepage you may with to redirect them to the application dashboard
- **Users Login with Email or Username** - Choose whether you want your users to login with their email or username
- **Username when Registering** - Show the username in the signup form or have it automatically generated based on the users name
- **Verify Email during Sign Up** - Enable this setting if you want your users to verify their email before being able to login

### Billing

- **Require Credit Card Up Front** - You can choose whether or not you want users to enter a credit card while signing up
- **Trial Days when No Credit Card Up Front** - Specify the amount of trial days when a user is not required to enter a Credit Card

---

<a name="configs"></a>
## Wave Configuration File

There are a few logical configurations you can make within the wave configuration file located at `/config/wave.php`. The contents of that file is as follows:

```php
<?php

return [

    'profile_fields' => [
        'about'
    ],

    'api' => [
        'auth_token_expires'    => 60,
        'key_token_expires'     => 1,
    ],

    'auth' => [
        'min_password_length' => 5
    ],

    'user_model' => App\User::class,
    'show_docs' => env('WAVE_DOCS', true),

];
```
<br>
- **profile_fields** - Whenever you want to dynamically create a new user profile field such as `about`, `social_links`, or any other field you will need to include the field name in this config. You will learn all about *Custom Profile Fields* in the [User Profiles Section](/docs/{{version}}/features/user-profiles)

- **api => auth_token_expires** - This is the amount of time you want your JSON web token to expire. After this token has expired the app will then request a refresh token. You will most likely never need to change this value, but it's there if you need it.

- **api => key_token_expires** - This is the amount of time (in minutes) an API token will expire when it is generated with a user API Key.

    A user can generate an API key in your application which is used to create an API token during a request. After the default **1** minute. The user or the users application will need to make another request with their API key.

- **auth => min_password_length** - This is the minimum password length a user must enter when registering for an acccount.

- **user_model** - This is the default user model of your application. In most cases this is going to be the `App\User` model. If you are using a different user model you will want to add that here.

    Remember your User Model will also need to extend the `\Wave\User` model. If you take a look at the `App\User` model you can see it extends from the Wave user model:

    ```php
    class User extends \Wave\User
    ```

    ---

    > {primary} Wave Themes will give you unlimited configurations for your SAAS. We'll cover more of this later, or you can jump to the [Themes section by clicking here](/docs/{{version}}/features/themes).
