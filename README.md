# lib_test/Makefileの説明
makeをすると、静的ライブラリ(.a)を作り、それをリンクした実行ファイル(main)を生成する
手順は以下
    make

静的ライブラリを生成するだけであれば以下でOK.
    gcc -c lib_math.c -o lib_math.o
    ar rcs libmath.a math_lib.o

# lib_test/gtest/buildの説明
gtest以下に、googleテスト（C++）で、C言語の.aを使って試験できる環境を用意した
buildフォルダを生成してrunTestsを生成する。

手順は以下
    mkdir build
    cd build
    cmake ..
    make
    ./runTests

jenkins表示用のxmlファイルを生成するように修正した
手順は以下
    cd build
    cmake ..
    make　　　//test ALLのオプションを入れているので、
               makeすると、make testを実行したことになり、
               make run_gtestsを実行したことになり、
               make runTests --gtest_output=xml:test_results.xmlを実行したことになり、
               JUnit形式のxmlファイルが生成される

# 注意点
CMake では、一度コンパイラを設定すると CMakeCache.txt に保存されるため、
再設定する場合はビルドディレクトリをクリーンアップ（削除）してから再度 CMake を実行する必要がある

rm -rf build/*
cmake ..

# lib_test/gtest/Makefileの説明
Cmakeではなく、普通のMakefileに置き換えたものは、
CMakeLists.txtと同一フォルダに配置した。
make testとすると、test_buildフォルダを生成してrunTestsとJUnit形式のファイルを生成する。