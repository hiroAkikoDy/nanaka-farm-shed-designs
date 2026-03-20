# 🏡 nanaka-farm-shed-designs

**ナナカファーム 農作業小屋 設計図 & 3Dモデル**

[![Zenn記事](https://img.shields.io/badge/Zenn-記事を読む-3EA8FF?logo=zenn&logoColor=white)](https://zenn.dev/hiroakikody/articles/47ba166f4dad26)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/hiroakikody/nanaka-farm-shed-designs/blob/main/colab/view_models_open3d.ipynb)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> 「言葉で動くCAD」— **Claude × Blender MCP** で農作業小屋の設計図を1日で4種類作った話

---

## 📐 設計図・モデル一覧

| # | 種別 | サイズ | 構造 | Blender | PLY |
|---|------|--------|------|---------|-----|
| ① | 単管パイプ小屋（本番） | 6,000×5,000mm（30㎡） | φ48.6mm 単管 | [.blend](blender/tankan_shed_30sqm.blend) | [.ply](blender/tankan_shed_30sqm.ply) |
| ② | 単管パイプ小屋（練習版） | 1,820×2,730mm（約3畳） | φ48.6mm 単管 | [.blend](blender/tankan_shed_mini_3jo.blend) | [.ply](blender/tankan_shed_mini_3jo.ply) |
| ③ | 木造農作業小屋（本番） | 6,000×5,000mm（30㎡） | 木造軸組 105角柱 | [.blend](blender/wood_shed_30sqm.blend) | [.ply](blender/wood_shed_30sqm.ply) |
| ④ | 木造農作業小屋（練習版） | 1,820×2,730mm（約3畳） | 木造軸組 105角柱 | [.blend](blender/wood_shed_mini_3jo.blend) | [.ply](blender/wood_shed_mini_3jo.ply) |

---

## 🔄 Google Colab でぐりぐり触れます

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/hiroakikody/nanaka-farm-shed-designs/blob/main/colab/view_models_open3d.ipynb)

**`Runtime → Run all`** を押すだけで全4モデルが表示されます。インストール不要。

| 操作 | 動作 |
|------|------|
| 🖱️ 左ドラッグ | 回転（上下左右から確認） |
| 🖱️ 右ドラッグ | 平行移動 |
| 🖱️ スクロール | ズームイン／アウト |
| 🏠 ホームボタン | 視点リセット |

**技術構成：** Open3D で `.ply` を読み込み → Plotly `Mesh3d` でインタラクティブ表示（EGL/GPU不要・ColabのCPUランタイムで動作）

---

## 🗂️ リポジトリ構成

```
nanaka-farm-shed-designs/
├── blender/
│   ├── tankan_shed_30sqm.blend      # 単管パイプ小屋（本番 30㎡）
│   ├── tankan_shed_30sqm.ply
│   ├── tankan_shed_mini_3jo.blend   # 単管パイプ小屋（練習版 約3畳）
│   ├── tankan_shed_mini_3jo.ply
│   ├── wood_shed_30sqm.blend        # 木造農作業小屋（本番 30㎡）
│   ├── wood_shed_30sqm.ply
│   ├── wood_shed_mini_3jo.blend     # 木造農作業小屋（練習版 約3畳）
│   └── wood_shed_mini_3jo.ply
└── colab/
    └── view_models_open3d.ipynb     # Plotly インタラクティブビューア
```

---

## 🏗️ 設計仕様

### 単管パイプ版（本番 30㎡）

| 項目 | 仕様 |
|------|------|
| 外寸 | 6,000 × 5,000 mm |
| 南側軒高 | 3,000 mm |
| 北側軒高 | 2,500 mm |
| 屋根 | 片流れ 1/10勾配（5.7°）ポリカ波板 t8 |
| 主管 | φ48.6mm t2.4mm（JIS A 8951準拠） |
| 柱ピッチ | X方向 1,500mm × Y方向 2,500mm |
| 基礎 | スパイラル杭 φ48.6mm 地中900mm × 15本 |
| 建具 | 両開きドア W1,200 × H2,000mm |
| 概算費用 | ¥237,100〜 |

### 木造版（本番 30㎡）

| 項目 | 仕様 |
|------|------|
| 外寸 | 6,000 × 5,000 mm |
| 南側軒高 | 3,000 mm |
| 北側軒高 | 2,500 mm |
| 屋根 | 片流れ 1/10勾配（5.7°）ポリカ波板 t8 |
| 柱 | 105 × 105mm @1,500mmピッチ |
| 軒桁 | 105 × 150mm |
| 垂木 | 45 × 105mm @1,000mm |
| 基礎 | 束石 200 × 200 × 150mm |
| 建具 | 引き戸 W1,800 × H2,100mm |

> 農研機構「建設足場資材利用園芸ハウスの施工マニュアル」（2017年）準拠

---

## 🔧 技術スタック

```
Claude Desktop（claude-sonnet-4系）
    ↓ MCP（Model Context Protocol）port 9876
Blender 4.x + blender-mcp アドオン
    ↓ Blender Python API（bpy）で自動生成
.blend ファイル → .ply エクスポート
    ↓
GitHub リポジトリ公開
    ↓
Google Colab（Open3D + Plotly）でブラウザ上インタラクティブ表示
```

### Blenderモデリングの工夫

- **`transform_apply` 不使用パターン** — スケールをそのまま残すことでワールド座標のずれを防止
- **2点間接続法（`pipe_between`関数）** — `rotation_difference()` で任意方向の単管パイプを正確配置
- **傾斜角の符号管理** — `rotation_euler[0] = -slope` で南高・北低の片流れ屋根を正確に表現

### Colab表示の工夫

- **Open3D `OffscreenRenderer` は使わない** — ColabのCPU環境ではEGLエラーでカーネルがクラッシュする
- **Plotly `Mesh3d`** — GPU不要、Colabセル内でマウス操作可能

---

## 🚀 使い方

### Colabでモデルを触る（推奨）

[Open In Colab](https://colab.research.google.com/github/hiroakikody/nanaka-farm-shed-designs/blob/main/colab/view_models_open3d.ipynb) を開いて `Runtime → Run all`

### Blenderファイルをローカルで開く

```bash
git clone https://github.com/hiroakikody/nanaka-farm-shed-designs.git
```

`blender/` フォルダの `.blend` ファイルを Blender 4.x で開く。

### ローカルでOpen3Dインタラクティブ表示

```bash
pip install open3d plotly jupyter
jupyter notebook colab/view_models_open3d.ipynb
```

CELL 9 の `draw_interactive('tankan_mini')` でウィンドウが開き、マウスでぐりぐり操作できます。

---

## 📚 参考資料

- [農研機構「建設足場資材利用園芸ハウスの施工マニュアル」(2017)](https://www.naro.go.jp/publicity_report/publication/files/warc_man_hausupanfu20170314a_2.pdf)
- 学研ムック DIYシリーズ「屋根付きウッドデッキの作り方」（Gakken、2014）
- [blender-mcp](https://github.com/ahujasid/blender-mcp)

---

## ✍️ 関連記事

- **Zenn**: [AI × Blender MCP で農作業小屋の設計図を1日で4種類作った話](https://zenn.dev/hiroakikody/articles/47ba166f4dad26)
- **Zenn**: [@hiroakikody の記事一覧](https://zenn.dev/hiroakikody)

---

## 📄 ライセンス

MIT License — 設計図・コード・3Dモデルは自由に改変・利用・再配布可能です。  
実際の建設時は構造安全性を専門家に確認することを推奨します。

---

*七花ファーム（ナナカファーム）　熊本県 / 古閑 弘晃（hiroakiKody）*
