# R1.5 Support for `-clonedSourcePackagesDirPath` and `-derivedDataPath` in `PSCliCodeInjector`.

We are happy to introduce an update to the iOS version of PS Tool. This enhancement aligns with `xcodebuild` functionality, allowing you to specify custom paths for cloned source packages and derived data, thus maintaining a consistent build environment across different build types.

## What’s new?

**This latest version of `PSCliCodeInjector` supports Xcode 16.** The latest version also adds support for the `-clonedSourcePackagesDirPath` and `-derivedDataPath` flags. These flags are passed to all xcodebuild commands, including those handling Swift Package Manager (SPM) dependencies, ensuring consistent directories for local dependencies and build caches between standard and PS builds when it's possible. 

## How to implement?

You can supply these flags in two ways:

- **Within the** `-console-build-command`: Include the flags in your console build command.
- **As direct parameters to** `PSCliCodeInjector`: Pass the flags directly when invoking `PSCliCodeInjector`.
