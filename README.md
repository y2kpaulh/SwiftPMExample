# ๐พ Framework Guidelines

ํ์ฌ์ ๋ฐฉ์ก ์ก์ถ ๊ธฐ๋ฅ์ ์ ๊ณตํ๊ธฐ ์ํ `Framework`๋ ์์ค๋ฅผ ์ธ๋ถ์์ ํ์ธํ  ์ ์๋๋ก ๊ตฌํ๋์ด์ผ ํ๋ค. ๊ตฌํ ์์ค ๋ด์ฉ์ `์๋์ฑ(encapsulation)`์ ๋ณด์ฅํ๊ธฐ ์ํด [Binary Framework](https://developer.apple.com/videos/play/wwdc2019/416/) ํํ๋ก ๊ตฌํ๋์ด์ผ ํ๋ค. 

์ฑ์์ ์ฌ์ฉํ๋ `์คํ ์์ค Library`๋ `Framework`๋ผ๋ ๋ช์นญ ๋์  ๊ตฌ๋ถ์ ์ํด `Third Party` Library๋ก ํ๊ธฐํจ.

ํ์ฌ ์ ํ์์ ์ ๊ณตํ๋ ํ๋ ์์ํฌ ๋ฐฉ์์ [XCFramework](https://help.apple.com/xcode/mac/11.4/#/dev544efab96)์ด๋ฉฐ,  `Binary Framework` Target ์ต์์ผ๋ก ์์ฑํ๋ค. ๋ฐฐํฌ ๋ฐฉ์์ ์ ํ์์ ์ง์ํ๋ `Swift Package Manager` ๋ฐฉ์ ๋ฐ `Thrid Party` ๋ฐฐํฌ ๋ฐฉ์์ธ [Cocoapod](https://cocoapods.org)์ด๋ [Carthage](https://github.com/Carthage/Carthage) ๋ฐฉ์์ผ๋ก๋ ๋ฐฐํฌ๊ฐ ๊ฐ๋ฅํ๋ค.

# ์์ ์์

- [Framework ๊ตฌํ](#framework-๊ตฌํ)
- [XCFramework  ์์ฑ](#xcframework-์์ฑ)
- [Swift Package ์์ ](#swift-package-์์ )
- [Swift Package Manager ๋ฐฐํฌ](#swift-package-manager-๋ฐฐํฌ)

# Framework ๊ตฌํ
 
## Framework๋ก ๊ตฌํํ๊ณ ์ ํ๋ ๊ธฐ์กด ์์ค ๋ฐ ๋ฆฌ์์ค๋ฅผ ๊ตฌํ ํ๋ก์ ํธ๋ก ๊ฐ์ ธ์จ๋ค. ๊ตฌํ ๋ด์ฉ ์ค Third Party Library ๊ธฐ๋ฅ์ ์ ์ฉํ๊ธฐ ์ํด Library Source ์๋ณธ์ ๊ฐ์ ธ์จ๋ค.

## Third Party Library ์ถ๊ฐ

- [ ]  ์์ํ๋ ์์ค ํ๋ก์ ํธ์ ์ถ๊ฐํ๊ณ ์ ํ๋ Library๋ฅผ ์์ค ํํ๋ก  ์ถ๊ฐํ๊ณ , ์ถ๊ฐ๋ ํ๋ ์์ํฌ์ ํ๊ฒ์ผ๋ก ๋ณ๊ฒฝํ์ฌ Library๋ฅผ ์ปดํ์ผํ์ฌ, ์ค๋ธ์ ํธ ํํ๋ก ํ๋ ์์ํฌ์ ์ถ๊ฐํ๋ค.

- [ ]  ์ถ๊ฐํ Library๋ฅผ XCode Menu์ GeneralโFrameworks and Libraries์  Library์  `.framework` ํ์ผ์ Drag & Drop ์ผ๋ก ์ถ๊ฐํ๊ณ , `Embed & Sign` ํํ๋ก ์ค์ ํ๋ค. Build Phase ๋ฉ๋ด์์ `Link Binary With Libraries` ๋ฉ๋ด์ Library๊ฐ ํฌํจ๋์ด ์๋์ง ํ์ธ๋ค.

- [ ]  ์ถ๊ฐํ Library๋ฅผ ์์ค์์ import ํ Library ๋์์ ํ์ธํ๋ค.

- [ ]  `Build Settings` ๋ฉ๋ด์์  `BUILD_LIBRARIES_FOR_DISTRIBUTION`  ์ต์์ `YES`๋ก ์ค์ ํ๋ค.

> `์ฃผ์: @import` ๊ตฌ๋ฌธ์ด ํฌํจ๋ ๋ผ์ธ์ Warning ๋ฉ์ธ์ง๊ฐ  ๋ฐ์ํ  ๊ฒฝ์ฐ ์ ์์ ์ผ๋ก Library๊ฐ ์ถ๊ฐ๋์ง ์์๊ฒ์ด๋ค.

# XCFramework ์์ฑ

XCFramework๋ `Platform` (MacOS, iOS, iOS-Simulator, iPadOS, WatchOS) ๋ณ๋ก xcarchive ํ์ผ์ ์์ฑํ  ์ ์๋ค. ๊ตฌํ ์์ค๋ ์ ํ๋ฒํธ ์ธ์ฆ ๋ฐ ์นด๋ฉ๋ผ ์ก์ถ ๊ธฐ๋ฅ์ด ํฌํจ๋์ด ์๊ธฐ ๋๋ฌธ์, ์๋ฎฌ๋ ์ดํฐ์์๋ ์ฌ์ฉํ  ์ ์๊ธฐ ๋๋ฌธ์ iOS ํ์ผ์ผ๋ก๋ง ์์นด์ด๋นํ๋ค.

##  **iOS Framework๋ก xcarchive ํ์ผ ์์ฑ**

```swift
xcodebuild archive \\
-scheme DemoXCFramework \\
-configuration Release \\
-destination 'generic/platform=iOS' \\
-archivePath './build/DemoXCFramework.framework-iphoneos.xcarchive' \\
SKIP_INSTALL=NO \\
BUILD_LIBRARIES_FOR_DISTRIBUTION=YES
```

##  **xcarchive ํ์ผ์ XCFramework๋ก ๋ณํ**

```swift
xcodebuild -create-xcframework \\
-framework './build/DemoXCFramework.framework-iphoneos.xcarchive/Products/Library/Frameworks/DemoXCFramework.framework' \\
-output './build/DemoXCFramework`.xcframework
```

# Swift Package ์์ 
- `Swift Package` ํ๋ก์ ํธ์ `Package.swift` ํ์ผ์ `targets` ์ต์์ `.binaryTarget`์ผ๋ก ์ค์ ํ๊ณ , `XCFramework` ํ์ผ ์ถ๊ฐ
- `Swift Package` ๋ฒ์  ์ ๋ณด ๋ณ๊ฒฝ

# Swift Package Manager ๋ฐฐํฌ
- `GitHub Repository`์ ์์ค ์๋ก๋ ํ ๋ณ๊ฒฝํ ๋ฒ์ ์ `Git Tag`๋ก ์ถ๊ฐํ๊ณ ,`Tag`๋ฅผ `Release`๋ก ๋ณ๊ฒฝํ์ฌ ๋ฐฐํฌํ๋ค.
- ๋ฐฐํฌ๋ `Framework`๋ฅผ ์ฌ์ฉํ๊ธฐ ์ํด portingํ ์ฑ์ `Framework` ํ์ผ ๋ด๋ถ์ ์ค๋ธ์ ํธ ํํ๋ก ์กด์ฌํ๋ Library๋ฅผ `Framework` ์ ์ฉ์ ๊ฐ์ด ๋์ผํ ๋ฒ์ ์ผ๋ก ์ ์ฉํด์ผ ์ ์๋์ํ๋ค. 

## Reference

1. [Create an XCFramework](https://help.apple.com/xcode/mac/11.4/#/dev544efab96)
2. [Distributing Binary Frameworks as Swift Packages](https://developer.apple.com/documentation/swift_packages/distributing_binary_frameworks_as_swift_packages)
