# `apkeep-files`

Files required to compile [`apkeep`](https://www.github.com/EFForg/apkeep/).

## `Configurations-15-android.conf.patch`

This file is required to build `apkeep` with the OpenSSL 3.2.1 dependency in a way that works with `termux`.  When building OpenSSL, the dynamic library extensions must be specified with the major version number.

## `openssl-3.2.1-static-x86_64-pc-windows-msvc.tar.gz`

This file is required to build `apkeep` for Windows x64.  It contains the statically compiled libraries for `openssl-3.2.1` built from the sources available on [https://www.openssl.org/](https://www.openssl.org/).  Cross-compilation of these libraries was not successful, so this had to be built on an actual Windows x64 platform (in this case, Server 2022).  [Visual Studio Community](https://visualstudio.microsoft.com/vs/community/) is needed with the Desktop Development with C++ workload.  [Strawberry Perl](https://strawberryperl.com/) and [NASM](https://www.nasm.us/) are also needed, and must be added to the `%PATH%` environmental variable.  Instructions to build can be found [here](https://wiki.openssl.org/index.php/Compilation_and_Installation#W64).  The build was made using the `VC-WIN64A` target:

    perl Configure -static VC-WIN64A
    nmake

To reduce the size of the download, only `libssl.lib`, `libcrypto.lib`, and `include/` results of the compilation are included in the file.
