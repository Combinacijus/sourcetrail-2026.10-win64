# Sourcetrail 2026.10 — Windows x64 portable build

Unofficial self-contained Windows build of [Sourcetrail 2026.10](https://github.com/petermost/Sourcetrail)
(petermost fork), statically linked against Qt 6.11.1, LLVM/Clang 21.1.2,
Boost 1.91 and ICU 78.3.

**Download:** see the [latest release](../../releases/latest).

## Install

No installation needed. Unzip and run `Sourcetrail.exe`. The MSVC runtime DLLs
are bundled, so it works on a clean Windows install without Visual Studio.

- Windows 10 (1809+) or Windows 11, 64-bit
- Java projects need JDK 21+ and Maven (paths set in the project wizard)

Settings live in the `user` folder created next to the executable, so the
extracted folder stays portable.

## Build notes

Compiled with Visual Studio 2026 (MSVC 14.52.37025), CMake 4.5.0, JDK 25 and
Maven 3.9.16 using the repository's `vcpkg-release` preset. The only source-level
change is a two-line workaround in the installed LLVM 21 header
`clang/Basic/Diagnostic.h` (`DiagnosticsEngine::takeClient` moved out of line),
required because MSVC 14.52 rejects the incomplete-type `unique_ptr` member.
It does not affect program behaviour.

## License

GPLv3 — see `LICENSE.txt` inside the archive. Corresponding source:
https://github.com/petermost/Sourcetrail (tag `2026.10`).

Not affiliated with the Sourcetrail project or its authors.
