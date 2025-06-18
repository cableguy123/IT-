# 📘 Kotlin & Android 開発メモまとめ

---

## 🎨 themes.xml の構成理解

```xml
<style name="AppTheme" ...>   <!-- アプリ全体に適用されるスタイル -->
<style name="ActivityTheme" ...> <!-- 特定のアクティビティにのみ適用されるスタイル -->
```

✅ アプリ全体に適用：上側の `<style>`
✅ アクティビティ個別適用：下側の `<style>`
📌 ※TopBar がプレビューでは表示されたが、デバッグ実行時に表示されなかった問題は `AndroidManifest.xml` で解決済み

---

## 🏗️ <application> タグ vs <activity> タグ

```xml
<application>: アプリ全体の設定を定義
<activity>: 各画面（Activity）の設定を定義
```

---

## 🧩 Modifier とは？

> Composable に装飾や動作を追加するための "修飾子"

* UI を装飾するための Modifier
* 動作を追加するための Modifier（例: クリックなど）

---

## 🔄 StateFlow / Flow / LiveData

```kt
StateFlow:
- 観察可能な状態（value アクセス可）
- 状態ベース、初期値が必要
- UI が再描画される → 単発イベントには不向き

SharedFlow:
- 単発イベントの処理に適している
- UI の再描画は行わない
```

🧠 特定時点のデータ = `State`
📤 それを流す手段 = `StateFlow` / `SharedFlow`

---

## 🔽 DropDownItem の主なプロパティ

* `expanded`: ドロップダウンが展開されているかどうか
* `onDismissRequest`: 閉じる際に呼ばれるコールバック

---

## 🛠️ Kotlin のスコープ関数

`let`, `with`, `run`, `apply`, `also` → 可読性向上のために使用

---

## 🧷 @Binds と @Provides の違い

| 項目          | 説明                     |
| ----------- | ---------------------- |
| `@Binds`    | 実装クラスとインターフェースを結びつけるだけ |
| `@Provides` | 複雑なロジックを含む提供処理も可能      |

---

## 🧩 Entity vs Model

| 用途     | 層     | 説明                      |
| ------ | ----- | ----------------------- |
| Entity | データ層  | DB テーブルに対応するクラス         |
| Model  | ドメイン層 | ビジネスロジックや UI 状態を表現するクラス |

---

## ⚙️ AGP（Android Gradle Plugin）

* ビルド、テスト、配布プロセスを自動化するための Gradle プラグイン

---

## 🧱 App Build の流れ

```txt
.kt / .java / .xml → Gradle → DEX → AAB / APK
外部ライブラリ（.JAR / .AAR） → DEX に変換
```

| フォーマット | 説明                                      |
| ------ | --------------------------------------- |
| `.JAR` | 純粋な Java クラスファイル                        |
| `.AAR` | AndroidManifest.xml を含む Android 専用パッケージ |

---

## 🔧 kapt / ksp の違い

| ツール    | 説明                          |
| ------ | --------------------------- |
| `kapt` | Kotlin → Java → アノテーション処理   |
| `ksp`  | Kotlin 向け軽量アノテーションプロセッサ（高速） |

---

## 🧰 ビルド設定構成

```gradle
defaultConfig:
- アプリの基本設定（例: minSdkVersion など）

isMinifyEnabled:
- コードの難読化 / 縮小設定
- アプリサイズを削減しセキュリティを向上
```

```txt
Minify: 不要な空白・コメントの削除
Shrink: 未使用のクラスやメソッドの削除
```

---

## 🌊 Flow の概念

* 生産者（Repo） → Flow にデータを送信
* 消費者（UI） → Flow からデータを収集

```kt
lifecycleScope.launch {
    flow.collect { ... }
}
```

✅ 構成変更に強く、バックグラウンドでもリソースの無駄がない

📅 2025/06/19 (木)

* SELECT → UI に自動反映
* DELETE / UPDATE → UI 変化なし
* `suspend` とは併用不可（Flow 自体が非同期）

---

## 🧠 Kotlin キーワード

```kt
out: ジェネリクスの共変性（出力専用）を表すキーワード
R: Android リソースアクセス用自動生成クラス
```

---

## ⏱️ LocalDateTime vs Instant

| 項目     | LocalDateTime  | Instant     |
| ------ | -------------- | ----------- |
| タイムゾーン | ❌ なし（ローカル時間基準） | ✅ UTC 基準    |
| 用途     | 国内 / 地域向けサービス  | グローバルサービス向け |

---

## 🔗 onDelete オプション

1. `CASCADE` : 親が削除されると子も自動削除
2. `RESTRICT` : 子が存在する場合、親の削除を拒否
3. `SET NULL` : 親削除時、子の外部キーを NULL に
4. `NO ACTION` : 何もしない

---

📦 本ドキュメントは Kotlin & Android 開発者向けメモまとめ `.md` フォーマットです。
✍️ 作成者: IM
