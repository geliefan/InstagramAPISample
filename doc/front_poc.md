# 教師用ガイドライン: Instagramの写真を取得する関数

## 学習目標
この課題を通じて、生徒に以下の要点を学んでほしいと考えています。
1. JavaScriptを使用したDOM操作の基本
2. APIリクエストの送信とレスポンスの処理
3. エラーハンドリングの重要性
4. 条件分岐を使用した入力検証

## スクリプトの構成

### 1. アクセストークンとユーザーIDの取得
まず、HTMLの入力フィールドからアクセストークンとユーザーIDを取得します。

```javascript
// Instagramの写真を取得する関数
function fetchInstagramPhotos() {
    // アクセストークンを取得
    const ACCESS_TOKEN = document.getElementById("token").value;
    // ユーザーIDを取得
    const USER_ID = document.getElementById("userId").value;
```

### 2. 入力検証
次に、アクセストークンまたはユーザーIDが入力されていない場合に警告を表示します。

```javascript
    // TODO: アクセストークンまたはユーザーIDがない場合は警告を表示するコードを書く
    // ヒント: if文を使用して、ACCESS_TOKEN または USER_ID が空かどうかをチェックし、
    // 空の場合は alert 関数で警告メッセージを表示する
```

### 3. APIエンドポイントの構築
Instagram APIのエンドポイントURLを構築します。

```javascript
    // Instagram APIのエンドポイントURLを構築
    const endpoint = `https://graph.facebook.com/v18.0/${USER_ID}/media?fields=id,caption,media_type,media_url&access_token=${ACCESS_TOKEN}`;
```

### 4. APIリクエストの送信
APIにリクエストを送信し、レスポンスを処理します。

```javascript
    // APIにリクエストを送信
    fetch(endpoint)
        .then(response => response.json())
        .then(data => {
            // TODO: 写真を表示するための displayPhotos 関数を呼び出すコードを書く
            // ヒント: displayPhotos 関数に data.data を引数として渡す
        })
        .catch(error => {
            console.error('Error fetching Instagram photos:', error);
            alert("An error occurred. Please check the console for more details.");
        });
}
```

## 演習の手順

1. **アクセストークンとユーザーIDの取得**:
   - HTMLの入力フィールドからアクセストークンとユーザーIDを取得します。
   - 例: 

const ACCESS_TOKEN = document.getElementById("token").value;



2. **入力検証**:
   - アクセストークンまたはユーザーIDが空の場合に警告を表示します。
   - 例: `if (!ACCESS_TOKEN || !USER_ID) { alert("アクセストークンとユーザーIDを入力してください。"); return; }`

3. **APIエンドポイントの構築**:
   - Instagram APIのエンドポイントURLを構築します。
   - 例: 

const endpoint = 

https://graph.facebook.com/v18.0/${USER_ID}/media?fields=id,caption,media_type,media_url&access_token=${ACCESS_TOKEN}`;`

4. **APIリクエストの送信**:
   - 

fetch

 を使用してAPIにリクエストを送信し、レスポンスを処理します。
   - 例: 

fetch(endpoint).then(response => response.json()).then(data => { /* 処理 */ }).catch(error => { /* エラーハンドリング */ });



## 豆知識

### DOM操作
JavaScriptを使用してHTML要素を操作する方法を学びます。

document.getElementById

 を使用して特定の要素を取得し、その値を読み取ることができます。

### APIリクエスト


fetch

 関数を使用してAPIリクエストを送信し、レスポンスを処理する方法を学びます。

fetch

 はPromiseを返すため、

then

 と 

catch

 を使用して非同期処理を行います。

### エラーハンドリング
APIリクエストが失敗した場合にエラーメッセージを表示する方法を学びます。

console.error

 を使用してエラーをコンソールに出力し、

alert

 を使用してユーザーに通知します。

### 条件分岐
`if` 文を使用して条件分岐を行い、特定の条件が満たされた場合に特定の処理を実行する方法を学びます。

## コラム: APIの利用とセキュリティ
APIを利用する際には、アクセストークンなどの機密情報を適切に管理することが重要です。アクセストークンを直接コードに埋め込むのではなく、環境変数やセキュアなストレージを使用して管理することを推奨します。また、APIリクエストを行う際には、HTTPSを使用して通信を暗号化し、データの盗聴や改ざんを防止します。
