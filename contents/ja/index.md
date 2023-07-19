---
title: SalesforceとChatGPTについて
marp: true
paginate: true
theme: freud
---

<!-- _paginate: false -->
<!-- theme: gradient class: blue-->
<!-- theme: freud class: blue-->

# Salesforce と ChatGPT について <!-- fit -->

</br>
</br>

![height:300](images/qr-code.jpg)

##### スライド:https://powerninja.github.io/chatGPT-Salesforce/ja/index

##### リポジトリ:https://github.com/powerninja/chatGPT-Salesforce

---

# はじめに

#### 今回の話すこと

- ChatGPT の基本情報
- ChatGPT の問題点
- Salesforce X ChatGPT

---

# トピックス

1. ChatGPT とは
2. ChatGPT はどんなことができるのか？
3. ChatGPT の問題点
4. Salesforce との融合(demo)

---

# ChatGPT とは

## 基礎知識

GPT3.5 や GPT4 モデルを使用した人工知能チャットボット

## 開き方

みなさんもご自身の Dev 環境などで、開いてみましょう

1. 設定のギアアイコンを押下する
2. 「開発者コンソール」と記載された箇所があるため押下する
3. 開発者コンソールが開かれる

---

# 開発者コンソールとは

![height:600](images/開発者コンソール_01.png)

---

# 開発者コンソールでできること

## Trailhead より抜粋

1. **Apex クラスやトリガー、Aura コンポーネント、Visualforce ページやコンポーネント**などに移動して作成・編集する
2. 組織で作成したパッケージを参照する
3. **デバッグ用のログを生成して、さまざまな視点から分析**する
4. 自分の **Apex コードをテストして、エラーがないことを確認**する
5. Apex コードにチェックポイントを設定し、エラーを特定して解決する
6. 組織のレコードを**検索、作成、更新する SOQL と SOSL クエリを記述して実行**する

→ 開発は、開発者コンソールで**ほとんど**行うことができる
(※現代の開発環境からはかけ離れていますが...)

---

# 開発者コンソールでできること

## **Apex クラスやトリガー、Aura コンポーネント、Visualforce ページやコンポーネント**などの作成を行う

- 画面左上の「File」を押下 →「New」を選択する
  ![height:400](images/開発者コンソール_03.png)

---

# 開発者コンソールでできること

### 作成できるコンポーネント

- Apex
- Visualforce
  - Visualforce Page:一つで Web ページが作成される
  - Visualforce Component:再利用可能な UI 部品
- 静的リソース(JavaScript)
- Lightning コンポーネント(Aura)
  - Lightning Application: 画面から作成するアプリケーションとは別物
  - Lightning Component:よく使う Aura コンポーネント
  - Lightning Interface:Aura で使用する共通処理を定義する
  - Lightning Event:コンポーネント同士をつなぐ
  - Lightning Tokens:Aura コンポーネント上のスタイルを一元で管理

---

# 開発者コンソールでできること

## **Apex クラスやトリガー、Aura コンポーネント、Visualforce ページやコンポーネント**などに移動して編集する

- 画面左上の「File」を押下 →「Open」を選択し編集したいクラスを開き編集する
  ![height:400](images/開発者コンソール_02.png)

---

# 開発者コンソールでできること

## 編集または、確認できるコンポーネント

- Apex
- Visualforce
- **オブジェクト**
  - 項目の API 参照名と、型が表示される
- 静的リソース
- パッケージ(メタデータ要素のグループ化)
- Aura

---

# 開発者コンソールでできること

![height:400](images/開発者コンソール_04.png)

- 表示したい項目を選択し、Query ボタンを押下することで SOQL が自動作成
- 左下の Execute ボタンを押下し、自動作成された SOQL を実行
- Devtool と違い、キャッシュなどで項目が表示されないなどが起こりにくい

---

# 開発者コンソールでできること

組織のレコードを**検索、作成、更新する SOQL と SOSL クエリを記述して実行**する

1. Query Editor タブを押下
2. SOQL または SOQL を入力
3. 結果が表示されインライン編集可能

![height:400](images/開発者コンソール_08.png)

---

# 開発者コンソールでできること

## **デバッグ用のログを生成して、さまざまな視点から分析**する

