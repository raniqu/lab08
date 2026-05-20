# Отчет к лабораторной работе 7

## Что сделано

### 1. Удалён submodule GTest
```
git rm -rf third-party/gtest
```

### 2. CMakeLists.txt обновлён на FetchContent

```
include(FetchContent)
FetchContent_Declare(
  googletest
  GIT_REPOSITORY https://github.com/google/googletest.git
  GIT_TAG release-1.12.1
)
FetchContent_MakeAvailable(googletest)
```

### 3. Добавлено demo-приложение

### Сборка
Сборка с флагом BUILD_TESTS=ON.
```
arina@debian:~/raniqu/workspace/projects/lab08$ cmake --build _builds --target test
Running tests...
Test project /home/arina/raniqu/workspace/projects/lab08/_builds
    Start 1: check
1/1 Test #1: check ............................   Passed    0.01 sec

100% tests passed, 0 tests failed out of 1

Total Test time (real) =   0.03 sec
```
```
arina@debian:~/raniqu/workspace/projects/lab08$ ./_builds/check
Running main() from /home/arina/raniqu/workspace/projects/lab08/_builds/_deps/googletest-src/googletest/src/gtest_main.cc
[==========] Running 1 test from 1 test suite.
[----------] Global test environment set-up.
[----------] 1 test from Print
[ RUN      ] Print.InFileStream
[       OK ] Print.InFileStream (0 ms)
[----------] 1 test from Print (0 ms total)

[----------] Global test environment tear-down
[==========] 1 test from 1 test suite ran. (0 ms total)
[  PASSED  ] 1 test.
```
Actions отработал зелёным
