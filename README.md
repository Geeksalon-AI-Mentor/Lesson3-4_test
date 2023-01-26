# Lesson3-4確認問題
これは教材Lesson3-4の確認問題となっています。Flaskの基本的な使い方を問うような問題になっているので挑戦してみてください。
以下のような動作になっていれば問題ないです。

## ①`http://127.0.0.1:5000`にアクセス

![index htmlの画面](https://user-images.githubusercontent.com/86188830/214501768-1cae463f-c3bc-4472-9860-086e1277ddf1.png)

## ②`http://127.0.0.1:5000/data`にアクセス（手動で打ち込み）

![data htmlの画面](https://user-images.githubusercontent.com/86188830/214502027-e88f3f27-e27b-452b-b129-fff171efab71.png)

## ③`355`と入力し送信ボタンを押した後の画面

![送信ボタン押した後の画面](https://user-images.githubusercontent.com/86188830/214501958-40a8d2bb-8123-4080-98d3-1605cc39947e.png)

先ほど`10`と表示されていた部分が入力した値に代わっています。


## 問題の取り組み方
①このGitHubのファイルを`GeekSalon`フォルダにコピーする。

- コマンドプロンプトで`GeekSalon`フォルダに移動

- `git clone git@github.com:Geeksalon-AI-Mentor/Lesson3-4_test.git`を実行

②Lesson3-4_testフォルダをVScodeで開いて問題に取り組む

②コードの実行は**Lesson3-1**で作成した`flasktest`という仮想環境で実行して動作を確認する。

## 問題の見方
- 問の隣にあるファイル名は手を加えるファイル名を示しています。
    - （例）問①(app.py)であれば`app.py`にコーディングする。
- ヒントや解答は以下のようなプルダウン形式になっておりボタンを押すことで確認することができます。

<details>
<summary>解答</summary>
ここに回答が表示される。
</details>

<details>
<summary>ヒント</summary>
ここにヒントが表示される。
</details>


## 問題１：flaskを使う準備
### 問①(app.py)

flaskライブラリから`Flask`,`render_template`, `request`をインポートし、Flaskを使うためのおまじないを書いてappという変数に代入してください。

<details>
<summary>解答</summary>

```python

from flask import Flask, render_template, request
app = Flask(__main__)

```
</details>

## 問題２：ルーティング
### 問①(app.py)

`http://xxx/`にアクセスした時にindex.htmlを表示するコードを問題１のコードの後に書いてください。関数名（処理名）をindexとしてください。

<details>
<summary>解答</summary>

```python
@app.route('/')
def index():
    return render_template('index.html')
```

</details>

### 問②(app.py)

問題①のルーティングに`GET`と`POST`の両方に対応できるようにコードを書き加えてください。

<details>
<summary>解答</summary>

```python
@app.route('/',method=['GET','POST'])
def index():
    return render_template('index.html')
```

</details>

### 問③(app.py)

問題②のコードで`GET`の時のみ`index.html`が表示されるようにコードを書き換えてください。

<details>
<summary>解答</summary>

```python
@app.route('/',methods=['GET','POST'])
def index():
    if request.method == 'GET':
        return render_template('index.html')
```

</details>

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

<details>
<summary>解答</summary>

```python
@app.route('/',methods=['GET','POST'])
def index():
    if request.method == 'GET':
        n = 10
        return render_template('index.html',number = n)
```

</details>

### 問②(app.py)

`http://xxx/data`にGETしたときに`data.html`を表示するような処理を書いてください。関数名はdataとしてください。

<details>
<summary>解答</summary>

```python
@app.route('/data',methods=['GET','POST'])
def index():
    if request.method == 'GET':
        return render_template('data.html')
```

</details>


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

<details>
<summary>解答</summary>

```html
<form action='/data' method='POST'>
```

</details>

### 問④(app.py)

問②で書いたコードに以下の処理を書き加えてください。

`form`から送信（`POST`）された時、データをFlaskで受け取り`data`という変数に代入する。

受け取ったら`index.html`に値(`data`)を変数(`number`)渡して表示する。

<details>
<summary>ヒント</summary>

問題２の問③を参考にしてmethodとルーティング、render_template部分を変更してみよう！

テキストを受け取りたいときは`request.form[name属性]`で受け取れます！

</details>

<details>
<summary>解答</summary>


```python
@app.route('/data',methods=['GET','POST'])
def index():
    if request.method == 'GET':
        return render_template('data.html')
    else:
        data = request.form['data']
        return render_template('index.html', number = data)
```

</details>

