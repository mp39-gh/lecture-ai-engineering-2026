# 第2回 解答

## 演習

- 使ったモデル・設定（`result.json` の `config` から）：
{
    "base_model": "Qwen/Qwen3.5-0.8B",
    "revision": "2fc06364715b967f1860aea9cf38778875588b17",
    "seed": 42,
    "num_train_epochs": 20,
    "warmup_steps": 6,
    "lr": 0.0002,
    "lora_r": 16,
    "lora_alpha": 32,
    "max_seq_len": 512,
    "max_new_tokens": 96,
    "gen": {
      "do_sample": false
    }
  }
  
- 自分で学習を実行したか（`executed_training_myself`）：●はい / いいえ（実行できた範囲：　）
- 学習前：`format_rate` =　 / `content_rate` =　format_rate = 9.5% / content_rate = 0%
- 学習後：`format_rate` =　 / `content_rate` =　format_rate = 100% / content_rate = 90.5%
- 退行した質問：なし
- 学習後に残った失敗と、その型（根拠なしの質問に断定した / 根拠ありの質問に確認要求で逃げた / 形式の崩れ）：
「成績はいつ出ますか」：根拠のない情報を断定
「オフィスアワーは事前予約が必要ですか」：関連情報を出力

- 知識を問う質問（セクション 6）の結果（学習前の分類 → 学習後の分類）と気づいたこと：
「この講座の最終課題の締切はいつですか」：format_error が asserted へ変化
「担当教員の名前は何ですか」：format_error が needs_review へ変化
「次回の講義のテーマは何ですか」：format_error が needs_review へ変化
「課題の提出期限はいつですか」：format_error が asserted へ変化

- 学習で変わったこと・変わらなかったこと：
学習前後でJSON形式の出力ができるようになり、形式遵守率が100%になった。
正解率も0%から90.5%になった。。

## 宿題

- 取り組んだレベル：基礎 / 実装 / 発展　⇒基礎
- 変えた設定やデータ：num_train_epochs を「20」から「10」へ変更
- 
- 結果（比較表や数字）：
評価項目	　　　　　変更前（20エポック）	変更後（10エポック）
format_rate	　　　100%　　　　　　　　100%
content_rate	　　90.50%　　　　　　　81.00%
Training Loss　　 0.014091　　　　　　0.101058
学習時間　　　　　 226秒　　　　　　　　110秒

- ファインチューニングが向く場面・向かない場面についての考察：
回答や出力形式などを習得させたい場面に向いている。
