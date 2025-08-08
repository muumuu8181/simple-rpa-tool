# 🤖 シンプルRPAツール

## 📌 概要
Firebase認証とリアルタイムデータベースを活用したブラウザベースのRPAツールです。
タスクの自動化、スケジューリング、実行履歴の管理が可能です。

---

## 🎯 最小手順（3ステップ）

### ステップ1: プロジェクトフォルダの作成

```bash
# Windowsの場合
1. C:\Users\user\Desktop\work\90_cc\0000-00-00-project-template をコピー
2. C:\Users\user\Desktop\work\90_cc\[本日の日付]\ に貼り付け
   例: C:\Users\user\Desktop\work\90_cc\20250807\
3. フォルダ名を変更（例: automation-management-system）
```

**重要**: このテンプレートは`.git`フォルダを削除済みなので、**Git干渉は発生しません**

### ステップ2: GitHubへアップロード

```bash
# プロジェクトフォルダ内で実行
git init
git add .
git commit -m "Initial commit"

# GitHubで新規リポジトリを作成後
git remote add origin https://github.com/[あなたのユーザー名]/[リポジトリ名].git
git push -u origin main
```

### ステップ3: 公開設定の選択

#### 🌐 **パブリック（Web公開する場合）**
1. GitHubリポジトリを**Public**で作成
2. Settings → Pages → Source を `main` ブランチに設定
3. Actions タブで自動デプロイを確認
4. 公開URL: `https://[ユーザー名].github.io/[リポジトリ名]/`

#### 🔒 **プライベート（Web公開しない場合）**
1. GitHubリポジトリを**Private**で作成
2. GitHub Pagesは設定しない
3. チーム内のみでコード共有

---

## ⚠️ アップロード前の確認事項

**Claudeに確認してもらう項目:**
- [ ] パブリック or プライベート？
- [ ] Web公開する？（GitHub Pages使用）
- [ ] 機密情報は含まれていない？

---

## 🌟 主要機能

### 📊 基本機能
- **データ記録**: 日付・時刻・値・タイミング・メモを記録
- **🔐 Google認証**: 安全なGoogle OAuth認証システム
- **🔄 リアルタイム同期**: Firebase Realtime Databaseによるデバイス間同期
- **⌨️ キーボード操作**: ↑↓キーで0.1単位の調整
- **📈 履歴表示**: 時系列でのデータ履歴確認

### 🎨 Core/Custom分離構造 (v0.2の新機能)
- **🚫 Core フォルダ**: 触ってはいけない安全領域（Firebase設定・GitHub Actions等）
- **✅ Custom フォルダ**: 自由にカスタマイズ可能（色・ボタン・動作設定）
- **🔧 簡単変更**: 他のアプリ（食事記録・運動記録等）への転用が容易
- **🛡️ 安全性**: 誤った変更による動作不良を防止

### 🔘 タイミングボタン（カスタマイズ可能）
- 🌅 起床後
- 🚽 トイレ前/後  
- 🛁 風呂前/後
- 🍽️ 食事前/後

## 🚀 使用方法

### ライブデモ
**https://muumuu8181.github.io/0000-00-00-project-template/**

### ローカル実行
1. HTTPサーバーを起動：
   ```bash
   python -m http.server 8000
   ```
   または
   ```bash
   npx http-server -p 8000
   ```

2. ブラウザで `http://localhost:8000` にアクセス

3. Googleアカウントでログイン

4. データを入力して保存

## 🔧 技術仕様

- **フロントエンド**: Vanilla HTML/CSS/JavaScript
- **認証**: Firebase Authentication (Google OAuth)
- **データベース**: Firebase Realtime Database
- **デプロイ**: GitHub Pages
- **対応ブラウザ**: Chrome, Firefox, Safari, Edge

## 📱 データ構造

