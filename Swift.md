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

# Composable 재사용 Recycle에 대해서 

- UI를 함수로 분리함 
- 다른화면이나 다른 컴포넌트에서 그걸 호출해서 
- 같은 UI를 다시쓴다라고 이해하면 될듯? 
- 즉 , 재사용을 한다는거다 

--- 

# collectAsStateWithLifecycle

- 주로 View <-> ViewModel을 이어준다는 인식으로 받았지만 이건 진짜 뭐지?
- 
📒 このドキュメントは Swift / iOS 開発者向けの知識メモ帳です。
✍️ 作成者: IM


```Kotlin
package jp.co.we.travelbuddy.presentation.view.signup

import android.annotation.SuppressLint
import android.widget.Space
import androidx.compose.foundation.Image
import androidx.compose.foundation.layout.*
import androidx.compose.foundation.rememberScrollState
import androidx.compose.foundation.shape.RoundedCornerShape
import androidx.compose.foundation.verticalScroll
import androidx.compose.material3.*
import androidx.compose.runtime.*
import androidx.compose.ui.Modifier
import androidx.compose.ui.graphics.Color
import androidx.compose.ui.res.painterResource
import androidx.compose.ui.res.stringResource
import androidx.compose.ui.text.TextStyle
import androidx.compose.ui.text.font.FontWeight
import androidx.compose.ui.tooling.preview.Preview
import androidx.compose.ui.unit.dp
import androidx.compose.ui.unit.sp
import androidx.hilt.navigation.compose.hiltViewModel

import androidx.lifecycle.compose.collectAsStateWithLifecycle
import jp.co.we.travelbuddy.R
import jp.co.we.travelbuddy.presentation.theme.signUpButtonColor
import jp.co.we.travelbuddy.presentation.theme.signUpButtonTextColor
import jp.co.we.travelbuddy.presentation.viewmodel.SignUpViewModel

/**
 * 会員登録
 * 機能
 */
@OptIn(ExperimentalMaterial3Api::class)
@Composable
fun SignUpWidget(
    navigationToLibraryView: () -> Unit,
    modifier: Modifier = Modifier,
    viewModel: SignUpViewModel = hiltViewModel()
) {
    // メールアドレス
    val emailLabelText = stringResource(R.string.signup_email)
    // パスワード
    val passwordLabelText = stringResource(R.string.signup_password)
    // ユーザーネーム
    val nameLabelText = stringResource(R.string.signup_nickname_form)
    // ユーザーメール入力フォーム
    val emailFormText = stringResource(R.string.signup_email_form)
    // ユーザーパスワード入力フォーム
    val passwordFormText = stringResource(R.string.signup_password_form)
    // ユーザーネーム入力フォーム
    val nameFormText = stringResource(R.string.signup_nickname_form)
    // 会員登録ボタン
    val signUpBtn = stringResource(R.string.signup_button)
    // メール値
    val email by viewModel.email.collectAsStateWithLifecycle()
    // パスワード値
    val password by viewModel.password.collectAsStateWithLifecycle()
    // ネーム値
    val name by viewModel.name.collectAsStateWithLifecycle()
    // 登録結果
    val result by viewModel.result.collectAsStateWithLifecycle()
    // 結果メッセージ
    val snackbarHostState = remember { SnackbarHostState() }
    // CoroutineScope
    val coroutineScope = rememberCoroutineScope()
    Scaffold(
        topBar = {
            SignUpTopAppBar(modifier = modifier)
        }
    ) {
        innerPadding ->
        Column(
            modifier = modifier
                .fillMaxWidth()
                .padding(innerPadding)
        ) {
            Spacer(modifier = modifier.height(16.dp))
            Text(
                text = emailLabelText,
                modifier = Modifier.padding(start = 20.dp, bottom = 10.dp),
                style = MaterialTheme.typography.labelMedium,
                color = Color.Gray
            )
            OutlinedTextField(
                value = email,
                onValueChange = { viewModel.onEmailChanged(it) },
                label = { emailFormText },
                modifier = Modifier
                    .fillMaxWidth()
                    .padding(horizontal = 20.dp, vertical = 8.dp),
                shape = RoundedCornerShape(10.dp)
            )
            Text(
                text = passwordLabelText,
                modifier = Modifier.padding(start = 20.dp, bottom = 4.dp),
                style = MaterialTheme.typography.labelMedium,
                color = Color.Gray
            )
            OutlinedTextField(
                value = password,
                onValueChange = { viewModel.onPasswordChange(it) },
                label = { passwordFormText },
                modifier = Modifier
                    .fillMaxWidth()
                    .padding(horizontal = 20.dp, vertical = 8.dp),
                shape = RoundedCornerShape(10.dp)
            )
            Text(
                text = nameLabelText,
                modifier = Modifier.padding(start = 20.dp, bottom = 4.dp),
                style = MaterialTheme.typography.labelMedium,
                color = Color.Gray
            )
            OutlinedTextField(
                value = name,
                onValueChange = { viewModel.onNameChange(it) },
                label = { nameFormText },
                modifier = Modifier
                    .fillMaxWidth()
                    .padding(horizontal = 20.dp, vertical = 8.dp),
                shape = RoundedCornerShape(10.dp)
            )

            Button(
                onClick = { viewModel.signUp() },
                modifier = Modifier
                    .fillMaxWidth()
                    .padding(20.dp),
                shape = RoundedCornerShape(12.dp),
                colors = ButtonDefaults.buttonColors(containerColor = Color(0xFFC6A457))
            ) {
                Text(text = signUpBtn, color = Color.White)
            }

            Spacer(modifier = Modifier.height(32.dp))

            LoginButtonByGoogle()
        }
    }
}

@Composable
fun SignUpForm(
    email: String,
    password: String,
    name: String,
    onEmailChange: (String) -> Unit,
    onPasswordChange: (String) -> Unit,
    onNameChange: (String) -> Unit,
    modifier: Modifier = Modifier
) {
    Column(
        modifier = modifier
            .fillMaxWidth()
    ) {  }
}


/**
 * 会員登録
 */
@OptIn(ExperimentalMaterial3Api::class)
@Composable
fun SignUpTopAppBar(
    modifier: Modifier = Modifier
) {

    val viewTitle = stringResource(R.string.signup_title)
    /**
     * TopBar
     */
    CenterAlignedTopAppBar(
        title = {
            Text(
                text = viewTitle,
                style = TextStyle(
                    color = Color.Black,
                    fontSize = 18.sp,
                    fontWeight = FontWeight.Bold
                )
            )
        },
    )
}
/**
 * Preview
 */

data class SignUpUiState(
    val email: String,
    val password: String,
    val name: String
)

/**
 * For Preview
 */
@OptIn(ExperimentalMaterial3Api::class)
@Composable
fun SignUpWidgetStateless(
    state: SignUpUiState,
    onEmailChange: (String) -> Unit,
    onPasswordChange: (String) -> Unit,
    onNameChange: (String) -> Unit,
    onSignUpClick: () -> Unit,
    modifier: Modifier = Modifier
) {
    val emailLabelText = stringResource(R.string.signup_email)
    val passwordLabelText = stringResource(R.string.signup_password)
    val nameLabelText = stringResource(R.string.signup_nickname_form)
    val emailFormText = stringResource(R.string.signup_email_form)
    val passwordFormText = stringResource(R.string.signup_password_form)
    val nameFormText = stringResource(R.string.signup_nickname_form)
    val signUpBtn = stringResource(R.string.signup_button)
    Scaffold(
        // TopBar
        topBar = {
            SignUpTopAppBar(modifier = modifier)
        },
    ) { innerPadding ->
        Column(modifier = Modifier
            .fillMaxWidth()
            .padding(innerPadding)){
            Spacer(modifier = Modifier.height(16.dp))
            Text(
                text = emailLabelText,
                modifier = Modifier.padding(start = 20.dp, bottom = 0.dp),
                style = MaterialTheme.typography.labelMedium,
                color = Color.Gray
            )
            OutlinedTextField(
                value = state.email,
//                onValueChange = { viewModel.onEmailChanged(it) },
                onValueChange = { onEmailChange },
                label = { emailFormText },
                modifier = Modifier
                    .fillMaxWidth()
                    .padding(horizontal = 20.dp, vertical = 0.dp),
                shape = RoundedCornerShape(10.dp)
            )
            Spacer(modifier = Modifier.height(20.dp))
            Text(
                text = passwordLabelText,
                modifier = Modifier.padding(start = 20.dp, bottom = 0.dp, top = 8.dp),
                style = MaterialTheme.typography.labelMedium,
                color = Color.Gray
            )
            OutlinedTextField(
                value = state.password,
//                onValueChange = { viewModel.onPasswordChange(it) },
                onValueChange = { onPasswordChange },
                label = { passwordFormText },
                modifier = Modifier
                    .fillMaxWidth()
                    .padding(horizontal = 20.dp, vertical = 0.dp),
                shape = RoundedCornerShape(10.dp)
            )
            Spacer(modifier = Modifier.height(20.dp))
            Text(
                text = nameLabelText,
                modifier = Modifier.padding(start = 20.dp, bottom = 0.dp, top = 8.dp),
                style = MaterialTheme.typography.labelMedium,
                color = Color.Gray
            )
            OutlinedTextField(
//                value = name,
                value = state.name,
//                onValueChange = { viewModel.onNameChange(it) },
                onValueChange = onNameChange,
                label = { nameFormText },
                modifier = Modifier
                    .fillMaxWidth()
                    .padding(horizontal = 20.dp, vertical = 0.dp),
                shape = RoundedCornerShape(10.dp)
            )

            Spacer(modifier = Modifier.height(12.dp))
            SignUpSuccessButton(onSignUpClick = onSignUpClick, modifier = modifier)
            LoginButtonByGoogle()
        }
    }
}

@Composable
fun LoginButtonByGoogle() {
    Column {
        OutlinedButton(
            onClick = {

            },
            shape = RoundedCornerShape(12.dp),
            modifier = Modifier
                .fillMaxWidth()
                .padding(horizontal = 20.dp)
        ) {
            Image(
                painter = painterResource(id = R.drawable.icons8_google_96),
                contentDescription = "google logo",
                modifier = Modifier.padding(start = 5.dp, end = 25.dp)
            )
            Text(
                text = stringResource(id = R.string.signup_google),
                color = Color.Black,
                modifier = Modifier.padding(end = 40.dp)
            )
        }
    }
}

/**
 * 会員登録ボタン
 */
@Composable
fun SignUpSuccessButton(
    onSignUpClick: () -> Unit,
    modifier: Modifier = Modifier
) {

    val signUpText = stringResource(R.string.signup_button)
    Button(
        onClick = onSignUpClick,
        colors = ButtonDefaults.buttonColors(containerColor = signUpButtonColor),
        shape = RoundedCornerShape(12.dp),
        modifier = modifier
            .fillMaxWidth()
            .padding(horizontal = 20.dp)
            .height(48.dp)
    ) {
        Text(text = signUpText, color = signUpButtonTextColor)
    }
}

@Preview(showBackground = true)
@Composable
fun SignUpFullPreview() {
    Scaffold(
        topBar = {

        }
    ) { paddingValues ->
        SignUpWidgetStateless(
            state = SignUpUiState(
                email = "preview@example.com",
                password = "password123",
                name = "プレビュー太郎"
            ),
            onEmailChange = {},
            onPasswordChange = {},
            onNameChange = {},
            onSignUpClick = {},
            modifier = Modifier
                .padding(paddingValues)
                .verticalScroll(rememberScrollState())
        )
    }
}


```