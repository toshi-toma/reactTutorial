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

# step2 チュートリアルの準備
Reactの公式チュートリアルでは、最低限のHTML、JS、CSSが提供された状態からスタートします。  
この準備では、チュートリアルを進めるのに最低限必要なReactのコンポーネントの表示までを行います。

***

プロジェクト直下にsrcディレクトリと、publicディレクトリを作成してください。
```
> mkdir src public
```

***

まず、必要最低限のHTMLファイルをpublicディレクトリに追加します。  
ファイル名はindex.htmlとしてください。  
ファイルの内容は[ここ](https://github.com/10shi10ma/reactTutorial/commit/ce666e4e8f33d8f25aa3db5fdb18ea49106792e5)を参照

***

次は、チュートリアルで利用する必要最低限のコンポーネントを定義したindex.jsファイルと、CSSファイルを追加します。  
ファイルの内容はindex.jsとindex.cssとしてください。  
ファイルの内容は[ここ](https://github.com/10shi10ma/reactTutorial/commit/78d9ac8d9b2fd018f720809b29d5bdf3d8bfb88e)を参照

***

これで最低限チュートリアルをスタートできる画面が作成できました。  
ブラウザで確認してみましょう。

```
> yarn start
```
[http://localhost:3000/](http://localhost:3000/)がブラウザで開かれて、3 * 3のテーブルが表示されていると思います。