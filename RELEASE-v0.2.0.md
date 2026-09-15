# VoxeLibre Web v0.2.0

This release is the full VoxeLibre 0.93.0-SNAPSHOT game running in the real
Luanti 5.17.0-dev C++ engine compiled to WebAssembly.

## Source and build

- Luanti source revision: `c81c72181` (`portal-singlethread` working tree with
  the browser pthread, persistence, loopback networking, audio, and rendering fixes)
- VoxeLibre content source: full `voxelibre-content.zip` from asset revision
  `5d5a4ae55b820aef820e60741bcd9e1f2e81b57f`
- Emscripten: 6.0.3
- Architecture: `-pthread`, shared WebAssembly memory, `PROXY_TO_PTHREAD`,
  `OFFSCREEN_FRAMEBUFFER`, WebGL 2, OpenAL/Vorbis, and IDBFS
- The complete game is preloaded at `/games/voxelibre`; no runtime zip
  extraction or reduced browser content pack is used.

## Release assets

| File | Bytes | SHA-256 |
| --- | ---: | --- |
| `luanti.data` | 113902717 | `88ade86a0344d25fe28b33a4035329868869d3ab5e54adb06501bd4fef88db7b` |
| `luanti.js` | 1172328 | `6d8e16bb52027cda16e2610f22137f8fa243359e1675c13d980cf6ac2511c609` |
| `luanti.wasm` | 10261209 | `8fe95259497e883352bf028757c61a7851159dacc318350d804c9f93854ee0cd` |
| `voxelibre-content.zip` | 84316165 | `0967596b873c6505b00ee3c0a2411a204b96139a03c81438faaff404a7f2bf3a` |

The full source archive contains 7,220 zip entries, including 2,930 textures,
520 Lua files, and 476 OGG audio files.

## Browser acceptance

- Worker-main, WebGL, pointer-lock, and cross-origin isolation probe passed.
- IDBFS save/reload probe passed.
- Two complete Chromium runs created a VoxeLibre world, joined the internal
  server, rendered gameplay, accepted keyboard/mouse/inventory input, activated
  VoxeLibre music, saved the SQLite-backed world, reloaded the page, restored
  the world from IndexedDB, and re-entered it without an abort or out-of-memory
  error.
