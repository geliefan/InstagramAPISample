# 教師用ガイドライン: Instagram APIを使用したユーザープロフィールの取得

## 目的
この演習では、Instagram APIを使用してユーザープロフィールを取得するPythonスクリプトを作成します。環境変数の読み込み、APIリクエストの送信、レスポンスの処理を学びます。

## 前提条件
- Pythonの基本的な知識
- `requests` ライブラリのインストール
- `python-dotenv` ライブラリのインストール

## スクリプトの構成

### 1. 環境変数の読み込み
まず、`.env` ファイルから環境変数を読み込みます。これにより、Instagramのアクセストークンを安全に管理できます。

```python
import requests
from dotenv import load_dotenv
import os

# 環境変数の読み込み
load_dotenv()
INSTAGRAM_ACCESS_TOKEN = os.getenv('INSTAGRAM_ACCESS_TOKEN')
```

### 2. ユーザープロフィールを取得する関数
次に、Instagram APIを使用してユーザープロフィールを取得する関数を定義します。

```python
def get_user_profile():
    # TODO: Instagram APIのURLを構築する
    # ヒント: f-stringを使用してINSTAGRAM_ACCESS_TOKENを読み出してURLを構築する
    # 例: url = f"https://graph.facebook.com/v18.0/me?fields=id%2Cname&access_token={INSTAGRAM_ACCESS_TOKEN}"
    url = f"https://graph.facebook.com/v18.0/me?fields=id%2Cname&access_token={}"

    # TODO: リクエストを送信し、レスポンスを取得する
    # ヒント: requests.get(url) を使用してリクエストを送信し、response変数に格納する
    # 例: response = requests.get(url)
    response = None

    # TODO: レスポンスが成功した場合はJSONデータを返す
    # ヒント: response.status_code が 200 の場合、response.json() を返す
    # 例: if response.status_code == 200: return response.json()
    if response:
        pass
    else:
        raise Exception("API request failed with status code " + str(response.status_code))
```

### 3. メイン関数
最後に、メイン関数を定義し、ユーザープロフィールを取得して表示します。

```python
def main():
    try:
        # TODO: get_user_profile関数を呼び出し、結果を表示する
        # ヒント: get_user_profile関数を呼び出し、その結果をprint関数で表示する
        # 例: profile = get_user_profile() print(profile)
        profile = None
        print(profile)
    except Exception as e:
        print("An error occurred:", e)

if __name__ == "__main__":
    main()
```

## 演習の手順

1. **URLの構築**:
   - `INSTAGRAM_ACCESS_TOKEN` を使ってURLを構築します。
   - 例: `url = f"https://graph.facebook.com/v18.0/me?fields=id%2Cname&access_token={INSTAGRAM_ACCESS_TOKEN}"`

2. **リクエストの送信**:
   - `requests.get(url)` を使ってリクエストを送信し、レスポンスを取得します。
   - 例: `response = requests.get(url)`

3. **レスポンスの処理**:
   - `response.status_code` を使ってステータスコードを確認し、成功した場合に `response.json()` を返します。
   - 例: `if response.status_code == 200: return response.json()`

4. **メイン関数の実行**:
   - `get_user_profile` 関数を呼び出し、その結果を `print` 関数で表示します。
   - 例: `profile = get_user_profile() print(profile)`

## 豆知識

### 環境変数の管理
環境変数を使用することで、APIキーやアクセストークンなどの機密情報をコード内に直接記述せずに管理できます。これにより、セキュリティが向上し、コードの再利用性も高まります。

### APIリクエストのエラーハンドリング
APIリクエストを行う際には、エラーハンドリングが重要です。ネットワークの問題やAPIの変更により、リクエストが失敗する可能性があります。適切なエラーハンドリングを行うことで、ユーザーに対して有用なエラーメッセージを提供し、問題の原因を特定しやすくなります。

### Pythonのf-string
Pythonのf-stringは、文字列の中に変数を埋め込むための便利な方法です。`f"Hello, {name}!"` のように使用することで、文字列のフォーマットが簡単になります。
