---
layout: post
title: "How to create a APK from PWA?"
description: "Build an Android TWA and publish on Google Play Store from PWA using llama pack"
categories: [PWA]
tags: [PWA]
---

- Has PWA all ready **Important!**

- Install llama pack dependencies

- [OpenJDK 8](https://adoptopenjdk.net/releases.html?variant=openjdk8&jvmVariant=hotspot)
  Download and uncompress it on `~/.java/` directory

  ```console
  tar xf ./openJDK-jdk.tar.gz -C ~/.java/
  tar xf ./openJDK-jre.tar.gz -C ~/.java/
  ```

  **Optional**
  Setup enviroment variable.

  ```console
  echo "export JAVA_HOME=\"/home/luis/.java/OpenJDK8U-jdk_xxx/jdk8u242-xxx\" >> ~/.bashrc"
  ```

  Close all terminals for changes to take effect

- [Android command line tools](https://developer.android.com/studio#command-tools)
  Search section command line tools only
  Download and uncompress it on `~/Android/sdk/`

  ```console
  unzip ./commandlinetools-linux-xxxx_latest.zip -d ~/Android/sdk/
  ```

- Install llama-pack cli

```console
npm i -g @llama-pack/cli
```

- Execute llama-pack

Provide `manifest.json` url or `manifest.webmanifest` file

```console
llama-pack init --manifest https://my-twa.com/manifest.webmanifest
```

Answer questions about twa

```console
Domain being opened in the TWA:
Name of the application:
```

In keystore let's press enter then it asks you about create a key store

```console
First and Last names (eg: John Doe): Luis Reinoso
Organizational Unit (eg: Engineering Dept): Developer
Organization (eg: Company Name): Freenlance
Country (2 letter code): EC
// use the same password
Password for the Key Store: [hidden]
Password for the Key: [hidden]
```

- Upload private key to google play console

* Create asset link
  Using package fingerprint (SHA256) inside app sign go to [Google Digital Asset Links](https://developers.google.com/digital-asset-links/tools/generator)

This will create a json then create a file named `assetlinks.json` and serve it from `https://my-twa.com/.well-known/assetlinks.json.`

Useful Checker
https://digitalassetlinks.googleapis.com/v1/statements:list?source.web.site=https://www.your-website-name.com&relation=delegate_permission/common.handle_all_urls

- Build apk

```console
llama-pack build
```

This generate the `app-release-signed.apk`

- Upload to play store
- Fill all data required from play store

# References

- [llama pack cli](https://github.com/GoogleChromeLabs/llama-pack/tree/master/packages/cli)
