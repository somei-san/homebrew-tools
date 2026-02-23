# homebrew-clip-show

`clip-show` を Homebrew で配布するための Tap リポジトリです。

- source repository: <https://github.com/somei-san/clip-show>
- formula: `Formula/clip-show.rb`

## clip-show とは

`clip-show` は macOS 向けの常駐アプリです。  
クリップボードにコピーされたプレーンテキストを検知し、画面中央に短時間（約1秒）HUD 表示します。

## 対応環境

- macOS

## インストール（初回導入）

```bash
brew tap somei-san/clip-show
brew install clip-show
brew services start clip-show
```

各コマンドの意味:

1. `brew tap somei-san/clip-show`: `somei-san/clip-show` Tap を Homebrew に登録します。
2. `brew install clip-show`: Tap に含まれる `clip-show` Formula から本体をインストールします。
3. `brew services start clip-show`: `clip-show` を常駐起動し、ログイン時の自動起動も有効にします（初期導入時は必須）。

1 行で実行する場合:

```bash
brew tap somei-san/clip-show && brew install clip-show && brew services start clip-show
```

## 起動・停止（ログイン時自動起動）

`clip-show` は Homebrew Service として動作します。

```bash
brew services start clip-show
```

停止:

```bash
brew services stop clip-show
```

状態確認:

```bash
brew services list
```

## 動作確認

```bash
clip-show --version
clip-show --help
```

## ログ

Homebrew のログ出力先:

```bash
$(brew --prefix)/var/log/clip-show.log
```

## アンインストール

```bash
brew services stop clip-show
brew uninstall clip-show
```

Tap 自体も外す場合:

```bash
brew untap somei-san/clip-show
```

## メンテナー向け

`clip-show` 側でリリースタグ（例: `v0.1.0`）を作成後、`clip-show` リポジトリの生成スクリプトで Formula を更新できます。

```bash
./scripts/homebrew/generate_formula.sh somei-san <version> ./Formula/clip-show.rb
```

詳細手順:

<https://github.com/somei-san/clip-show/blob/main/docs/Homebrewで公開する手順.md>
