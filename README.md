# make-objectcapture

> 日本語のREADMEはこちらです: [README.ja.md](README.ja.md)

A command-line tool to create 3D models from photos using Apple's Object Capture API. This tool runs on Apple silicon Macs with macOS Monterey and later.

## Requirements

-   **Runtime**: An Apple silicon (M1 or newer) Mac running macOS Monterey (12.0) or later.
-   **Build**: Xcode 13 or later.

## Installation

You can either use the pre-compiled binary included in the repository or build it from source.

To build from source:
```bash
swift build -c release
# The binary will be located at ./.build/release/make-objectcapture
```

## Usage

Run the tool from your terminal, providing a detail level, an input directory of images, and an output path for the `.usdz` model.

```bash
./make-objectcapture [detail] [input-directory] [output-file.usdz]
```

**Example:**
```bash
./make-objectcapture full ./photos/ my-model.usdz
```

## Detail Levels

The `detail` parameter controls the quality and file size of the resulting 3D model.

| Detail    | Max Triangles | Estimated File Size | Texture Size      |
| :-------- | :------------ | :------------------ | :---------------- |
| `preview` | < 25k         | < 5MB               | 1024 x 1024       |
| `reduced` | < 50k         | < 10MB              | 2048 x 2048       |
| `medium`  | < 100k        | < 30MB              | 4096 x 4096       |
| `full`    | < 250k        | < 100MB             | 8192 x 8192       |
| `raw`     | < 30M         | Varies              | 8192 x 8192 (multiple) |

## See Also

-   [Apple Developer: Object Capture](https://developer.apple.com/augmented-reality/object-capture/)
-   [Apple Developer: PhotogrammetrySession Documentation](https://developer.apple.com/documentation/realitykit/photogrammetrysession)
-   [Blog Post by Taisuke Fukuno](https://fukuno.jig.jp/3489)

## License

MIT License — see [LICENSE](LICENSE).