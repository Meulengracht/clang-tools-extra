include_directories(${CMAKE_CURRENT_SOURCE_DIR}/..)

set(LLVM_LINK_COMPONENTS
  FuzzMutate
  Support
  )

# This fuzzer runs on oss-fuzz, so keep it around even if it looks unreferenced.
add_llvm_fuzzer(clangd-fuzzer
  clangd-fuzzer.cpp
  DUMMY_MAIN DummyClangdMain.cpp
  )

target_link_libraries(clangd-fuzzer
  PRIVATE
  clangBasic
  clangDaemon
  clangFormat
  clangFrontend
  clangSema
  clangTooling
  clangToolingCore
  )
