# ICP Sample Canister Deployment 🚀

このプロジェクトは、Internet Computer Protocol (ICP) 上にデプロイしたシンプルなスマートコントラクトです。  
Rust を使用して `greet` 関数を実装し、名前を入力すると `"Hello, [name]!"` を返します。  
フロントエンドはシンプルなウェブインターフェースを提供し、ユーザーが直接 `greet` 関数を呼び出せるようになっています。

---

## 🔧 デプロイ方法
このプロジェクトをローカルまたは本番環境にデプロイする手順です。

### **1️⃣ ICP SDK のインストール**
まず、ICP の開発環境をセットアップします。
```sh
sh -ci "$(curl -fsSL https://internetcomputer.org/install.sh)"
```

### **2️⃣ リポジトリのクローン**
```sh
git clone https://github.com/Krminfinity/icp-sample.git
cd icp-sample
```

### **3️⃣ ローカル環境でのデプロイ**
以下のコマンドを実行すると、ローカル環境でキャニスターをデプロイできます。
```sh
dfx start --background
dfx deploy
```

### **4️⃣ 本番環境（ICPネットワーク）へのデプロイ（任意）**
本番環境にデプロイする場合は、以下を実行：
```sh
dfx deploy --network ic
```
※ 本番環境デプロイには **Cycle（手数料）** が必要です。

---

## 🔍 動作確認ガイド
デプロイが完了したら、以下の方法でスマートコントラクトをテストできます。

### ✅ **1. フロントエンドの確認**
ブラウザで以下のURLを開く：
```
http://bd3sg-teaaa-aaaaa-qaaba-cai.localhost:4943/
```
DAppが表示され、ユーザーが `greet` 関数を直接呼び出せることを確認してください。

---

### ✅ **2. バックエンド（スマートコントラクト）の確認**
Candid UI を開いて `greet` 関数を実行：
```
http://127.0.0.1:4943/?canisterId=bkyz2-fmaaa-aaaaa-qaaaq-cai
```
または、ターミナルで直接呼び出す：
```sh
dfx canister call hello_backend greet "Alice"
```
**期待される出力**
```sh
("Hello, Alice!")
```

---

## 📌 キャニスターのコード
Rust で実装された `greet` 関数（`src/hello_backend/src/lib.rs`）のコードは以下の通りです。

```rust
#[ic_cdk::query]
fn greet(name: String) -> String {
    format!("Hello, {}!", name)
}
```

---

## 📎 キャニスター情報
- **Backend Canister ID:** `bkyz2-fmaaa-aaaaa-qaaaq-cai`
- **Frontend Canister ID:** `bd3sg-teaaa-aaaaa-qaaba-cai`


