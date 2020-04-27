# Env
OS: Ubuntu 19.10

LLVM & Clang: built from LLVM source, branch 9.0

Code editor: VSCode (surprisingly easy to config and use!)

The tutorial from LLVM official site is not the worst OSS tutorial, but it is bad enough. I started with the OCaml version, since that pops up top of rank in Google search, I and thought I'd have to pick up my OCaml compiler skill again, stayed late into night and failed here and there. Even though I have limited knowledge in CMake but I have close to 0 knowledge in ocamlbuild. After a few more searches, I found there is a C++ version, which is much better to follow. This repo serves as a log of my journey (code, learning and fix) with this LLVM kaleidoscope tutorial.

Each commit with Lesson X is the code list of the necessary changes for that lesson.


# Compile
clang++ -O3 -c $(llvm-config --cxxflags) toy.cpp -o toy.o
clang++ toy.o $(llvm-config --ldflags --libs) -lpthread -lncurses

03 Code generation to LLVM IR
clang++ -g -O3 toy.cpp `llvm-config --cxxflags --ldflags --system-libs --libs core` -o toy

04 JIT and Optimizer
An introduction to JIT: https://eli.thegreenplace.net/2013/11/05/how-to-jit-an-introduction/
History of JIT: http://eecs.ucf.edu/~dcm/Teaching/COT4810-Spring2011/Literature/JustInTimeCompilation.pdf
clang++ -g toy.cpp `llvm-config --cxxflags --ldflags --system-libs --libs core mcjit native orcjit` -rdynamic -O3 -o toy

05 Control Flow
06 User-defined operators
