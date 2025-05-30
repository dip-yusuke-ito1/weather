# Weather MCP Practice

このリポジトリは、[Model Context Protocol (MCP)](https://github.com/modelcontextprotocol) サーバーとして天気情報を取得できるサンプルです。  
**Cursor** 環境での利用を前提としています。

## 機能

- アメリカ国立気象局（NWS）のAPIを利用し、以下の情報を取得できます:
  - 指定した州の天気警報（アラート）
  - 指定した緯度・経度の天気予報

## セットアップ手順

1. **リポジトリをクローン**

   ```sh
   git clone <このリポジトリのURL>
   cd weather
   ```

2. **依存パッケージのインストール**

   ```sh
   npm install
   ```

3. **TypeScriptのビルド**

   ```sh
   npm run build
   ```

4. **MCPサーバーの起動**

    ##### Cursorでのmcp.json設定方法（cursorsetting）

    CursorでMCPサーバーを利用するには、プロジェクト直下に `mcp.json` を作成し、以下のように設定してください。

    ```json
    {
        "mcpServers": {
            "weather": {
                "command": "node",
                "args": [
                    "/ABSOLUTE/PATH/TO/PARENT/FOLDER/weather/build/index.js"
                ]
            }
        }
    }
    ```

    - `/ABSOLUTE/PATH/TO/PARENT/FOLDER/weather/build/index.js` の部分は、実際の絶対パスに書き換えてください。
    - 例: `/Users/yourname/practice/mcp-practice/weather/build/index.js`

   
   ##### Cursor上で「MCPサーバーとして起動」または、ターミナルで以下のコマンドを実行してください。

   ```sh
   npx weather
   ```

   または

   ```sh
   node build/index.js
   ```

   > ※ `npx weather` は `package.json` の `bin` 設定により利用できます。

## 使い方（Cursorでの例）

1. Cursorでこのリポジトリを開きます。
2. MCPサーバーを起動します（上記手順4）。
3. CursorのAIチャットで、以下のように天気情報を問い合わせます。

   - **天気警報の取得例:**
     ```
     テキサスの天気は？
     ```

   > ※ 米国内の緯度・経度のみ対応しています。

