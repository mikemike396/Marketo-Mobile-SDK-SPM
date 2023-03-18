# Unofficial Swift Package for Marketo Mobile SDK

## Swift Package Manager

- File > Swift Packages > Add Package Dependency
- Add `https://github.com/mikemike396/MarketoMobileSDK-SPM`

## Official Marketo Library
https://github.com/Marketo/ios-sdk

## Steps we used to build XCFramework

1. Download repository from official repo https://github.com/Marketo/ios-sdk
2. Install https://github.com/igor-makarov/XCFrameworkConverter
3. Run `xcfconvert <path/to/Marketo.framework>`
   - This will generate an xcframework with the appropriate architectures for arm64(phone), arm64_x86_64(simulator)
   <img width="250" alt="image" src="https://user-images.githubusercontent.com/14999806/226145731-cd7b1d2f-f498-4992-9174-3fca9bb4d188.png">
   
4. Download and compile https://github.com/luosheng/arm64-to-sim#prepare
5. Run `arm64-to-sim patch <path/to/Marketo.framework/Marketo>`

   <img width="250" alt="image" src="https://user-images.githubusercontent.com/14999806/226145918-20727c2d-6b03-423c-933a-0c33228420e4.png">
6. Remove `Marketo.alias` and `Marketo.original`
7. Rename `Marketo.patched` to `Marketo`

   <img width="250" alt="image" src="https://user-images.githubusercontent.com/14999806/226145958-60538655-260d-4951-bb6e-10cd91b8860a.png">
8. Copy updated `Marketo.framework` over `Marketo.xcframework/ios-arm64_x86_64-simulator/Marketo.framework`
9. 🎉 You now have an XCFramework of the static Marketo SDK which can be ran on arm64 and x86_64 simulators
