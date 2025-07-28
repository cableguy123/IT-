# Kotlin コーディング規約（関数名命名ルール）

## ディレクトリ別関数命名規則（MVVM + クリーンアーキテクチャ基準）

---

## `data/di`

- 依存性注入に使う関数は `provideXXX()` 形式で命名する。

```kotlin
@Provides
fun provideUserRepository(): UserRepository
```

---

## `data/entity`

- 通常は `data class` のみを定義し、関数定義は不要。
- 他レイヤーから変換関数を追加する場合は `toXXXEntity()` や `toDomain()` を使用。

```kotlin
fun User.toUserEntity(): UserEntity
fun UserEntity.toDomain(): User
```

---

## `data/impl`

- Repository の具体的な実装クラス。
- 外部とのやり取りに合わせて以下のような関数名を使用する。

| 処理内容       | 関数名例         |
|----------------|------------------|
| 取得（サーバー）| `fetchXXX()`     |
| 保存           | `saveXXX()` / `storeXXX()` |
| 削除           | `deleteXXX()`    |
| 検索           | `findXXX()` / `queryXXX()` |

```kotlin
override fun fetchUserList(): List<User>
override fun saveUser(user: User)
```

---

## `data/local`

- Room や DataStore などローカルデータの操作を担当。
- 一般的なDB操作に応じて以下のように命名。

| 処理内容 | 関数名例         |
|----------|------------------|
| 取得     | `getXXX()`       |
| 挿入     | `insertXXX()`    |
| 更新     | `updateXXX()`    |
| 削除     | `deleteXXX()`    |

```kotlin
suspend fun getAllSchedules(): List<ScheduleEntity>
suspend fun insertThread(thread: ThreadEntity)
```

---

## `domain/mapper`

- 各レイヤー間のデータ変換を担当。
- 命名は変換の方向性に基づいて `toXXX()` 形式とする。

```kotlin
fun ThreadEntity.toDomain(): Thread
fun Thread.toEntity(): ThreadEntity
```

---

## `domain/model`

- アプリ内部で使う純粋なデータ構造。
- 通常は `data class` のみを定義。
- ルールや検証ロジックが必要な場合は `isValid()` 等の関数名を使う。

```kotlin
data class Budget(val amount: Int) {
    fun isValid(): Boolean = amount >= 0
}
```

---

## `domain/repository`

- UseCase 層から利用される抽象的なデータ取得・保存用インターフェース。
- ビジネスに基づいたシンプルな関数名を使う。

```kotlin
suspend fun fetchUserProfile(): User
suspend fun saveThread(thread: Thread)
```

---

## `domain/usecase`

- 各クラスはひとつのユースケースを表す。
- クラス名は `Verb + Object + UseCase` 形式（例: `GetUserProfileUseCase`）
- `operator fun invoke()` を使って処理を記述。

```kotlin
class GetThreadListUseCase @Inject constructor(
    private val repository: ThreadRepository
) {
    suspend operator fun invoke(): List<Thread>
}
```

---

## 補足：共通関数命名ルール

| 処理目的         | 推奨関数名例       |
|------------------|--------------------|
| ViewModel 初期化 | `setupXXX()`       |
| データ取得       | `fetchXXX()` / `getXXX()` |
| データ保存       | `saveXXX()`        |
| 条件検索         | `findXXX()`        |
| 列挙型検索       | `fromRaw()` / `find()` |

```kotlin
fun setupObservers()
fun fetchUserProfile()
fun saveThread(thread: Thread)
fun findColor(raw: String): Color
```

---
