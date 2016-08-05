# CLibgit2Swift

A swift package manager wrapper for libgit2

## Requirements

 - Swift package manager (SPM, see http://swift.org)
 - Libgit2 C library, install via `brew install libgit2`

## Usage

In order to use CRabbitMQ in Swift, for example in a file as follows:

```
import CLibgit2Swift


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