- Apex はもちろん**フロー**のログも確認可能
  - 下記は取引先作成時に、年間売り上げ項目に「1」を追加するフロー

![height:400](images/開発者コンソール_05.png)

---

# 開発者コンソールでできること

## **デバッグ用のログを生成して、さまざまな視点から分析**する

### ログの注意点

- **ログインしているユーザのログのみ表示可能**
- デバッグログを仕込む必要なし(デバッグレベルは SFDC_DevConsole )
  - デバッグレベルは設定、または開発者コンソールで変更可能

---

# 開発者コンソールでできること

ログの確認方法

1. ガバナ制限の一覧が表示される
2. デバッグレベルによって、表示が変更される
3. Debug Only：debug ステートメントのみ表示される
   Filter：検索([8]のように記載することで行数検索可能)
   ![height:385](images/開発者コンソール_10.png)

---

# 開発者コンソールでできること

### ログレベルの変更方法(開発者コンソールで行う場合)

1. Debug → Change Log Levels を開く
2. General Trace Settings for You の「Add/Change」を押下
3. 変更したいデバッグレベルを選択する
   ![height:400](images/開発者コンソール_06.png)

---

# 開発者コンソールでできること

自分の **Apex コードをテストして、エラーがないことを確認**する

1. Test → New Run を開く
2. 対象のテストクラスと実行するメソッドを選択
3. 実行したテストクラスで通った箇所、カバレッジ率を確認可能

![height:400](images/開発者コンソール_07.png)

---

# Apex コードの実行

### 1. Apex クラスの動作確認(ログも確認可能)

### 2. レコードの取得・作成・更新・削除(SOQL と DML 操作)

### 3. Apex クラスではなく、Apex コードを記載し匿名で実行する

---

# Apex コードの実行

ご自身の Dev 環境などでお試しください

1. Debug → Open Execute Anonymous Window を押下(または ctrl + E, cmd + E)
2. Enter Apex Code というウィンドウが開きます

![height:400](images/開発者コンソール_09.png)

---

# Apex コードの実行

3. Enter Apex Code に下記コードを入力し、Execute を押下
4. 取引先に test が作成される
   ※SOQL は Query Editor でも実行可能

```Java
    Account act = new Account();
    act.Name = 'test';
    insert act;
    //作成した取引先のIdがログに表示される
    System.debug(act.Id);

    Account resultAct = [SELECT Id, Name FROM Account WHERE Id = :act.Id];
    //作成した取引先をSOQLで取得し、IdとNameを表示する
    System.debug(resultAct);
```

---

# Apex コードの実行

## Apex バッチの起動

- スケジュールしていない時でも、任意でバッチの呼び出しが可能

```java
//呼び出すバッチをインスタンス化
AccountBatch ab = new AccountBatch();
//バッチを起動(200はバッチサイズ)
Database.executeBatch(ab, 200);
```

---

# Apex コードの実行(おまけ)

- 先ほど試したコードを Apex クラスにすると下記

```java
public without sharing class AccountController {
  public static void createAccount(){
      Account act = new Account();
      act.Name = 'test';
      insert act;
      //作成した取引先のIdがログに表示される
      System.debug(act.Id);

      Account resultAct = [SELECT Id, Name FROM Account WHERE Id = :act.Id];
      //作成した取引先をSOQLで取得し、IdとNameを表示する
      System.debug(resultAct);
  }
}
```

- 下記 Apex コードを実行し、Apex クラスを起動する

```java
AccountController.createAccount();
```

---

# vsCode との比較

| 機能                                | 開発者コンソール | vsCode |
| ----------------------------------- | ---------------- | ------ |
| Apex,Aura,Visualforce の作成,更新   | △                | ◎      |
| デバッグの確認                      | ◯                | △      |
| Apex のテスト実行                   | ◯                | ◯      |
| SOQL,SOSL の実行 (クエリエディター) | ◯                | △      |
| Apex コードの実行(匿名実行)         | ◯                | △      |

※ LWC の作成、更新やメタデータの管理は開発者コンソールでは不可

---

# まとめ

- Apex や Visualforce を実際に記載する際は、vsCode の方が扱いやすい
- ただ、Apex を匿名実行したい場合や、SOQL クエリを使いたい場合は開発者コンソールの方が楽に実行ができる
