# Claude Code学習プロジェクト - KAOS/Alloy形式手法アプローチ

**作成者**: 古閑弘晃  
**作成日**: 2026年1月26日  
**目的**: 形式手法（KAOS/Alloy）を活用して、Claude Codeを体系的に習得し、本業（農業）の生産性をデータ駆動型で向上させる

---

## 📚 プロジェクト概要

このプロジェクトは、**ソクラテス式問答**を通じて明確化されたゴール構造を、**KAOS（ゴール志向分析）**と**Alloy（形式記法）**で形式化し、**Claude Code学習**に活かすものです。

### 🎯 ルートゴール
**「Claude Codeを使って、本業（農業）の生産性をデータ駆動型で向上させる」**

### 🌟 プロジェクトの特徴
1. **形式手法による曖昧性の排除**
   - KAOSでゴール構造を可視化
   - Alloyで論理的整合性を検証
   - AIへの指示精度を向上

2. **段階的・検証可能な学習**
   - 各フェーズの達成条件を形式的に定義
   - Alloy Analyzerで進捗を検証可能

3. **実業務への直接適用**
   - 農作業記録の自動化
   - デジタル三河屋（顧客関係構築）
   - データ駆動型意思決定

---

## 📁 ファイル構成

```
claude_code_learning/
├── README.md                          # このファイル
├── kaos_claude_code_learning.png      # KAOSゴール図（NetworkX生成）
├── kaos_goal_diagram.py               # KAOS図生成Pythonスクリプト
├── kaos_claude_code_learning.graphml  # GraphML形式（yEd等で編集可能）
├── claude_code_learning_kaos.als      # Alloy形式記法モデル
├── ALLOY_MODEL_GUIDE.md              # Alloyモデル解説書
└── CLAUDE_CODE_LEARNING_ROADMAP.md   # 詳細学習ロードマップ
```

---

## 🚀 クイックスタート

### 1. KAOS図の確認
`kaos_claude_code_learning.png` を開いて、ゴール構造を把握

**ゴール階層**:
```
ROOT: Claude Codeで生産性向上
├─ G1: 正確な指示ができる【最優先】
│  ├─ G11: KAOS/Alloyで要件形式化
│  ├─ G12: 形式要件をプロンプトに変換
│  └─ G13: Claude Codeワークフロー習得
│     ├─ G131: 探索フェーズ
│     ├─ G132: 計画フェーズ
│     ├─ G133: 実装フェーズ
│     └─ G134: コミットフェーズ
├─ G2: データが継続的に蓄積される【優先度1】
│  ├─ G21: 入力項目最適化
│  ├─ G22: 入力リマインダー
│  └─ G23: MCP経由でNeo4j操作
└─ G3: 顧客との関係を構築【優先度2】
   ├─ G31: 顧客データ管理
   ├─ G32: パーソナライズ提案
   └─ G33: GNNサジェスト（将来）
```

### 2. Alloyモデルの検証

#### インストール（macOS）
```bash
brew install --cask alloy
```

#### モデルを開く
1. Alloy Analyzerを起動
2. `claude_code_learning_kaos.als` を開く

#### 検証実行
```
Execute → Check NoCycles              # 循環依存の検証
Execute → Check RootRequiresG1andG2   # ルートゴール達成条件
Execute → Run Phase1_Complete         # フェーズ1完了シナリオ
Execute → Run G1_Achieved             # 最優先ゴール達成
```

### 3. 学習ロードマップの確認
`CLAUDE_CODE_LEARNING_ROADMAP.md` を読んで、具体的な学習計画を把握

---

## 🎓 学習フェーズ

### フェーズ0: 準備（1週間）
- Alloy Analyzerセットアップ
- Notionデータベース構築
- 技術書1-2章読了

### フェーズ1: 基礎固め（2-3週間）
- Claude Codeベストプラクティス習得
- ワークフロー（探索→計画→実装→コミット）
- プロジェクト: TODOアプリ

### フェーズ2: 形式手法統合（2-3週間）
- KAOS→Alloy→プロンプトのパイプライン確立
- プロジェクト: 農作業記録入力支援ツール

### フェーズ3: MCP実践（3-4週間）
- Neo4j/Notion MCP統合
- データ蓄積の自動化
- プロジェクト: 農作業管理システム拡張

### フェーズ4: デジタル三河屋（継続的）
- 顧客データ管理
- パーソナライズ提案
- 将来的にGNN活用

