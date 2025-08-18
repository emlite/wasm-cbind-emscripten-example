# wasm-cbind-example

This is an example C repo which shows how you can use wasm-cbind to target web API via emscripten, wasm-cbind and emlite.

wasm-cbind is fetched in the CMake script using FetchContent.

Do note that using npm is not strictly necessary, however it simplifies bundling emlite and managing its version.

## Usage
```bash
git clone https://github.com/emlite/wasm-cbind-emscripten-example
cd wasm-cbind-emscripten-example
npm i
npm run cmake:config
npm run cmake:build
npm run pack
npm run serve
```

The contents of these commands can be found in the package.json scripts entry.

