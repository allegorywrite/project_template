### 目的
console.mdの目的を達成する

### 手順
console.mdを参照

### サーベイ規則
サーベイは `surveys/task_{i}/request.md`を作成してサーベイ要件をまとめる．
サーベイはdeep researchを使うため，自律的には行わずrequest.mdを作成した時点で停止しanswer.mdの作成を待つ．

### OCR規則
`utils/run_mistral_ocr.py`スクリプトを使ってOCR，その他の拡張子はpdf化してからOCRする．OCRしたtext等はcacheに保存する．
- pythonのパッケージ管理はvenv仮想環境を使用

### 資料及びコード作成規則
あなたは出力文字数が一定値を超えると途切れるようになっています．長い文章及びコードを出力する場合は，適宜区切り，write_in_fileではなくreplase_in_fileを用いてファイルを更新してください．