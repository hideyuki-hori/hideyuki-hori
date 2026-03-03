<div align="center">同じ川に二度入ることはできない</div>
<br/>
<br/>
<br/>
ヘラクレイトスの言葉がすきだ。
<br/>
常に流れる川の水に足を踏み入れると、そのたびに異なる水に入れ替わっている。同時に入る側の人間も常に変化している。
<br/>
同じ状態は二度と訪れないという意味。
<br/>
プログラミングでも状態ではなく、出来事が積み重なっていくことにロマンを感じる。

Streamはそれをコードで表現する手段で、何を作ってもStreamが最上級の解決策に思えてくる。

フロント(WebGPU)を書いてるとバックエンドがやりたくなり、バックエンドを書いてるとフロントがやりたくなる。
どちらか片方では満足できないので、2つのプロジェクトに分けてプログラミング欲を解決してる。

## [shard](https://github.com/hideyuki-hori/shard)

ブラウザで動くVJアートツール。HoudiniやUnityのVFX Graphのようなノードベースエディタ。
WebGPU + ECS + Effect.ts + DuckDB-WASM。
urlにアクセスしただけで立ち上がり、ローカルにデータを持ち、p2pでつながる。

## [cadaver](https://github.com/hideyuki-hori/cadaver)

クロスボーダー送金におけるカオスエンジニアリング。
Rust + KurrentDB + PostgreSQL。
分散システム上のStream処理が障害下でどう振る舞うかを検証してる。
