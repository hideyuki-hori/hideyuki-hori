# I ♥ Stream based architecture

<center>同じ川に二度入ることはできない</center>

ヘラクレイトスの言葉がすきだ。
川の水は常に流れ、足を踏み入れるたびに異なる水に入れ替わっており、同時に、入る側の人間も常に変化しているため、同じ状態は二度と訪れないという意味。
プログラミングでも状態ではなく、出来事が積み重なっていくことにロマンを感じる。

Streamはそれをコードで表現する手段で、何を作ってもStreamが最上級の解決策に思えてくる。

フロント(WebGPU)を書いてるとバックエンドがやりたくなり、バックエンドを書いてるとフロントがやりたくなる。
どちらか片方では満足できないので、2つのプロジェクトに分けている。

## [shard](https://github.com/hideyuki-hori/shard)

ブラウザで動くVJアートツール。HoudiniやUnityのVFX Graphのようなノードベースエディタ。
WebGPU + ECS + Effect.ts + DuckDB-WASM。
urlにアクセスしただけで立ち上がり、ローカルにデータを持ち、p2pでつながる。

## [cadaver](https://github.com/hideyuki-hori/cadaver)

クロスボーダー送金におけるカオスエンジニアリング。
Rust + KurrentDB + PostgreSQL。
分散システム上のStream処理が障害下でどう振る舞うかを検証してる。
