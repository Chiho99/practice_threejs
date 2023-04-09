# Introduction

## canvas要素を用意

```js
<body>
  <canvas id="myCanvas"></canvas>
</body>
```

## JSライブラリを読み込む

```js
// CDN
<script src="https://unpkg.com/three@0.147.0/build/three.min.js"></script>
```

```js
// DOMContentLoadedイベント発生を監視、ページ読み込み終了時に実行させたい関数を指定
<script>
window.addEventListener('DOMContentLoaded', init);
function init(){
  // 処理
}
</script>
```

## 3D表示ようのJavaScriptを用意

```js
const renderer = new THREE.WebGLRenderer({
    canvas: document.querySelector('#myCanvas');
});
```

## シーンを作成

```js
const scene = new THREE.Scene();
```

## カメラを作る

`THREE.PerspectiveCamera`クラスのコンストラクターで画角、アスペクト比、描画開始距離、描画終了の4つの情報を引数として渡す

```js
const camera = new THREE.PerspectiveCamera(45, 960/540);
```

## 立方体を作る

立方体はメッシュという表示オブジェクトを使用して作成する
メッシュを作るには、**ジオメトリ(形状)** と **マテリアル(素材)** の二種類を用意

ジオメトリは頂点情報や面情報を持っている

```js
const geometry = new THREE.BoxGeometry(500, 500, 500);
```

## アニメーション

`requestAnimationFrame()`は引数として渡された関数を、毎フレーム実行する

```js
// 初回実行
tick();

function tick() {
    requestAnimationFrame(tick);
    // アニメーション処理をここに書く

    renderer.render(scene, camera)
}
```

## Three.jsの基本構造

### THREE.Sceneクラス(3D空間を表すクラス)

3Dオブジェクトはシーンに`add()`メソッドを利用して追加することで表示可能

### THREE.PerspectiveCameraクラス(3D空間を撮影するカメラクラス)

視点を制御するために使用する

3D空間のどの視点で撮影しているのかの情報が必要となる

### THREE.WebGLRendererクラス(3D空間のレンダリングを行うクラス)

内部的にはThree.jsがWebGLのAPIを使用して、GPUで座標を計算させ画面に表示させている。