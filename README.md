# Website

This website is built using [Docusaurus 2](https://docusaurus.io/), a modern static website generator.

### Installation

```
$ yarn
```

### Local Development

```
$ yarn start
```

This command starts a local development server and opens up a browser window. Most changes are reflected live without having to restart the server.

### Build

```
$ yarn build
```

This command generates static content into the `build` directory and can be served using any static contents hosting service.

### Deployment

Using SSH:

```
$ USE_SSH=true yarn deploy
```

Not using SSH:

```
$ GIT_USER=<Your GitHub username> yarn deploy
```

If you are using GitHub pages for hosting, this command is a convenient way to build the website and push to the `gh-pages` branch.

### Deployment using Cloud Run

```
$ gcloud init
```

Configure project with gcp accout ( Set Account name, Project name )

```
$ gcloud iam service-accounts keys create {KEY_FILE_PATH} --iam-account {SERVICE_ACCOUNT_EMAIL}
```

Add access key json file path and service email

```
$ gcloud iam service-accounts keys create {KEY_FILE_PATH} --iam-account {SERVICE_ACCOUNT_EMAIL}
```

Export the access key credentials

```
$ gcloud run deploy
```

Deploy the project

### Add credentials for google signing

Before build the debug apk

Copy debug.keystore file from location

mobile/android/app/debug.keystore

and paste file in the following location

~/.android/

### IOS build and release

IOS app development is consisted with following steps.

1. Open the app in Xcode and navigate to **General** tab. Increase last digit of version number and increase build number by one.

![Build Number Increase](./static/release/1.png)

2. Navigate to **Signing and Capabilities** tab. Select all option and fill details as below.

![Configure Development Team](./static/release/2.png)

3. Navigate to **Product** tab as below. Select _**Any iOS Device (arm64)**_ option

![Device Selection](./static/release/3.png)

4. From left navigation menu, select **Pods**. In the **Build Settings** tab search for _**Enable Bitcode**_ option and disable.

Select **flutter_facebook_auth** from pods list. Search for _**Enable Bitcode**_ option and select _**No**_.

![Pods disable bitcode](./static/release/4.png)

![flutter_facebook_auth disable bitcode](./static/release/5.png)

5. Repeat above step for **FBAEMKit, FBSDKCoreKit, FBSDKCoreKit_Basic and FBSDKLoginKit**.

![FBSDK disable bitcode](./static/release/6.png)

6. Navigate to **mobile** directory and execute following command and build the app

```
$ flutter build ios
```

7. Navigate to **Product** tab as below. Click on Archieve and create a build archieve.

![Create build archieve](./static/release/8.png)

8. On popup window select latest distribution. Click on **Distribute App**

![Create distribution](./static/release/9.png)

Select all default options. When following window is appeared, Click on **Upload**

![Upload distribution](./static/release/10.png)

After upload is completed click **Done**

![Complete distribution](./static/release/11.png)

9. After the distribution is completed new release should be displayed in **TestFlight**

![Latest Releases](./static/release/12.png)

### Add Firebase In App Messaging

You can add new messages to the Qranlingo through Firebase. [ Click here for guidelines.](https://onedrive.live.com/view.aspx?resid=8FD0DBB5283591A5!162&ithint=file%2cdocx&authkey=!AMqQcCTz8mNlUp0)
