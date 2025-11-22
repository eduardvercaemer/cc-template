# cc-template

Minimal C++ project template using CMake:

```sh
cmake -S . -B build
cmake --build build
build/hello-world
```

Running tests:

```sh
cmake --build build --target test
```

### What's included:

1. Git ignore.
2. CMake configuration.
3. VSCode configuration.
4. [Catch2](https://github.com/catchorg/Catch2).
5. [Clang format](https://clang.llvm.org/docs/ClangFormat.html).
6. [Clang tidy](https://clang.llvm.org/extra/clang-tidy/checks/list.html).
7. [Include-what-you-use](https://github.com/include-what-you-use/include-what-you-use).
8. Stricter compilation flags.
