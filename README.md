# love-actions-android

## About

Github Action for building & deploying Android `.apk` and `.abb` packages of a [LÖVE](https://love2d.org/) framework based game.

### Related actions

See related actions below:

[Love actions bare package](https://github.com/marketplace/actions/love-actions-bare-package)

[Love actions for testing](https://github.com/marketplace/actions/love-actions-for-testing)

[Love actions for iOS](https://github.com/marketplace/actions/love-actions-for-ios)

[Love actions for Linux](https://github.com/marketplace/actions/love-actions-for-linux)

[Love actions for macOS portable](https://github.com/marketplace/actions/love-actions-for-macos-portable)

[Love actions for macOS App Store](https://github.com/marketplace/actions/love-actions-for-macos-app-store)

[Love actions for Windows](https://github.com/marketplace/actions/love-actions-for-windows)

## Quick example

```yaml
- name: Build love android
  id: build-love
  uses: 26F-Studio/love-actions-android@main
  with:
    app-name: "My Love Game"
    bundle-id: "org.love2d.my_game"
    keystore-alias: ${{ secrets.ANDROID_KEYSTORE_ALIAS }}
    keystore-base64: ${{ secrets.ANDROID_KEYSTORE_BASE64 }}
    keystore-key-password: ${{ secrets.ANDROID_KEYSTORE_KEYPASSWORD }}
    keystore-store-password: ${{ secrets.ANDROID_KEYSTORE_STOREPASSWORD }}
    love-package: "./game.love"
    product-name: "my-game"
    resource-path: "./assets/android/res"
    libs-path: "./assets/android/libs"
    extra-assets: ./README.md ./license.txt
    version-string: "2.3.4"
    version-code: 234
    output-folder: "./dist"
```

## All inputs

| Name                      | Required | Default                | Description                                                  |
| :------------------------ | -------- | ---------------------- | ------------------------------------------------------------ |
| `app-name`                | `false`  | `"LÖVE for Android"`   | App display name. Used in `app/src/main/AndroidManifest.xml` |
| `bundle-id`               | `false`  | `"org.love2d.android"` | App bundle id. Used in `app/build.gradle`                    |
| `icon-specifier`          | `false`  | `"@drawable/love"`     | App icon specifier. Used in `app/src/main/AndroidManifest.xml` |
| `keystore-alias`          | `false`  | `""`                   | Signing keystore's alias. Won't build release packages if not specified |
| `keystore-base64`         | `false`  | `""`                   | Signing keystore's content in `base64` string. Won't build release packages if not specified |
| `keystore-key-password`   | `false`  | `""`                   | Signing keystore's key password. Won't build release packages if not specified |
| `keystore-store-password` | `false`  | `""`                   | Signing keystore's store password. Won't build release packages if not specified |
| `love-package`            | `false`  | `"./game.love"`        | `.love` game package file path                               |
| `product-name`            | `false`  | `"love-app"`           | Base name of the package. Used to rename products            |
| `resource-path`           | `true`   | `""`                   | Path to the android resources folder. Would copy all contents to `app/src/main/res` excluding top folder |
| `libs-path`               | `false`  | `""`                   | Path to the JNI libraries folder. Would copy all contents to `app/libs` excluding top folder |
| `extra-assets`            | `false`  | `""`                   | List of folder & file paths to be added to `app/src/embed/assets/`. Separated by spaces |
| `version-string`          | `false`  | `"11.4"`               | App version string no more than 3 numbers. Used in `app/build.gradle` |
| `version-code`            | `false`  | `"30"`                 | Numeric app version code . Used in `app/build.gradle`        |
| `output-folder`           | `false`  | `"./build"`            | Built packages output folder                                 |

## All outputs

| Name            | Example                                                 | Description                                                  |
| :-------------- | ------------------------------------------------------- | ------------------------------------------------------------ |
| `package-paths` | `./build/my-game-debug.apk ./build/my-game-release.apk` | Built packages' paths in a bash-style list relative to the repository root, separated by spaces |
