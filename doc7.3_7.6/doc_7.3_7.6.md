<!-- $theme: gaia -->

# <div style="text-align: center;">チーム開発実践入門</div>

### <div style="text-align: center;">7.3-7.6</div>

#### <div style="text-align: center;">中村</div>

---
<div style="font-size: 24pt">

# 目次
</div>

<div style="font-size: 19pt">

* JenkinsとSeleniumの連携(割愛)
* Seleniumの高速化
* 複数のアプリケーションバージョンでのテスト
* まとめ
</div>

---
<div style="font-size: 24pt">

# Seleniumテストの高速化1
</div>

<div style="font-size: 19pt">
* Seleniumテストが遅いのはよく起きる問題
  * ユーザ視点のテストで使われることが多い
  * Selenium自身も高速ではない
* 自動テスト増加に伴う、テストスイート及び実行時間の推移(筆者の所属会社)
</div>

<table style="border: 0px">
<tr align="center">
    <td><img src=images/TestSuiteTransition.png height=300px></td>
    <td><img src=images/TestExeTransition.png height=300px></td>
</tr>
</table>

---
<div style="font-size: 24pt">

# Seleniumテストの高速化2
</div>

<div style="font-size: 19pt">

「分散ビルド」でテストを並列実行
* Jenkinsの持つ並列実行を助けてくれるしくみ
* 数十台～数百台のマシンでクラスタを組むことが可能

<div align="center">
	<img src=images/master_slave.png height=180px>
</div>
手順(詳細はp.301～p.303参照)

1. スレーブとなるマシンをJenkinsに設定
2. マスタとスレーブを接続
3. テストジョブをどのスレーブで事項するかを設定
4. ビルド実行

</div>

---
<div style="font-size: 24pt">

# Seleniumテストの高速化3
</div>

<div style="font-size: 19pt">

Seleniumテスト並列化で起こりうる問題
* 並列化で複数のブラウザが起動し、それぞれがサーバに対してリクエストを行うので、レスポンスが遅くなる(左図)
→各マシンの[hostsファイルを書き換え](	http://onocom.net/blog/windows-hosts-file/)、ブラウザ側とサーバ側を1:1のセットにする(右図)

<table style="border: 0px">
<tr align="center">
    <td><img src=images/client_server1.png height=300px></td>
    <td><img src=images/client_server2.png height=300px></td>
</tr>
</table>

</div>

---
<div style="font-size: 16pt">

# 複数のアプリケーションバージョンでのテスト
</div>

<div style="font-size: 19pt">

メリット
* 緊急なリリースが必要な場合でも、自動テストが実行できれば安心してリリースできる
* 緊急なリリースに対するテストと並行して、次の予定されたリリースに向けた開発を進めることができる
* 複数のブランチで開発が並行している場合でも、ブランチに対応するテストケースが実行可能
→メインのリポジトリへのコミット前に自動テスト可能

手順

1. テストしたいバージョンのアプリをデプロイ
2. テストケースをチェックアウト
(テストケースもバージョン管理されていることが前提)
3. テスト実行

</div>

---
<div style="font-size: 24pt">

# 7章まとめ
</div>

<div style="font-size: 19pt">

リグレッションテストで
　結合テスト、
　ユーザ受け入れテスト
を行うことは、継続してシステムをバージョンUPする上で非常に強力


しかし、必ずしもテストコストを下げることには繋がるわけではない。
メンテが大変...手動のほうが効率が良い...etc.


自動テストを作成する際に、
1. 作ろうとしているテストは今後何回くらい行われるか
2. 将来どのようなメンテが必要になるか

を考えると良い。
</div>