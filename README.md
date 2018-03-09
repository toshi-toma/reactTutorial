# Reactチュートリアル
Reactの公式チュートリアルの解説です。

# Step1 環境構築
ローカルの環境に、yarnまたはnpmが既にインストールされている状態からはじめます。  
コマンドはyarnの場合を記載しますので、npmを利用したい人は適宜変更してください。

***

package.jsonを作成
```
> yarn init --yes
```

package.jsonの内容を以下を参考に記入してください。
```json
{
  "name": "reactTutorial",
  "version": "1.0.0",
  "description": "React Tutorial",
  "author": "10shi10ma (https://github.com/10shi10ma)",
  "license": "MIT",
  "dependencies": {
    "react": "^16.2.0",
    "react-dom": "^16.2.0",
    "react-scripts": "^1.1.1"
  },
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build"
  }
}
```

***

必要に応じてgitignoreファイルを追加してください。[参考](https://github.com/10shi10ma/reactTutorial/commit/eae264af199130d13717e052a5aaceda1f8acb05)

***
package.jsonに書かれているパッケージをインストール
```
> yarn
```

これで環境構築は完了です。