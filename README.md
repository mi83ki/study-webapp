# study-webapp
Node.js+Express+MySQLで作る安全なWebアプリケーションの勉強

# やったこと
## package.jsonの作成
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

## .gitignoreの作成
1. 「.gitignore」ファイルを新規作成する
1. 以下のサイトにアクセスする
    https://www.toptal.com/developers/gitignore
1. NodeとVisualStudioCodeを選択して作成ボタンを押下する
1. 作成された文字列を.gitignoreファイルにコピペする

## デバッグの設定
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