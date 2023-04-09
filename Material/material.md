# Material

## マテリアルとは

物体の質感設定のこと

3Dの形状を作る際に見栄えを決める「マテリアル」を指定することで、着色や画像・陰影の割り当て、ライティングの反射などを適用可能

## 代表的なマテリアル
- 単色塗りのマテリアル
- 画像を使ったマテリアル
どちらも`THREE.MeshStandardMaterial`クラスを使用する。コンストラクタの引数に色か画像テクスチャを指定するかで自動的に適したマテリアルになる


## red_sphere

```js
// create a sphere
const geometry = new THREE.SphereGeometry(300, 30, 30);
const material = new THREE.MeshStandardMaterial({ color: 0xFF0000 });
// create a mesh
const mesh = new THREE.Mesh(geometry, material);
scene.add(mesh);

```

### ライティングについて
```js
// directional light
const directionalLight = new THREE.DirectionalLight(0xFFFFFF);
directionalLight.position.set(1, 1, 1);

scene.add(directionalLight);

```
- `THREE.DirectionalLight`クラス
- `THREE.AnmbientLight`クラス

## 画像をマテリアルに使用する方法
画像はGPUの制約から、2の累乗の高さ・幅である画像のみが利用することが可能