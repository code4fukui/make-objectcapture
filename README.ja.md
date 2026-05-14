# make-objectcapture

AppleのObject Capture APIを使用して、写真から3Dモデルを作成するコマンドラインツールです。このツールは、macOS Monterey以降を搭載したAppleシリコンMacで動作します。

## 必要条件

- **実行環境**: macOS Monterey（12.0）以降を搭載したAppleシリコン（M1以降）のMac。
- **ビルド環境**: Xcode 13以降。

## インストール

リポジトリに含まれるコンパイル済みのバイナリを使用するか、ソースからビルドすることができます。

ソースからビルドする場合:
```bash
swift build -c release
# バイナリは ./.build/release/make-objectcapture に出力されます
```

## 使い方

ターミナルからツールを実行し、詳細レベル（detail）、入力画像のディレクトリ、出力する `.usdz` モデルのパスを指定します。

```bash
./make-objectcapture [detail] [input-directory] [output-file.usdz]
```

**例:**
```bash
./make-objectcapture full ./photos/ my-model.usdz
```

## 詳細レベル

`detail` パラメータは、生成される3Dモデルの品質とファイルサイズを制御します。

| 詳細レベル | 最大ポリゴン数 | 推定ファイルサイズ | テクスチャサイズ      |
| :-------- | :------------ | :------------------ | :---------------- |
| `preview` | < 25k         | < 5MB               | 1024 x 1024       |
| `reduced` | < 50k         | < 10MB              | 2048 x 2048       |
| `medium`  | < 100k        | < 30MB              | 4096 x 4096       |
| `full`    | < 250k        | < 100MB             | 8192 x 8192       |
| `raw`     | < 30M         | 可変                | 8192 x 8192（複数） |

## 関連情報

- [Apple Developer: Object Capture](https://developer.apple.com/augmented-reality/object-capture/)
- [Apple Developer: PhotogrammetrySession ドキュメント](https://developer.apple.com/documentation/realitykit/photogrammetrysession)
- [福野泰介のブログ記事](https://fukuno.jig.jp/3489)

## ライセンス

MIT License — 詳細は [LICENSE](LICENSE) を参照してください。
