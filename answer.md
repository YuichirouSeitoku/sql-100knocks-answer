> S-001: レシート明細データ（receipt）から全項目の先頭10件を表示し、どのようなデータを保有しているか目視で確認せよ。

```
select * from receipt limit 10;
```

> S-002: レシート明細データ（receipt）から売上年月日（sales_ymd）、顧客ID（customer_id）、商品コード（product_cd）、売上金額（amount）の順に列を指定し、10件表示せよ。

```
select sales_ymd, customer_id, product_cd, amount from receipt limit 10;
```

> S-003: レシート明細データ（receipt）から売上年月日（sales_ymd）、顧客ID（customer_id）、商品コード（product_cd）、売上金額（amount）の順に列を指定し、10件表示せよ。ただし、sales_ymdsales_dateに項目名を変更しながら抽出すること。

```
select sales_ymd AS sales_date, customer_id, product_cd, amount from receipt limit 10;
```

> S-004: レシート明細データ（receipt）から売上日（sales_ymd）、顧客ID（customer_id）、商品コード（product_cd）、売上金額（amount）の順に列を指定し、以下の条件を満たすデータを抽出せよ。  
・ 顧客ID（customer_id）が"CS018205000001"

```
select sales_ymd, customer_id, product_cd, amount from receipt where customer_id='CS018205000001' limit 10;
```

> S-005: レシート明細データ（receipt）から売上日（sales_ymd）、顧客ID（customer_id）、商品コード（product_cd）、売上金額（amount）の順に列を指定し、以下の全ての条件を満たすデータを抽出せよ。  
・顧客ID（customer_id）が"CS018205000001"  
・売上金額（amount）が1,000以上

```
select sales_ymd, customer_id, product_cd, amount from receipt where customer_id='CS018205000001' and amount >= 1000;
```

> S-006: レシート明細データ（receipt）から売上日（sales_ymd）、顧客ID（customer_id）、商品コード（product_cd）、売上数量（quantity）、売上金額（amount）の順に列を指定し、以下の全ての条件を満たすデータを抽出せよ。  
・顧客ID（customer_id）が"CS018205000001"  
・売上金額（amount）が1,000以上または売上数量（quantity）が5以上

```
select sales_ymd, customer_id, product_cd, quantity, amount from receipt where customer_id='CS018205000001' and  (amount >= 1000 or quantity >=5);
```

> S-007: レシート明細データ（receipt）から売上日（sales_ymd）、顧客ID（customer_id）、商品コード（product_cd）、売上金額（amount）の順に列を指定し、以下の全ての条件を満たすデータを抽出せよ。  
・顧客ID（customer_id）が"CS018205000001"    
・売上金額（amount）が1,000以上2,000以下

```
select sales_ymd, customer_id, product_cd, amount from receipt where customer_id='CS018205000001' and amount between 1000 and 2000;
```

> S-008: レシート明細データ（receipt）から売上日（sales_ymd）、顧客ID（customer_id）、商品コード（product_cd）、売上金額（amount）の順に列を指定し、以下の全ての条件を満たすデータを抽出せよ。  
・顧客ID（customer_id）が"CS018205000001"  
・商品コード（product_cd）が"P071401019"以外

```
select sales_ymd, customer_id, product_cd, amount from receipt where customer_id='CS018205000001' and product_cd != 'P071401019';
```

> S-009: 以下の処理において、出力結果を変えずにORをANDに書き換えよ。  
SELECT * FROM store WHERE NOT (prefecture_cd = '13' OR floor_area > 900)

```
select * from store where (not prefecture_cd = '13') and (not floor_area > 900);
```

> S-010: 店舗データ（store）から、店舗コード（store_cd）が"S14"で始まるものだけ全項目抽出し、10件表示せよ。

```
select * from store where store_cd like 'S14%';
```

> S-011: 顧客データ（customer）から顧客ID（customer_id）の末尾が1のものだけ全項目抽出し、10件表示せよ。

```
select * from customer where customer_id '%1' limit 10;
```

> S-012: 店舗データ（store）から、住所 (address) に"横浜市"が含まれるものだけ全項目表示せよ。

```
select * from store where address like '%横浜市%';
```

> S-013: 顧客データ（customer）から、ステータスコード（status_cd）の先頭がアルファベットのA〜Fで始まるデータを全項目抽出し、10件表示せよ。

```
select * from customer where status_cd similar to '([A-F])%' limit 10;
```

> S-014: 顧客データ（customer）から、ステータスコード（status_cd）の末尾が数字の1〜9で終わるデータを全項目抽出し、10件表示せよ。

```
select * from customer where status_cd similar to '%([1-9])' limit 10;
```

> S-015: 顧客データ（customer）から、ステータスコード（status_cd）の先頭がアルファベットのA〜Fで始まり、末尾が数字の1〜9で終わるデータを全項目抽出し、10件表示せよ。

```
select * from customer where status_cd similar to '([A-F])%([1-9])' limit 10;
```