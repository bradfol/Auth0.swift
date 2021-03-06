# Auth0.swift

[![CI Status](http://img.shields.io/travis/auth0/Auth0.swift.svg?style=flat-square)](https://travis-ci.org/auth0/Auth0.swift)
[![Version](https://img.shields.io/cocoapods/v/Auth0.svg?style=flat-square)](http://cocoadocs.org/docsets/Auth0)
[![License](https://img.shields.io/cocoapods/l/Auth0.svg?style=flat-square)](http://cocoadocs.org/docsets/Auth0)
[![Platform](https://img.shields.io/cocoapods/p/Auth0.svg?style=flat-square)](http://cocoadocs.org/docsets/Auth0)
[![Carthage compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat-square)](https://github.com/Carthage/Carthage)

Swift toolkit for Auth0 API

## Requirements

iOS 8+ and Xcode 7 (Swift 2.0)

## Installation

###CocoaPods

Auth0.swift is available through [CocoaPods](http://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod "Auth0", '~> 0.2'
```

###Carthage

In your Cartfile add this line

```
github "auth0/Auth0.swift"
```

###Manual installation

Download `Auth0.framework` from [Releases](/releases) and add it to your project in Xcode.

##Auth0.swift

Before we start add your **Auth0** domain in your `Info.plist` file as the value of the key `Auth0Domain`, e.g.:

`Auth0Domain`: `https://samples.auth0.com`

Or create your own instance of Auth0

```swift
let auth0 = Auth0(domain: "https://samples.auth0.com")
```
> If you choose to follow this path, you are responsible to keep this reference alive

### Users

####Update `user_metadata` with `id_token`

```swift
Auth0
    .users(id_token)
    .update(userMetadata: ["first_name": "John Doe"])
    .responseJSON { error, userJSON in
        //Do stuff...
    }
```

####Update User root attributes (including metadata) with `id_token`

```swift
Auth0
    .users(id_token)
    .update(parameter: [
        "email": "support@auth0.com", 
        "verify_email": true
        ])
    .responseJSON { error, userJSON in
        //Do stuff...
    }
```

####Update `app_metadata` using API v2 JWT

```swift
Auth0
    .users(jwt)
    .update(id: "auth0|1234567890", appMetadata: ["role": "admin"])
    .responseJSON { error, userJSON in
        //Do stuff...
    }
```

####Update User root attributes (including metadata) using API v2 JWT

```swift
Auth0
    .users(jwt)
    .update(id: "auth0|1234567890", parameter: [
        "email": "support@auth0.com", 
        "verify_email": true
        ])
    .responseJSON { error, userJSON in
        //Do stuff...
    }
```

####Fetch User using id_token

```swift
Auth0
    .users(id_token)
    .find()
    .responseJSON { error, userJSON in
        //Do stuff...
    }
```

####Fetch User using API v2 JWT

```swift
Auth0
    .users(id_token)
    .find(id: "auth0|1234567890")
    .responseJSON { error, userJSON in
        //Do stuff...
    }
```

## What is Auth0?

Auth0 helps you to:

* Add authentication with [multiple authentication sources](https://docs.auth0.com/identityproviders), either social like **Google, Facebook, Microsoft Account, LinkedIn, GitHub, Twitter, Box, Salesforce, amont others**, or enterprise identity systems like **Windows Azure AD, Google Apps, Active Directory, ADFS or any SAML Identity Provider**.
* Add authentication through more traditional **[username/password databases](https://docs.auth0.com/mysql-connection-tutorial)**.
* Add support for **[linking different user accounts](https://docs.auth0.com/link-accounts)** with the same user.
* Support for generating signed [Json Web Tokens](https://docs.auth0.com/jwt) to call your APIs and **flow the user identity** securely.
* Analytics of how, when and where users are logging in.
* Pull data from other sources and add it to the user profile, through [JavaScript rules](https://docs.auth0.com/rules).

## Create a free Auth0 Account

1. Go to [Auth0](https://auth0.com) and click Sign Up.
2. Use Google, GitHub or Microsoft Account to login.

## Issue Reporting

If you have found a bug or if you have a feature request, please report them at this repository issues section. Please do not report security vulnerabilities on the public GitHub issue tracker. The [Responsible Disclosure Program](https://auth0.com/whitehat) details the procedure for disclosing security issues.

## Author

[Auth0](auth0.com)

## License

This project is licensed under the MIT license. See the [LICENSE](LICENSE.txt) file for more info.
