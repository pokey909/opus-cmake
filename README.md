# opus-cmake
cross-platform libopus with cmake and polly

# Getting the source

```
git clone --recursive git@github.com:pokey909/opus-cmake.git
```

# Requirements
**Android**

Download and install android ndk 17 to an arbitrary local folder and add an environment variable pointing to your NDK 17 installation.
```
export ANDROID_NDK_r17=/home/you/Android/ndk
```

# Building
To improve the laborious process of typing long toolchain names, I included a toolchain selector
which accepts a ```PLATFORM_TARGET``` variable and maps it to an approriate toolchain.

Here is a list of possible values

|```PLATFORM_TARGET```   |  Description |
|---|---|
| android  |  armeabi, gcc, NDK11c (deprecated since NDK17) |
| android-v7a  |  clang, c++14, arm-v7a, NDK17 |
| android-64-v8a  | clang, c++14, arm-v8a (64bit), NDK17  |
| android-x86 | clang, c++14, x86, NDK17 |
| android-x86_64 | clang, c++14, x86 (64bit), NDK17 |
| linux | clang, host architecture |
| osx | clang, host architecture, c++14, makefiles |
| osx-xcode | clang, host architecture, osx 10.13, xcode project / xcbuild |
| ios | clang, no codesign |
| ```undefined``` | defaults to libcxx14 |

To start the build
```
mkdir build
cmake .. -DPLATFORM_TARGET=<target>
cmake --build .
```

## Using polly as build helper
Of course you can also use ruslo's excellent build tool polly which is included as a submodule under ```cmake/toolchains```.
