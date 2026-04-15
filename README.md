# BGP Simulator (WebAssembly Edition)

**Live Demo:** bgp.connor-ingram.com

This is a purely client-side, browser-based implementation of the BGP Simulator. The core engine is written in C++ and compiled to WebAssembly (WASM) using Emscripten, allowing massive graph traversals and BGP propagation to run at near-native speeds directly in the user's browser without a backend server.

## Architecture
* **Backend Engine:** C++ (compiled to `.wasm`)
* **Frontend UI:** HTML5, JavaScript (ES6 Modules), and Tailwind CSS.
* **Hosting:** Deployed instantly via Cloudflare Pages.

## How it Works
Due to browser security restrictions, the UI utilizes the HTML5 `FileReader` API to read the CAIDA, ROV, and Announcement CSV files into memory as raw strings. These strings are passed to the WebAssembly module via Embind (`wasm_bindings.cpp`). The C++ engine builds the graph, runs the valley-free propagation, and returns the target ASN's Routing Information Base (RIB) as a formatted string back to the DOM.
