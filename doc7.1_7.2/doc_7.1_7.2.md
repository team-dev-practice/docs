<!-- $theme: gaia -->

# <div style="text-align: center;">チーム開発実践入門</div>

### <div style="text-align: center;">7.1-7.2</div>

#### <div style="text-align: center;">手島 史裕</div>

---
<div style="font-size: 24pt">

# 目次
</div>

* リグレッションテスト
* selenium

---
###### リグレッションテスト

<div style="font-size: 18pt">

* ユーザー視点のテスト
	* 実際にブラウザを利用して入力や画面遷移。ページが表示されるかなどを確認する
	* 時間がかかるテストが多い
	
    → 処理の高速化には並列処理必須（なお〇田案件...
    
</div>

---
###### テストの種別
<div style="font-size: 14pt">

* 第1象限はCIで出てきた話
* 第2象限はユーザー視点のテスト
	* ビジネス担当者でも理解できるようなテスト内容
	* Seleniumなどもここに該当
* 第3象限は製品の批評にかかわるテスト（自動化不可能）
* 第4象限は技術がかかわる製品の批評

</div>
<div align="center">

<img src=images/2.1.jpg height=350px>
</div>

---
###### リグレッションテストで目指すこと

<div style="font-size: 18pt">

* ユニットテストでは他のWebサービスのAPI連携などの確認は難しい
* OSやブラウザ依存のバグも、実際に結合テストをしないとわからないことが多い
* 様々な条件下でシステムの要望を満たしているかを確認することがリグレッションテストの目的

</div>

---
###### Selenium

<div style="font-size: 18pt">

* Seleniumとは
	<div style="font-size: 14pt">
    
    * ブラウザ駆動型のテストツール群
    </div>

* Seleniumコンポーネント
	<div style="font-size: 14pt">
    
	* SeleniumIDE
		* テストケース作成から実行、デバックまでできる。
		* FireFoxのアドイン
	* SeleniumRC（Selenium1）
		* マシン上にサーバーを起動してサーバー経由でテストを実施する
		* 複数のブラウザでテスト可能
		* プログラム言語でテスト作成するため、効率的なテストが作成できる
		* ブラウザ操作部分がJSのため、セキュリティ制限を多く受ける
	* Selenium WebDriver(Selenium2, 〇田案件で使用)
		* Selenium1の利点が反映されている
		* JSサンドボックスの外部で動作する機能を持つ
		* 高速軽量汎用的なブラウザエミュレーターを持つ
	</div>
</div>

---
###### Selenium周りで出てくるツール
<div style="font-size: 18pt">

* agouti
	<div style="font-size: 14pt">
    
    * WebDriverのクライアントのgolang版
    * 一つのバイナリになるのでチームなどへの連携、配布が楽
    * 〇田さんが宣伝してた
    </div>

* PhantomJS
	<div style="font-size: 14pt">
    
	* ヘッドレスブラウザ
	* テストの時にブラウザが開かずとも裏でテストやってくれる
	* ブラウザ表示しないくせにスクショが取れる
	* 私がSeleniumでブラウザ動作眺めてたら「PhantomJSでいいじゃんwwww」と〇田さんに言われた
	</div>
</div>

---

# Selenium IDEを試してみる

---

# Selenium2を試してみる

---

# agoutiとPhantomJS
# を試してみる

---

###### Seleniumあれこれ
<div style="font-size: 18pt">

* ボタンがあるはずなのに無いと怒られる
	<div style="font-size: 14pt">
    
    * Seleniumの処理が画面遷移速度を上回る
    → 画面が作成される前にボタン操作とかしようとする
    → ボタンが無いと怒られる
    </div>
    
    
* textボックスに入れた文字が正しく反映されない
	<div style="font-size: 14pt">
    
	* 入力処理をしてから、textボックスに文字が反映される前に次のUI操作をすると死ぬ
	* textボックスの中身を空にする処理をしてもステータス上は消えない([参考](	http://qiita.com/MasamotoMiyata/items/ff48bacb0dd3bc599182))
	→ 「空にする、なんか文字入れる、backspaceで文字を消す」で対応できる
    
    
* テストだけではなくブラウザの操作を自動で行うためだけにも利用可能
	<div align="center">
    <img src=images/auto.png height=100px>
	</div>
    
* テストしようとするだけで、可読性の高いコードを書く気にもなれる
    <div align="center">
    <img src=images/magic.png height=100px>
	</div>

</div>