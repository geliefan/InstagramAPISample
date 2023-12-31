# 詳細設計書 - Instagram APIサンプルプロジェクト

## 1. 概要
この詳細設計書は、Instagram APIサンプルプロジェクトの各コンポーネントの具体的な設計に関する詳細を提供します。

## 2. フロントエンド設計

### 2.1. ユーザーインターフェース
- HTMLとCSSを使用して、レスポンシブなデザインを実装。
- JavaScriptを使用して、動的なコンテンツの操作とAPI呼び出しを管理。

### 2.2. ページ構成
- ホームページ (`/`): 写真の取得とフォトブックの作成オプションを提供。

## 3. バックエンド設計

### 3.1. コントローラー
- Flaskを使用してルーティングとリクエストハンドリングを実装。
- 各エンドポイントは特定の機能（写真の取得、フォトブックの作成など）を担当。

#### 3.1.1. エンドポイント
- `/fetch_photos`: Instagramから写真を取得し、JSON形式で返す。
- `/fetch_hashtags`: 写真からハッシュタグを抽出し、出現回数と共に返す。
- `/search_by_hashtag`: 特定のハッシュタグを含む写真を検索し、写真のURLを返す。
- `/create_photobook`: 新しいフォトブックを作成し、成功メッセージを返す。
- `/get_photobooks`: 特定のユーザーのフォトブックのリストを返す。
- `/get_photobook_photos`: 特定のフォトブックの写真のURLを返す。
- `/get_image/<user_id>/<photobook_name>/<filename>`: 指定された画像ファイルを送信する。

### 3.2. ビジネスロジック
- 写真の取得、ハッシュタグの抽出、フォトブックの管理などの機能を実装。
- Instagram APIとの通信を管理。

## 4. データベース設計

### 4.1. テーブル設計
- `UserToken` テーブル: ユーザー認証情報を格納。
- `PhotoBook` テーブル: フォトブックの情報を格納。

### 4.2. クエリ設計
- ユーザーとフォトブックの関連付け。
- 効率的なデータ取得と更新のためのクエリ最適化。

## 5. API設計

### 5.1. エンドポイント
- 各機能に対応するエンドポイントを定義。

### 5.2. リクエストとレスポンス
- JSON形式でデータを送受信。
- エラーハンドリングと適切なステータスコードの返却。

## 6. セキュリティ対策

### 6.1. データ保護
- ユーザーのアクセストークンは暗号化してデータベースに保存。
- クロスサイトスクリプティング（XSS）やSQLインジェクション対策を実装。

### 6.2. システムセキュリティ
- セキュリティパッチの定期的な適用。
- 入力検証とエラーハンドリングを通じた堅牢なコードの実装。