---

## 🔍 ドキュメント詳細

### 1. KAOS図（PNG + GraphML）
**目的**: ゴール構造の可視化

**活用方法**:
- NetworkX生成PNG: 全体俯瞰
- GraphML: yEd, Gephi等で編集・カスタマイズ
- プレゼン資料、ブログ記事への活用

### 2. Alloyモデル（`.als`）
**目的**: ゴール構造の形式的検証

**主要要素**:
- **Signature**: Goal, RefinementType (AND/OR), Priority, Status
- **Facts**: 非循環性、ANDゲート、ORゲートの制約
- **Predicates**: 各フェーズ完了条件
- **Assertions**: ルートゴール達成条件、優先度整合性

**活用方法**:
- ゴール追加時の整合性チェック
- 達成条件の明確化
- 学習計画の妥当性検証

### 3. Alloyモデル解説（`.md`）
**目的**: Alloyモデルの理解と活用ガイド

**内容**:
- シグネチャ定義の意味
- 制約条件の詳細解説
- 検証シナリオの実行方法
- Claude Codeとの統合方法

### 4. 学習ロードマップ（`.md`）
**目的**: 具体的な学習計画と進捗管理

**内容**:
- フェーズ別詳細計画
- 週次スケジュール例
- Notionデータベース構造
- 成功基準とマイルストーン

---

## 💡 このアプローチの強み

### 1. 曖昧性の排除
**課題**: 「Claude Codeを使いこなす」は抽象的すぎる

**解決**: 
- KAOSでゴール分解
- Alloyで達成条件を形式化
- 測定可能な基準を設定

### 2. 論理的整合性の保証
**課題**: ゴール間の矛盾や循環参照

**解決**:
- Alloyで自動検証
- ANDゲート/ORゲートの明確な定義
- 依存関係の可視化

### 3. AIへの指示精度向上
**課題**: 自然言語の解釈のブレ

**解決**:
- 形式的に検証された要件
- プロンプトへの変換パイプライン
- 再現可能な開発プロセス

---

## 🎯 期待される成果

### 3ヶ月後
- [ ] Claude Code基礎習得完了（G1達成）
- [ ] 農作業記録の習慣化（G2達成）
- [ ] ブログ投稿10本以上

### 6ヶ月後
- [ ] デジタル三河屋MVP稼働（G3部分達成）
- [ ] 顧客10名以上獲得
- [ ] データ駆動型農業経営の基盤確立

### 1年後
- [ ] ルートゴール達成
- [ ] 本業生産性の測定可能な向上
- [ ] KAOS/Alloy/Claude Codeの知見体系化

---

## 📖 参考リソース

### Claude Code
- [Anthropic: Claude Code Best Practices](https://www.anthropic.com/engineering/claude-code-best-practices)
- [技術評論社: Claude CodeによるAI駆動開発入門](https://gihyo.jp/book/2025/978-4-297-15275-8)

### KAOS
- "Goal-Oriented Requirements Engineering" (van Lamsweerde)
- "Requirements Engineering" (Axel van Lamsweerde)

### Alloy
- [Software Abstractions (書籍)](https://mitpress.mit.edu/9780262528900/software-abstractions/)
- [Alloy Documentation](https://alloytools.org/documentation.html)

---

## 🔄 更新履歴

| 日付 | 内容 |
|------|------|
| 2026-01-26 | プロジェクト開始、KAOS図・Alloyモデル・ロードマップ作成 |
| 2026-02-09 | フェーズ0完了予定 |
| 2026-02-23 | フェーズ1完了予定 |

---

## 📝 次のアクション

### 今週（1/27-2/2）
- [ ] Alloy Analyzerインストール
- [ ] Alloyモデルの検証実行
- [ ] Notionデータベース構築
- [ ] ブログ記事1本執筆開始

### 来週（2/3-2/9）
- [ ] 技術評論社『Claude Code入門』3章
- [ ] TODOアプリのKAOS図作成
- [ ] ブログ記事1本公開

---

## 🤝 フィードバック

このプロジェクトは継続的に改善されます。

**フィードバック歓迎**:
- GitHub Issues（リポジトリ作成後）
- ブログコメント
- Zennスクラップ

---

**最終更新**: 2026年1月26日  
**次回レビュー**: 2026年2月9日（フェーズ0終了時）
