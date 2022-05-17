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
