# homebrew-tools

`cliip-show` などを Homebrew で配布するための Tap リポジトリです。

## リポジトリ登録（初回のみ）

```bash
brew tap somei-san/tools
```

## 機能1: cliip-show

`cliip-show` は macOS 向けの常駐アプリです。  
クリップボードにコピーされたプレーンテキストを検知し、画面上部（デフォルト、設定で変更可）に短時間（約1秒）HUD 表示します。

- source repository: <https://github.com/somei-san/cliip-show>
- formula: `Formula/cliip-show.rb`

![cliip-show HUDの表示イメージ](docs/assets/cliip-show-hud.png)

### インストール（初回導入）

```bash
brew tap somei-san/tools
brew install somei-san/tools/cliip-show
brew services start cliip-show
```

### 起動・停止（ログイン時自動起動）

`cliip-show` は Homebrew Service として動作します。

```bash
brew services start cliip-show
```

停止:

```bash
brew services stop cliip-show
```

### 動作確認

```bash
cliip-show --version
cliip-show --help
```

### 設定

表示設定は config ファイルで管理できます。

設定ファイル:

- 既定パス: `~/Library/Application Support/cliip-show/config.toml`
- パス変更: `CLIIP_SHOW_CONFIG_PATH=/path/to/config.toml`

初期化と確認:

```bash
cliip-show --config init
cliip-show --config show
```

よく使う設定の変更例:

```bash
cliip-show --config set hud_duration_secs 2.5
cliip-show --config set max_lines 3
cliip-show --config set hud_position top
cliip-show --config set hud_scale 1.2
cliip-show --config set hud_background_color blue
```

設定キー:

- `poll_interval_secs`（既定値: `0.3`、`0.05` - `5.0`）
- `hud_duration_secs`（既定値: `1.0`、`0.1` - `10.0`）
- `max_chars_per_line`（既定値: `100`、`1` - `500`）
- `max_lines`（既定値: `5`、`1` - `20`）
- `hud_position`（既定値: `top`、`top` / `center` / `bottom`）
- `hud_scale`（既定値: `1.1`、`0.5` - `2.0`）
- `hud_background_color`（既定値: `default`、`default` / `yellow` / `blue` / `green` / `red` / `purple`）

設定反映のため、変更後はサービスを再起動してください。

```bash
brew services restart cliip-show
```

### ログ

Homebrew のログ出力先:

```bash
$(brew --prefix)/var/log/cliip-show.log
```

### アンインストール

```bash
brew services stop cliip-show
brew uninstall cliip-show
```

### メンテナー向け

詳細手順:

<https://github.com/somei-san/cliip-show/blob/main/docs/Homebrewで公開する手順.md>
