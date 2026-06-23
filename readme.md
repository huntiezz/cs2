# cs2-offsets

Auto-generated Counter-Strike 2 offsets and schema dumps, updated shortly after each game patch. Output comes from [cs2-dumper](https://github.com/a2x/cs2-dumper) and is published here so you can pull fresh headers or JSON without running the dumper yourself.

Each update includes a build number and timestamp in `info.json`.

## What's in here

- **Core offsets** - `offsets.*` (client, engine2, inputsystem globals)
- **Schema dumps** - one set per module (`client_dll`, `engine2_dll`, `server_dll`, etc.)
- **Buttons and interfaces** - input button IDs and engine interface lists
- **Four formats per file** - pick what your project uses:
  - `.hpp` - C/C++
  - `.cs` - C#
  - `.rs` - Rust
  - `.json` - anything else

## Stats

- 21 module dumps (client, engine2, server, panorama, particles, and others)
- 1 offsets bundle
- 1 buttons bundle
- 1 interfaces bundle
- 4 formats each (hpp, cs, rs, json)
- 86 data files total

## Usage

Include the headers in your project, or fetch them at runtime from raw GitHub URLs.

**C++ example:**

```cpp
#include "offsets.hpp"
#include "client_dll.hpp"
#include "engine2_dll.hpp"
```

**Runtime download example:**

```cpp
const std::vector<std::pair<std::string, std::string>> files = {
    { "offsets.hpp",     "https://raw.githubusercontent.com/huntiezz/cs2-offsets/main/offsets.hpp" },
    { "client_dll.hpp",  "https://raw.githubusercontent.com/huntiezz/cs2-offsets/main/client_dll.hpp" },
    { "engine2_dll.hpp", "https://raw.githubusercontent.com/huntiezz/cs2-offsets/main/engine2_dll.hpp" },
};
```

**JSON example:**

```json
// offsets.json - top-level keys are module names
{
  "client.dll": { "dwEntityList": 38435624, ... },
  "engine2.dll": { "dwBuildNumber": 6317316, ... }
}
```

Check `info.json` for the current game build and dump time before wiring offsets into your code.

## Notes

- Offsets break on game updates. Re-pull after patches.
- Schema class names and counts change between builds - do not hardcode counts from old dumps.
- This repo only hosts the generated output. To dump locally, use [cs2-dumper](https://github.com/a2x/cs2-dumper).
