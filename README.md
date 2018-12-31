GitAhead - Understand Your History
==================================

GitAhead is a graphical Git client designed to help you understand
and manage your source code history. It's available as a pre-built
binary for Windows, Linux, and macOS, or can be built from source by
following the directions below.

How to Get Help
---------------

Ask questions about building or using GitAhead on
[Stack Overflow](http://stackoverflow.com/questions/tagged/gitahead) by
including the `gitahead` tag. Remember to search for existing questions
before creating a new one.

Report bugs in GitAhead by opening an issue in the
[issue tracker](https://github.com/gitahead/gitahead/issues).
Remember to search for existing issues before creating a new one.

If you still need help, email us at
[support@gitahead.com](mailto:support@gitahead.com).

Build Environment
-----------------

* C++11 compiler
  * Windows - MSVC >= 2017 recommended
  * Linux - GCC >= 6.2 recommended
  * macOS - Xcode >= 10.1 recommended
* CMake >= 3.3.1
* Ninja (optional)

Dependencies
------------

External dependencies can be satisfied by system libraries or installed
separately. Included dependencies are included as submodules of this
repository. Some of the submodules are optional or may also be satisfied
by system libraries.

**External Dependencies**

* Qt (required >= 5.9)

**Included Dependencies**

* libgit2 (required)
* cmark (required)
* git (only needed for the credential helpers)
* libssh2 (needed by `libgit2` for SSH support)
* openssl (needed by `libssh2` and `libgit2` on some platforms)

How to Build
------------

**Initialize Submodules**

    git submodule init
    git submodule update

**Build OpenSSL**

    # Start from root of gitahead repo.
    cd dep/openssl/openssl

Win:

    perl Configure VC-WIN64A
    ms\do_win64a
    nmake -f ms\ntdll.mak

Mac:

    ./Configure darwin64-x86_64-cc
    make

Linux:

    ./config -fPIC
    make

**Configure Build**

    # Start from root of gitahead repo.
    mkdir -p build/release
    cd build/release
    cmake -G Ninja -DCMAKE_BUILD_TYPE=Release ../..

If you have Qt installed in a non-standard location, you may have to
specify the path to Qt by passing `-DCMAKE_PREFIX_PATH=<path-to-qt>`
where `<path-to-qt>` points to the Qt install directory that contains
`bin`, `lib`, etc.

**Build**

    ninja

How to Contribute
-----------------

We welcome contributions of all kinds, including bug fixes, new features,
documentation and translations. By contributing, you agree to release
your contributions under the terms of the license.

Contribute by following the typical
[GitHub workflow](https://guides.github.com/introduction/flow/index.html)
for pull requests. Fork the repository and make changes on a new named
branch. Create pull requests against the `master` branch. Follow the
[seven guidelines](https://chris.beams.io/posts/git-commit/) to writing a
great commit message.

License
-------

GitAhead is licensed under the MIT license. See LICENSE.md for details.
