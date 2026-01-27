# Clawdbot Setup

Mac mini で24時間稼働する AI社員環境のセットアップ

## 概要

このリポジトリは、Clawdbot を Mac mini 上で常時稼働させるための設定・スクリプト集です。

## Clawdbot とは

- オープンソースのパーソナルAIアシスタント
- WhatsApp、Telegram、Slack、iMessage など複数のメッセージングプラットフォームに対応
- ローカルマシンで動作し、ファイル操作・コマンド実行・ブラウザ自動化が可能
- Claude をバックエンドとして使用

## Mac mini を選ぶ理由

- 24時間365日稼働に最適
- 低消費電力 & 静音
- macOS ネイティブ連携（iMessage、オートメーション）
- 買い切りでVPSより長期的にコスト効率が良い
- Ollama 等のローカルAIも実用速度で動作

## セットアップ

### 1. Mac mini の準備

```bash
# スリープを無効化
sudo pmset -a sleep 0
sudo pmset -a disksleep 0
sudo pmset -a displaysleep 0

# 電源復旧時に自動起動
sudo pmset -a autorestart 1
```

### 2. Clawdbot のインストール

```bash
# 公式リポジトリからクローン
git clone https://github.com/steipete/clawdbot.git
cd clawdbot

# 依存関係のインストール
npm install
```

### 3. 環境変数の設定

```bash
cp .env.example .env
# .env ファイルを編集して API キーなどを設定
```

## ディレクトリ構成

```
clawdbot-setup/
├── README.md
├── scripts/           # 自動化スクリプト
├── config/            # 設定ファイル
├── skills/            # カスタムスキル
└── logs/              # ログファイル
```

## 参考リンク

- [Clawdbot 公式サイト](https://clawd.bot/)
- [GitHub リポジトリ](https://github.com/steipete/clawdbot)
- [Clawdbot Skills コレクション](https://github.com/VoltAgent/awesome-clawdbot-skills)

## ライセンス

MIT
