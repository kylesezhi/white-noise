# White Noise

Generates 10-hour white, pink, and brown noise FLAC files with [mise](https://mise.jdx.dev) tasks and ffmpeg.

## Requirements

- [mise](https://mise.jdx.dev) (tasks)
- [ffmpeg](https://ffmpeg.org) with FLAC support

## Usage

Generate all three files in parallel (skips files that already exist):

```sh
mise run make
```

Or generate a single color:

```sh
mise run white
mise run pink
mise run brown
```

## Outputs

| File                   | Color     |
| ---------------------- | --------- |
| `white-noise-10h.flac` | White     |
| `pink-noise-10h.flac`  | Pink      |
| `brown-noise-10h.flac` | Brown     |

Each file is 10 hours, 44.1 kHz, stereo FLAC (~4 GB each, encoded at compression level 0 — noise is incompressible, so higher levels only slow encoding down). Output files are gitignored.

## Tasks

Defined in `mise.toml`:

- `make` — runs the three encodes concurrently, skipping any output that already exists
- `white` / `pink` / `brown` — generate a single file, skipping if it exists