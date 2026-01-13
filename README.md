# I ♥ WebGPU

shardっていうブラウザで動くnode editorを作ってる。  
VJが使うようなアートツールをイメージしている。

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

