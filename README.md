# Example Project

## Setup & Open the Project

You'll need to have [Carthage](https://github.com/Carthage/Carthage) installed
in order to pull the AppAuth dependency.

So first run `carthage bootstrap` to build AppAuth framework then open the
`Example.xcodeproj` file.

## Configuration

The example doesn't work out of the box, you need to configure it with your own
client ID.

### Information You'll Need

* Issuer
* Client ID
* Redirect URI

How to get this information varies by IdP, but we have
[instructions](../README.md#openid-certified-providers) for some OpenID
Certified providers.

### Creating credentials in google
1. visit https://console.developers.google.com/apis/credentials?project=_ 
2. Create a new project
3. Then tap "Create credentials" and select "OAuth client ID".
4. Follow the on-screen instructions, just give product name
5. Select ios 
6. Give bundle identifier. 

How to find bundle identifier
Selcet the project  in xcode project navigator. Under Targets section you will find the bundle identifier name.

### Configure the Example

#### In the file `AppAuthExampleViewController.swift` 

1. Update `kIssuer` with the IdP's issuer.
2. Update `kClientID` with your new client id.
3. Update `kRedirectURI` redirect URI

Use the following for google.

let kRedirectURI: String = "com.googleusercontent.apps.878180022764-bna77rh9cuq5a689db5pj2is6tnaqra7:/oauth2redirect/google";
let kClientID: String? = "878180022764-bna77rh9cuq5a689db5pj2is6tnaqra7.apps.googleusercontent.com";
let kIssuer: String = "https://accounts.google.com";



#### In the file `Info.plist`

Fully expand "URL types" (a.k.a. `CFBundleURLTypes`) and replace
`com.example.app` with the *scheme* of your redirect URI. 
The scheme is everything before the colon (`:`).  For example, if the redirect
URI is `com.example.app:/oauth2redirect/example-provider`, then the scheme
would be `com.example.app`.

For google use this:
URLTypes --> Item0 --> URL Schemes --> Item0 ---> update the  url 'com.googleusercontent.apps.878180022764-bna77rh9cuq5a689db5pj2is6tnaqra7' here 




### Running the Example

Now your example should be ready to run.

