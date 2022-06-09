# study-webapp

Node.js+Express+MySQLで作る安全なWebアプリケーションの勉強

## やったこと

### package.jsonの作成

以下のコマンドでプロジェクトを新規作成し、package.jsonを作成する。
エントリポイントはapp.jsにする。

```bash
npm init
```

生成されたpackage.jsonは以下になる。

```json
{
  "name": "study-webapp",
  "version": "1.0.0",
  "description": "Node.js+Express+MySQLで作る安全なWebアプリケーションの勉強",
  "main": "app.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "repository": {
    "type": "git",
    "url": "git+https://github.com/mi83ki/study-webapp.git"
  },
  "author": "Tatsuya Miyazaki",
  "license": "MIT",
  "bugs": {
    "url": "https://github.com/mi83ki/study-webapp/issues"
  },
  "homepage": "https://github.com/mi83ki/study-webapp#readme"
}
```

### .gitignoreの作成

1. 「.gitignore」ファイルをルートディレクトリに新規作成する
1. 以下のサイトにアクセスする
    <https://www.toptal.com/developers/gitignore>
1. NodeとVisualStudioCodeを選択して作成ボタンを押下する
1. 作成された文字列を.gitignoreファイルにコピペする

### デバッグの設定

1. VSCodeの実行とデバッグボタンを押す
1. launch.jsonを作成するを選択する
1. 以下の内容に書き換える

    ```json
    {
      // IntelliSense を使用して利用可能な属性を学べます。
      // 既存の属性の説明をホバーして表示します。
      // 詳細情報は次を確認してください: https://go.microsoft.com/fwlink/?linkid=830387
      "version": "0.2.0",
      "configurations": [
        {
          "type": "node",
          "request": "launch",
          "name": "Launch Program",
          "skipFiles": [
            "<node_internals>/**"
          ],
          "program": "${workspaceFolder}/app.js",
          "envFile": "${workspaceFolder}/.env"
        }
      ]
    }
    ```

### .envの作成

環境ファイルを作成する。

1. 「.env」ファイルをルートディレクトリに新規作成する
1. 以下を入力する

    ```env
    PORT=3000
    ```

### app.jsの作成と実行

1. 「app.js」ファイルをルートディレクトリに新規作成する
1. 以下を入力して保存する

    ```javascript
    const PORT = process.env.PORT;
    console.log(PORT);
    ```

1. F5キーを押してデバッグを開始する
1. ターミナルに 3000 が表示されればOK

### 静的解析ツール ESLintのインストール

1. VSCodeの拡張機能で「eslint」を検索してESLintをインストール
1. ターミナルで以下を実行する

    ```bash
    $ npm install eslint@^7.25.0 --dev
    $ npx eslint --init
      √ How would you like to use ESLint? · syntax
      √ What type of modules does your project use? · commonjs
      √ Which framework does your project use? · none
      √ Does your project use TypeScript? · No / Yes
      √ Where does your code run? · browser, node
      √ What format do you want your config file to be in? · JavaScript
    ```

1. 「.eslintrc.js」を開いてextendsとjqueryとrulesを追加する

    ```javascript
    module.exports = {
      "env": {
          "browser": true,
          "jquery": true,
          "commonjs": true,
          "es2021": true,
          "node": true
      },
      "extends": "eslint:recommended",
      "parserOptions": {
          "ecmaVersion": 12
      },
      "rules": {
        "indent": [
          "error",
          2,
          { "SwitchCase": 1}
        ],
        "quotes": [
          "error",
          "double"
        ],
        "semi": [
          "error",
          "always"
        ],
        "no-unused-vars": [
          "error",
          {
            "vars": "all",
            "args": "none"
          }
        ]
        "no-console": [
          "off"
        ]
      }
    };
    ```

### expressのインストール

ターミナルを開いて以下のコマンドでexpressモジュールをインストールする

```bash
npm install express
```

### ejsのインストール

1. VSCodeの拡張機能で「ejs」を検索してEJS language supportをインストール
1. ejsパッケージをインストール

    ```bash
    npm install ejs
    ```

### serve-faviconパッケージのインストール

faviconを配信するためにserve-faviconをインストールする

```bash
npm install serve-favicon
```

### サーバーサイド情報の隠ぺい

以下のコードをapp.jsに記述することで、サーバー側の情報を隠ぺいすることができる。
これを記述しない場合、httpヘッダの応答からnode.jsのexpressを使用していることがバレるため、脆弱性情報から攻撃されやすくなる。

```javascript
app.disable("x-powered-by");
```
