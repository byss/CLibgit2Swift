# CLibgit2Swift

A swift package manager wrapper for libgit2

## Requirements

 - Swift package manager (SPM, see http://swift.org)
 - Libgit2 C library installed

  ### Install on Mac OS

  ```
  brew install libgit2
  ```

  ### Install on Linux

  ```
  sudo apt-get update
  sudo apt-get install libgit2-dev
  sudo ldconfig
  ```

  or build manually, but don't forget this `sudo ldconfig`!

## Usage

In order to use CRabbitMQ in Swift, for example in a file as follows:

```
import CLibgit2


// init git
Swift.print("libgit init")
git_libgit2_init()

// query git version
var major:Int32 = 0
var minor:Int32 = 0
var rev:Int32 = 0
git_libgit2_version(&major, &minor, &rev)
Swift.print("libgit version: \(major).\(minor).\(rev)")


// shutdown git
git_libgit2_shutdown()
Swift.print("shut down")

```

all you need is to place a `Package.swift` file in the same directory:

```
import PackageDescription

let package = Package(
    name: "GitTest",
    targets: [],
    dependencies: [
        .Package(url: "https://github.com/ben-ole/CLibgit2Swift.git", majorVersion: 0)
    ]
)

```

## Caveat

The libgit2 pkg-config file is currently not compatible with the Swift Package Manger. In particular commit [768e185c54164a66fc4e2dbe7c58097eff65ebdf](https://github.com/libgit2/libgit2/commit/768e185c54164a66fc4e2dbe7c58097eff65ebdf) introduced some quotes which need to be removed from the `pkgconfig/libgit2.pc` to work properly with the swift build system.