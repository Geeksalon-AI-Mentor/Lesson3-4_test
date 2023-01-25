# Lesson3-4確認問題

## 問題１：flaskを使う準備
### 問①(app.py)

flaskライブラリからFlask,render_template, requestをインポートし、Flaskを使うためのおまじないを書いてappという変数に代入してください。

## 問題２：ルーティング
### 問①(app.py)

`http://xxx/`にアクセスした時にindex.htmlを表示するコードを書いてください。関数名（処理名）をindexとしてください。

### 問②(app.py)

問題①のルーティングにGETとPOSTの両方に対応できるようにコードを書き加えてください。

### 問③(app.py)

問題②のコードで`GET`の時のみ`index.html`が表示されるようにコードを書き換えてください。

## 問題３：FlaskとHTMLのやりとり
`index.html`は以下のようなコードになっています。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h1>Hello World</h1>
    {{ number }}
</body>
</html>
```

### 問①(app.py)

問題２の問③のコードを変数`n`に10を代入して、`index.html`の`number`に変数`n`を渡すように書き換えてください。

### 問②(app.py)

`http://xxx/data`にGETしたときに`data.html`を表示するような処理を書いてください。関数名はdataとしてください。

`data.html`は以下のようなコードになっています。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <form ~~~~~~~>
        <input type="text" name="data">
        <input type="submit">
    </form>    
</body>
</html>
```

### 問③(data.html)

inputで入力された値を`http://xxx/data`に`post`で送信するようにformの空白部分(~)を埋めてください。

### 問④(app.py)

問②で書いたコードに以下の処理を書き加えてください。

`form`から送信（`POST`）された時、データをFlaskで受け取り`data`という変数に代入する。

受け取ったら`index.html`に値(`data`)を変数(`number`)渡して表示する。

<details>
<summary>ヒント</summary>

問題２の問③を参考にしてmethodとルーティング、render_template部分を変更してみよう！

テキストを受け取りたいときは`request.form[name属性]`で受け取れます！

</details>


