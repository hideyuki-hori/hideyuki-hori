# I ♥ WebGPU

shardっていうブラウザで動くVJが使うようなアートツールを作ってる。
HoudiniやUnityのVFX Graphのようなものを考えている。

urlにアクセスしただけでアプリが立ち上がり、ローカルDBにユーザーデータを格納、必要があれば別のユーザーとサーバを介さずに(シグナリングは別として)やり取りできるものを作ってみたい。

進捗はここに書いてる。

- [GitHub Project](https://github.com/users/hideyuki-hori/projects/13/views/1)
- [Zenn](https://zenn.dev/hideyuki_hori)

以下の技術的な欲求を満たしたい。

- WebGPU
- ECS(Entity Component System)
- Effect.ts
  - ほんとはHaskellやF#がすきだが、Webアプリがすきだし関数型アプローチができるため
- CQRS
- Event Sourcing
- p2p
- DuckDB-WASM

低レイヤー操作に強い関心があり、Rustもすきなのでできればwasmをいれたいが、呼び出しコストが思ったよりおおきかったので様子見中。

2025-12-31時点のmock

<img width="1512" height="982" alt="shard mock screenshot" src="https://github.com/user-attachments/assets/2613da4f-398e-4d3d-9681-fe5852d21acc" />

# 今ハマってること

DuckDB-WASM + Effect で CQRS + EventSourcing + Streamを実現したい。
ユーザーデータはユーザーのpcで管理したい。
アプリを操作して出たeventはそのまま保存したい。
アプリで使用するデータはProjectionを通して使いたい。
Command実行後は成功のStreamで画面を更新したい。

ResultがほしかったからEffectに興味を持った。
触ってみるとStream合成が楽しく型もちゃんとしててよかった。

C#のMessagePipeにハマってたときDIがほしくなった。
というのもMessagingをするときLifetimeの管理が難しい。
Scopeが死ねば自動でCloseされる仕組みがたのしかった。
Service LocatorやSingletonのような簡易的なものも試したが、自分から取りに行く系の仕組みにすると依存関係が散らばりすぎてしんどくなる。

Stream処理がやりたいとDIが欲しくなり、DIを入れようとすると型システムが欲しくなる。パターンマッチングのためのTaggedErrorとかほしいよな。
またEffectはgeneratorで処理することもいい。
promiseでもええやんという考え方もあるが、eventのfork/race/merge/join/cancelがとにかく直感的にかけるのが嬉しい。
ということでそういうデータ構造とevent管理を試してる。

https://github.com/hideyuki-hori/lab-effect-duckdb-wasm-cqrs-es-stream

# これまで試したもの

## 1. RxJS + WebWorkerで負荷の高い処理をオフロードできないかについて

個人的にRxJSは多少クセはあれど非常にわかりやすいライブラリだと思うが、型の表現力が物足りなかった。
特にmergeしたstreamの型付けが難しい。
WebWorkerは夢があるので今後も触っていきたい。

- https://github.com/hideyuki-hori/distribution-worker
- https://zenn.dev/hideyuki_hori/articles/3823e2cf589fd1

- 動いてるサイト -> https://distribution-worker.every.fail/

## 2. Cloudflare Durable Objects + WebSocket

WebSocketが試したくて作った。
運用費がいきなりハネたりしないかビビってcf workerにはあげてない。

- https://github.com/hideyuki-hori/clayish/
- https://zenn.dev/hideyuki_hori/articles/c6aa9ae673e5c5

作ってる途中でやっぱりp2pがいいなぁ、中央集権な作りより分散がすきだなぁと思った。
分散は自由な感じがする。

## 3. WebGL -> WebGPU

JSXがすきなので、three.jsをReactで操作できるものを試してみた。

- https://github.com/hideyuki-hori/love-poimandres
- https://zenn.dev/hideyuki_hori/articles/6d3f710b794154
- 動いてるサイト -> https://love-poimandres.every.fail/

poimandresのライブラリはとても便利だなと思うが、おしゃれなサイトでよく出てくる感じになるなと思った。
カタログから選んでる感じが苦手。
自分がライブラリに求めてるのは関数群であって、積極的に副作用を起こすものは苦手かもしれない。
Three.js自体がかなりリッチなライブラリなので、poimandresの問題ではないがそう思った。
poimandresはおしゃれだし、Post Processingのコードは特に勉強になった。
この手のライブラリは使うのではなくリファレンスとして付き合いたい。

WebGLは構文がしんどく、WebGPUに興味が移ったがWebGPUもそんなに楽じゃない。
ただRustに似た文法で洗練されていて書いていて気持ちいい。
TypeGPUにちょっとだけ興味が移ったが、今は生のWebGPUがすき。


