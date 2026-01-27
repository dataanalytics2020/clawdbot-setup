# Clawdbot (Moltbot) Setup

Mac mini で24時間稼働する AI社員環境のセットアップ 🦞

> **Note:** Clawdbot は現在 **Moltbot** にリブランドされました（molt = 脱皮）

## 概要

このリポジトリは、Clawdbot/Moltbot を Mac mini 上で常時稼働させるための設定・スクリプト集です。

## Clawdbot とは

- オープンソースのパーソナルAIアシスタント
- WhatsApp、Telegram、Slack、Discord、iMessage など複数のメッセージングプラットフォームに対応
- ローカルマシンで動作し、ファイル操作・コマンド実行・ブラウザ自動化が可能
- Claude / OpenAI をバックエンドとして使用

## Mac mini を選ぶ理由

- 24時間365日稼働に最適
- 低消費電力 & 静音
- macOS ネイティブ連携（iMessage、オートメーション）
- 買い切りでVPSより長期的にコスト効率が良い
- Ollama 等のローカルAIも実用速度で動作

## 必要要件

| 項目 | 要件 |
|------|------|
| Node.js | **v22 以上** |
| OS | macOS / Linux / Windows (WSL2推奨) |
| API | Anthropic API キー または OpenAI Codex |

## セットアップ

### 1. Mac mini の準備（24時間稼働設定）

```bash
# スリープを無効化
sudo pmset -a sleep 0
sudo pmset -a disksleep 0
sudo pmset -a displaysleep 0

# 電源復旧時に自動起動
sudo pmset -a autorestart 1
```

### 2. Clawdbot/Moltbot のインストール

```bash
# 方法1: ワンライナー（推奨）
curl -fsSL https://molt.bot/install.sh | bash

# 方法2: npm でインストール
npm install -g clawdbot@latest

# オンボーディングウィザードを実行（デーモン自動登録）
moltbot onboard --install-daemon
```

### 3. メッセージングプラットフォーム連携

```bash
# チャンネル設定
moltbot channels login

# 動作確認
moltbot health
moltbot status --all
```

### 4. ソースからビルドする場合

```bash
git clone https://github.com/clawdbot/clawdbot.git
cd clawdbot
pnpm install
pnpm ui:build
pnpm build
pnpm clawdbot onboard --install-daemon
```

## 対応プラットフォーム

- WhatsApp（QRコード認証）
- Telegram
- Slack
- Discord
- iMessage（macOSネイティブ）
- Signal
- Mattermost
- Google Chat
- Microsoft Teams

## ディレクトリ構成

```
clawdbot-setup/
├── README.md
├── scripts/           # 自動化スクリプト
├── config/            # 設定ファイル
├── skills/            # カスタムスキル
└── logs/              # ログファイル
```

## 注意事項

⚠️ **トークン消費に注意**: ヘビーユーザーは2日で$300以上使った報告あり。API使用量を監視することを推奨。

## 参考リンク

- [Moltbot 公式サイト](https://molt.bot/)
- [Clawdbot 公式サイト](https://clawd.bot/)
- [GitHub リポジトリ](https://github.com/clawdbot/clawdbot)
- [Clawdbot Skills コレクション](https://github.com/VoltAgent/awesome-clawdbot-skills)
- [公式ドキュメント](https://docs.molt.bot/start/getting-started)

## ライセンス

MIT
