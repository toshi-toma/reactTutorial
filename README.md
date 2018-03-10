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

# step3 BoardコンポーネントからSquareコンポーネントにデータを渡す
step2が完了した時点で、3つのReactのコンポーネントが定義された状態になっています。
- Square Component: 単一の```<button>```をレンダリングするコンポーネント
- Board Component: 9つの四角形をレンダリングするコンポーネント
- Game Component: 後で記入するプレースホルダをボードにレンダリングするコンポーネント

***

BoardコンポーネントからSquareコンポーネントへデータを渡します。  
renderSquareメソッド内を```<Square />;```から```<Square value={i}/>;```に書き換えてください。
```js
class Board extends React.Component {
  renderSquare(i) {
    return <Square value={i}/>;
  }
```

***

Squareコンポーネントのrenderメソッドで```{/* TODO */}```となっている箇所を```{this.props.value}```に書き換えてください。  
コンポーネント内では、```props```というオブジェクトを通して受け取ったデータへアクセスします。
```js
class Square extends React.Component {
  render() {
    return (
      <button className="square">
        {this.props.value}
      </button>
    );
  }
}
```

***

これで、各四角形の中に1~9の数字が表示されるようになりました。  

[step3での変更点](https://github.com/10shi10ma/reactTutorial/commit/e57c66009cf0e7ae4b5ebc7525489c233c242f74)

# Step4 Squareコンポーネントに状態を持たせる
Squareコンポーネントをクリックすると "X"が表示されるようにしましょう。  

***

Reactコンポーネントはコンストラクタ内でthis.stateを設定することでコンポーネントが状態(state)を持つことができます。正方形の現在の状態(state)を保存し、正方形がクリックされたときにそれを変更しましょう。

***

まず、Squareコンポーネントクラスにコンストラクタを追加してstateを初期化します。  
constructorの内容は以下のようにしてください。
```js
class Square extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      value: null,
    };
  }
```
これでSquareコンポーネントが状態(state)を持つことができるようになりました。

***

次に、Squareコンポーネントのrenderメソッドを書き換えます。  
これまでpropsを参照していたのを、stateを参照するようにします。  
```<button>```タグ内の```this.props.value```を```this.state.value```に変更してください。

***

あとは、Squareコンポーネントをクリックした時の動作を記述します。
renderメソッド内のbuttonタグを以下の内容に変更してください。
```js
<button className="square" onClick={() => this.setState({value: 'X'})}>
```
this.setStateが呼び出されると、渡されたstateでコンポーネントの状態が更新されて再レンダリングされます。

***

任意の正方形をクリックすると、その中にXが表示されるようになりました。

[step4での変更点](https://github.com/10shi10ma/reactTutorial/commit/971fd55d6c7c8c5315a89a2c64288c4336ac6f86)

