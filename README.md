# Svelte の動作を見てみるために動かしてみるリポジトリ

build すると、`.svelte-kit/output/prerendered/pages`に html ファイルが出力されるので、見てみる。

head タグ内に以下のように記述されている感じ

```html
...省略
<link href="./_app/immutable/assets/0.fa9427ff.css" rel="stylesheet" />
<link href="./_app/immutable/assets/2.57239003.css" rel="stylesheet" />
<link rel="modulepreload" href="./_app/immutable/entry/start.04797b35.js" />
<link
  rel="modulepreload"
  href="./_app/immutable/chunks/scheduler.cbf234a0.js"
/>
<link
  rel="modulepreload"
  href="./_app/immutable/chunks/singletons.a4db4bb8.js"
/>
<link rel="modulepreload" href="./_app/immutable/chunks/index.14349a18.js" />
<link rel="modulepreload" href="./_app/immutable/chunks/parse.bee59afc.js" />
<link rel="modulepreload" href="./_app/immutable/entry/app.8c1634e3.js" />
<link rel="modulepreload" href="./_app/immutable/chunks/index.200976ee.js" />
<link rel="modulepreload" href="./_app/immutable/nodes/0.f4793173.js" />
<link rel="modulepreload" href="./_app/immutable/chunks/stores.706754f8.js" />
<link rel="modulepreload" href="./_app/immutable/nodes/2.549c4b9e.js" />
...省略
```

結局のところ、受注や請負の場合は、出力側のファイルは納品形態に依存する。
クライアントが Ops 部分を担う場合は、HTML や CSS ファイルが可読である必要があるので、そのような場合は、レガシィなファイル構成で納品する必要がある。

ポイントは以下

- クライアントは HTML 以外のファイルを原則 Ops フェイズでは変更しない。（スタイルは style タグ、スクリプトは script タグでインラインで記述）
- Ops フェイズを RELEASE - Configure - Monitor - PLAN のサイクルと仮定した際に、first Release 以外は別案件扱い

という前提ならジャパニーズ請負でも利用可能？

アルゴリズミックとヒューリスティックをどこまで近づけられるかが肝かも、、