```json
{
  "users": {
    "userId": {
      "weights": {
        "recordId": {
          "date": "2025-08-06",
          "time": "20:30",
          "value": 50.0,
          "timing": "タイミング",
          "memo": "メモ",
          "timestamp": 1722944530000,
          "userEmail": "user@example.com"
        }
      }
    }
  }
}
```

## 🛡️ プライバシー

- データはユーザー別に完全分離
- Firebase認証による安全なアクセス制御
- 個人情報はFirebaseサーバー側で保護
- アプリコードに個人データは含まれません

## 📁 プロジェクト構造 - Core/Custom分離版

### 🔧 フォルダ構成

```
weight-management-app/
├── core/                           # 🚫 触ってはいけない領域
│   ├── .github/                   # GitHub Actions設定
│   │   └── workflows/
│   │       └── pages.yml          # GitHub Pages自動デプロイ
│   ├── src/                       # Core Firebase設定
│   │   └── firebase-config.js     # Firebase認証・DB設定
│   └── universal-system/          # Universal Template システム
├── custom/                         # ✅ 自由にカスタマイズ可能
│   ├── app-config.js              # アプリ設定（色・ボタン・動作等）
│   └── styles.css                 # カスタムCSS（デザイン全般）
├── index.html                      # メインアプリファイル
└── README.md                       # このファイル
```

### 🚫 CORE フォルダ（触ってはいけない）

- **🔥 Firebase設定** - 認証・データベース接続の核心部分（絶対変更禁止）
- **⚙️ GitHub Actions** - 自動デプロイ設定（変更するとデプロイ失敗）
- **🛠️ Universal System** - テンプレート基盤（Core変更は全体に影響）

### ✅ CUSTOM フォルダ（自由にカスタマイズ可能）

- **🎨 app-config.js** - アプリ名・ボタン設定・動作設定
- **🎨 styles.css** - カラーテーマ・フォント・レイアウト・ダークモード

## 🔄 他のアプリに変更する方法

### ✅ 変更してOKなファイル
- `custom/app-config.js` → アプリの動作・設定
- `custom/styles.css` → 見た目・デザイン
- `index.html` の表示部分のみ → UI構造

### 🚫 変更NGなファイル
- `core/` 内のすべて
- `index.html` のFirebase設定部分

### 🎯 カスタマイズ例

#### TODOアプリに変更
1. `custom/app-config.js` で：アプリ名・ボタンをTODO関連に変更
2. `custom/styles.css` で：カラーテーマをタスク管理系に変更
3. `index.html` で：入力フィールドをタスク入力に変更

#### メモアプリに変更
1. `custom/app-config.js` で：アプリ名・ボタンをメモ関連に変更
2. `custom/styles.css` で：シンプルなカラーテーマに変更

## ⚡ 開発ワークフロー

1. **カスタマイズ** → `custom/` フォルダのみ編集
2. **テスト** → ローカルでHTTPサーバー起動
3. **デプロイ** → `git push` で自動デプロイ
4. **確認** → https://muumuu8181.github.io/0000-00-00-project-template/

## 🛡️ 保護メカニズム

- **Core分離** - 誤った変更を物理的に防止
- **明確な境界** - 触ってOK/NGが一目瞭然
- **独立カスタマイズ** - 他への影響なし
- **バックアップ保護** - Core部分は常に安全

## 🎯 開発情報

- **バージョン**: v0.1
- **作成日**: 2025-08-07
- **言語**: JavaScript (ES6)
- **ライセンス**: MIT

## 📋 更新履歴

### v0.1 (2025-08-07)
- 汎用アプリテンプレートとしてリリース
- Firebase + Google認証実装済み
- データ記録・履歴表示機能
- キーボード操作対応
- タイミングボタンプリセット
- Core/Custom分離構造
- GitHub Pages デプロイ対応

## 🤝 貢献

Issue・Pull Request歓迎です。改善提案やバグ報告をお待ちしています。

---

**🚀 GitHub Pages**: https://muumuu8181.github.io/0000-00-00-project-template/