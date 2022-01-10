# `apkeep-files`

Files required to compile [`apkeep`](https://www.github.com/EFForg/apkeep/).

## `openssl-1.1.1m-static-x86_64-pc-windows-msvc.tar.gz`

This file is required to build `apkeep` for Windows x64.  It contains the statically compiled libraries for `openssl-1.1.1m` built from the sources available on [https://www.openssl.org/](https://www.openssl.org/).  Cross-compilation of these libraries was not successful, so this had to be built on an actual Windows x64 platform (in this case, Server 2019).  Instructions to build can be found [here](https://wiki.openssl.org/index.php/Compilation_and_Installation#W64), and the build was made using [Strawberry Perl](https://strawberryperl.com/) for the `VC-WIN64A` target:

    perl Configure -static VC-WIN64A
    nmake

To reduce the size of the download, only `libssl.lib`, `libcrypto.lib`, and `include/` results of the compilation are included in the file.
