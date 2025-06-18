# 📘 iOS開発メモ帳（Swift中心）

---

## 🧱 フレームワークとライブラリの違い

```
フレームワーク：アプリ開発の基盤（例：SwiftUI, UIKit, Flutter, React Native）
ライブラリ：特定の機能に特化したコード集（例：Alamofire, Axios）
```

---

## 🌱 SwiftUI vs UIKit

| 観点     | SwiftUI       | UIKit          |
| ------ | ------------- | -------------- |
| パラダイム  | 宣言型           | 命令型            |
| UI構築方法 | 少ないコードで直感的に記述 | Viewを生成して手動で制御 |
| 利点     | シンプル、再利用性高    | 柔軟、細かい制御が可能    |

### 🔍 宣言型 vs 命令型

* 宣言型："何をしたいか" を記述（SwiftUI）
* 命令型："どうするか" を順番に記述（UIKit）

---

## 🧭 MVVMアーキテクチャ

```
Model: データ管理 / DB・API・ビジネスロジック担当
ViewModel: ModelとViewの橋渡し（UI用に整形）
View: ユーザーに表示されるUI部分、ViewModelを監視
```

✅ ViewModel → View へ状態通知（＝データバインディング）
✅ ViewModelは再利用性◎ / テストしやすい

---

## 👀 Observerパターン

* Publisher（発行者）と Observer（購読者）の関係を構築
* 状態変化が起きたら自動で通知
* **疎結合**を実現し、OCP原則を守れる

---

## ⚠️ Never型とは？

* 戻り値が "絶対に返らない" 関数に使われる型（例：`fatalError()`）
* Swiftでは `enum Never {}` で定義され、インスタンス化不可

---

## 🍎 Combine（リアクティブフレームワーク）

* 非同期イベントを処理するためのApple公式フレームワーク
* `Publisher` が値を発行 → `Subscriber` が受信

### sinkの役割

```
Publisher からのデータを受信し、処理するクロージャ
→ 値処理 + エラー処理両対応
```

### Subject（PassthroughSubject / CurrentValueSubject）

* 外部から `send(_:)` で値を注入できる特殊な Publisher

### AnyCancellable

* サブスクリプションを保持・解放するための型（ARC管理）

---

## 🌐 WebViewの種類

| タイプ                  | 特徴                    |
| -------------------- | --------------------- |
| SafariViewController | 外部ブラウザ呼び出し、安全 & ATS不要 |
| UIWebView            | 非推奨、古いAPI             |
| WKWebView            | 高性能で現代的なWeb表示用View    |

---

## 🛠️ XcodeGenとは？

* `.yml` or `.json` から `.xcodeproj` を自動生成するCLIツール
* プロジェクト構造の共有・管理がしやすく、CI/CDとの相性も良

---

## 🚦 Swift Concurrency（非同期処理）

```
async / await：非同期処理をシンプルに
Task：非同期コンテキストの生成
TaskGroup：複数非同期タスクを並列実行＆集約
Task.detached：親と独立した非同期タスク
```

---

## ⚙️ GCD（Grand Central Dispatch）

* Swift Concurrency前の非同期API
* FIFOの `DispatchQueue` を通じてスレッド管理

| Queueの種類         | 特徴              |
| ---------------- | --------------- |
| Serial Queue     | 1つずつ順番に処理（同期向き） |
| Concurrent Queue | 複数同時実行（並列処理向き）  |

✅ `DispatchQueue.main` はUI更新に使用（Main Thread）

---

## 🧼 クリーンアーキテクチャとは？

```
「設計図」のようなもので、責務を分離し、保守性・テスト性を高めた構造
```

### 各層の責務

* **Presentation層**: UIイベントを受けてDomainへ渡す
* **Domain層**: ビジネスロジックを実行（フレームワーク依存なし）
* **Persistence層**: DB、API、外部連携を担当

特徴：

* テストしやすい
* 拡張性が高い
* 各層が疎結合

---

## ⚡ RxSwift 基礎

* 非同期＆イベント駆動型の反応的プログラミング（FRP）

| 用語         | 説明                     |
| ---------- | ---------------------- |
| Observable | イベントを発行するストリーム         |
| Observer   | イベントを購読し、反応する側         |
| Subscribe  | 購読処理、`onNext`などでイベント処理 |
| Subject    | 発行と購読を兼ねるストリーム         |
| Scheduler  | 実行コンテキスト（メインスレッドなど）指定用 |

---

## 📦 CocoaPodsとは？

* iOS用パッケージマネージャー（内部でRubyが使われている）
* `gem install cocoapods` で導入可能

---

## 🔐 Provisioning Profile

```
アプリを特定のデバイスでテスト / リリースするために必要な証明書
```

構成：

* App ID（Bundle ID）
* Development Certificate（開発者署名）
* デバイス UUID

---

## 🔁 エンコーディングとデコーディング

* Encoding：オブジェクト → JSONなどへ変換
* Decoding：JSONなど → オブジェクトへ変換

---

## 💾 データセグメントの分類（iOSメモリ）

| セグメント        | 内容                   |
| ------------ | -------------------- |
| Text Segment | 実行コード（読み取り専用）        |
| Data Segment | static変数や初期化済みデータ    |
| Stack        | 一時的なローカル変数・関数の引数など   |
| Heap         | 動的に確保されたメモリ領域（クラスなど） |

---

📒 このドキュメントは Swift / iOS 開発者向けの知識メモ帳です。
✍️ 作成者: IM
