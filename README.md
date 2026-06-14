# I ♥ Event Driven Architecture

**[i-love-event-driven-architecture](https://github.com/hideyuki-hori/i-love-event-driven-architecture)**

ユーザーにも負けず、トランザクションにも負けず  
CPU使用率にもディスクアクセス数にも負けぬ  
丈夫な基盤をもち  
欲に溺れ、決して妥協せず  
いつもカチキレながら  
1日に白米2合と肉、魚とすきな酒をのみ  
自分を限りなく愛し  
よく見聞きし分かり  
忘れてもなんとかなる仕組みを作り  
静かだが割と便利でPayPayが使えるくらいの程よい田舎に住み  
東に本社があればたまに出社し  
西にうまそうなうどんがあれば食いにいき  
南に生き返りそうな温泉があれば入りに行き  
北にダルそうな輩がいれば、目を合わさず空気と化し  
1人のときはゲームを楽しみ  
複数人のときは多少めんどくさがりながらも楽しみ  
みんなから愛され、褒められて、持ち上げられ  
いつも上機嫌でいられる  

そんな人間に私はなりたい  

## Done

- 2026-06-14 [🔮 Cassandra を理解する](https://zenn.dev/hideyuki_hori/articles/c51f9183cebf89)
- 2026-06-13 [🔌 Kafka Connect を理解する](https://zenn.dev/hideyuki_hori/articles/8d13751240091c)
- 2026-06-13 [🪲 Kafka を理解する](https://zenn.dev/hideyuki_hori/articles/8ce83fd931baa8)

> If you'd like to read these articles in English, try appending `?locale=en` to the article URL.
> If Zenn has finished its automatic translation, you'll be able to read them in English.

## In Progress

- debezium

## TODO

1. schema-registry-avro
1. kafka-streams
1. flink
1. Transactional Outbox - DB 更新とイベント発行を同一トランザクションに乗せる
1. 書き込みをイベント列として記録し、Kafka で流して、Streams / Flink で読み取りモデルを構築する
1. Saga - 分散トランザクションと補償処理
