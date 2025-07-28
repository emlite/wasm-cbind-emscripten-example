cmake_minimum_required(VERSION 3.20)
project(wasmbind-example)

include(FetchContent)

FetchContent_Declare(
    wasm-cbind
    GIT_REPOSITORY https://github.com/emlite/wasm-cbind.git
    GIT_TAG main
    GIT_SHALLOW True
)

FetchContent_MakeAvailable(wasm-cbind)

add_executable(main src/main.c)
target_link_libraries(main PRIVATE webbind::webbind)
target_compile_options(main PRIVATE -Wno-incompatible-pointer-types)
set_target_properties(main PROPERTIES LINKER_LANGUAGE C SUFFIX .js LINK_FLAGS "-sSINGLE_FILE -sDEFAULT_TO_CXX=0 -sALLOW_MEMORY_GROWTH=1 -sEXPORTED_RUNTIME_METHODS=wasmTable,UTF8ToString,lengthBytesUTF8,stringToUTF8 -sEXPORTED_FUNCTIONS=_malloc,_main -Wl,--strip-all")