# guitest_sdl3
testing how complicated it would be to put a gui application as the github-pages site.

contrary to what the name might suggest i use sdl3.

## result
https://konstantinneuroth.github.io/guitest_sdl2/guitest_sdl.html

## usage:

install emscripten as described on their page https://emscripten.org/docs/getting_started/downloads.html

create a build folder

navigate to the build folder

build via

`{ emcmake cmake .. }`

`{ emmake make }`

note the switch to make on the second command
 
 output should be
 
 - guitest_sdl.html
 - guitest_sdl.js
 - guitest_sdl.wasm
 
as seen in the docs folder
