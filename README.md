# homebrew-clip-show

`clip-show` を Homebrew で配布するための Tap リポジトリです。

- source repository: <https://github.com/somei-san/clip-show>
- formula: `clip-show.rb`

## clip-show とは

`clip-show` は macOS 向けの常駐アプリです。  
クリップボードにコピーされたプレーンテキストを検知し、画面中央に短時間（約1秒）HUD 表示します。

## 対応環境

- macOS

## インストール

```bash
brew tap somei-san/clip-show
brew install clip-show
brew services start clip-show
```

1 行で実行する場合:

```bash
brew tap somei-san/clip-show && brew install clip-show && brew services start clip-show
```

## 起動・停止（ログイン時自動起動）

`clip-show` は Homebrew Service として起動できます。

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

## メンテナー向け（Formula 更新）

`clip-show` 側でリリースタグ（例: `v0.1.0`）を作成後、`clip-show` リポジトリの生成スクリプトで Formula を更新できます。

```bash
./scripts/homebrew/generate_formula.sh somei-san <version> <output-path>
```

このリポジトリでは `clip-show.rb` を更新対象にします。
