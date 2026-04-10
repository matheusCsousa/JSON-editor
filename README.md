# JSON Editor — TUI

Terminal-based JSON editor built with Rust, [ratatui](https://github.com/ratatui-org/ratatui) and [crossterm](https://github.com/crossterm-rs/crossterm). Lets you build flat key-value JSON objects interactively and export them to a file.

## Controls

**Normal mode**

| Key | Action |
|---|---|
| `e` | Add a new key-value pair |
| `q` | Quit (prompts for export) |

**Editing mode** (popup)

| Key | Action |
|---|---|
| `Tab` | Switch between Key / Value fields |
| `Enter` | Confirm and save the pair |
| `Backspace` | Delete last character |
| `Esc` | Cancel and return to normal mode |

**Exit prompt**

| Key | Action |
|---|---|
| `y` | Print JSON to stdout and exit |
| `n` / `q` | Exit without output |

## Usage

```bash
cargo run
```

Save output to a file:

```bash
cargo run > output.json
```

> The app renders to `stderr` so `stdout` stays clean for redirection.

## Dependencies

| Crate | Purpose |
|---|---|
| `ratatui` | TUI layout and widgets |
| `crossterm` | Cross-platform terminal input/raw mode |
| `serde_json` | JSON serialization on export |
| `color-eyre` | Error handling |

## Project Structure

```
.
├── src/
│   ├── main.rs   # Terminal setup, event loop, key handling
│   ├── app.rs    # State machine (Main / Editing / Exiting)
│   └── ui.rs     # Ratatui layout, popup rendering
├── test.json     # Sample output file
└── Cargo.toml
```

## Limitations

- Only supports flat `String → String` pairs — no nested objects or arrays
- No editing or deleting existing pairs after they are saved
