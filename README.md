# V8 Monolithic Library Builds

This repository contains automated builds of Google V8 static libraries for multiple platforms using GitHub Actions.

English | [简体中文](README.ZH.md)

## Current V8 Version

**14.3.92**

## Supported Platforms

- **Android** (arm64, arm, x64)
- **iOS** (Universal library for arm64 device + arm64 simulator)
- **macOS** (arm64)
- **Windows** (x64)

## Latest Release

Check the [Releases](../../releases) page for the latest precompiled binaries.

## Package Contents

Each release includes zip packages with:
- **Static library file** (libv8_monolith.a / v8_monolith.lib)
- **args.gn** - Build configuration used for compilation
- **args.full.txt** - Complete GN arguments list with all default values and descriptions

## Build Artifacts

| Platform | Artifact File | Architectures | Description |
|----------|--------------|---------------|-------------|
| Android  | `libv8_monolith-android-arm64.zip` | arm64 | Static library for Android arm64 |
| Android  | `libv8_monolith-android-arm.zip` | arm | Static library for Android arm |
| Android  | `libv8_monolith-android-x64.zip` | x64 | Static library for Android x64 (emulator) |
| Android  | `include-android.zip` | - | V8 header files (from arm64 build) |
| iOS      | `libv8_monolith-ios-universal.zip` | arm64 (device + simulator) | Universal library for iOS |
| iOS      | `include-ios.zip` | - | V8 header files |
| macOS    | `libv8_monolith-mac-arm64.zip` | arm64 | Static library for macOS Apple Silicon |
| macOS    | `include-mac.zip` | - | V8 header files |
| Windows  | `libv8_monolith-win-x64.zip` | x64 | Static library for Windows x64 |
| Windows  | `include-win.zip` | - | V8 header files |

## Build Configuration Files

The repository contains GN build configuration files for each platform:

### Android
- [args.android.arm64.gn](args.android.arm64.gn)
- [args.android.arm.gn](args.android.arm.gn)
- [args.android.x64.gn](args.android.x64.gn)

### iOS
- [args.ios.arm64.gn](args.ios.arm64.gn) - Device configuration
- [args.ios.arm64.simulator.gn](args.ios.arm64.simulator.gn) - Simulator configuration

**Note**: The iOS build produces a Universal (Fat) library that contains both device and simulator architectures, making it easy to use in Xcode projects without switching libraries.

### macOS
- [args.mac.arm64.gn](args.mac.arm64.gn)

### Windows
- [args.win.x64.gn](args.win.x64.gn)

## Features

- ✅ Automated builds via GitHub Actions
- ✅ Consistent configuration across platforms
- ✅ Pre-build scripts for platform-specific optimizations ([builder.js](builder.js))
- ✅ Full build argument traceability
- ✅ iOS WebAssembly support enabled

## Usage

1. Download the appropriate zip file for your platform from the [Releases](../../releases) page
2. Extract the static library file
3. Link against the library in your project
4. Include the V8 headers (included in the release)
5. Refer to `args.gn` and `args.full.txt` to understand the build configuration

## Build System

All builds are automated using [GitHub Actions](.github/workflows/main.yml):
- Clean build environment for each platform
- Consistent depot_tools version
- Reproducible builds
- Automated release creation

## V8 Documentation

### Official V8 Resources
- [V8 Build Instructions](https://v8.dev/docs/build)
- [V8 Build with GN](https://v8.dev/docs/build-gn)
- [V8 ARM64 Build](https://v8.dev/docs/compile-arm64)

### Chromium Build Instructions
- [Windows Build Instructions](https://chromium.googlesource.com/chromium/src/+/HEAD/docs/windows_build_instructions.md)
- [Android Build Instructions](https://chromium.googlesource.com/chromium/src/+/HEAD/docs/android_build_instructions.md)
- [iOS Build Instructions](https://chromium.googlesource.com/chromium/src/+/HEAD/docs/ios/build_instructions.md)
- [macOS Build Instructions](https://chromium.googlesource.com/chromium/src/+/HEAD/docs/mac_build_instructions.md)
- [macOS ARM64 Build](https://chromium.googlesource.com/chromium/src/+/HEAD/docs/mac_arm64.md)

### Additional Resources
- [V8 Release Schedule](https://chromiumdash.appspot.com/schedule)
- [GitHub Actions Runner Images](https://github.com/actions/runner-images)

## Contributing

To update the V8 version or modify build configurations:

1. Update `V8_VERSION` in [.github/workflows/main.yml](.github/workflows/main.yml)
2. Modify platform-specific `args.*.gn` files as needed
3. Update [builder.js](builder.js) for platform-specific build logic
4. Create a new git tag to trigger the build workflow

## Acknowledgments

This project is inspired by and references the work from [just-js/v8](https://github.com/just-js/v8).

## License

This repository contains build configurations and automation scripts. V8 itself is licensed under the BSD license. See the [V8 repository](https://github.com/v8/v8) for details.
