autoscale: true

![full center](https://raw.githubusercontent.com/mirucon/wct-2018-slide/master/screenshots/%E9%87%91%E4%BA%95%20%E4%BF%8A%E6%B5%A9.jpg)

---

# *テーマレビューの現場から見た、抑えておくべきテーマ制作のセオリーと基礎知識*

#### *WordCamp Tokyo 2018 / 金井俊浩*

---

## 自己紹介

---

### 金井俊浩 (mirucon)

* フリーランスの Web エンジニア
* 最近は Vue.js などのフロントエンドがメイン

* WordPress Core Contributor
* WordPress テーマ Coldbox 開発者
* WordPress テーマレビューチームモデレータ

* *Twitter: @mirucons / Facebook & GitHub etc.: mirucon*
* *https://www.mirucon.com/*

^ (for TRT mod) WordPress.org に申請されるテーマをレビューし、承認したり、問題点があればそれを指摘したりする。これは誰でも参加できる。

![30% right fit](https://raw.githubusercontent.com/mirucon/wct-2018-slide/master/screenshots/code-new-circle.png)

---

<!--

## このセッションの目的

* テーマ制作に興味があり、なんとなくのテーマの構造がわかっている人
* 受託開発などでテーマ制作をしたことがあるが、配布テーマを作ってみたい人

---

-->

## テーマの基礎

---

### テーマとは

---

### テーマとは

##### ウェブサイト全体の見た目からレイアウト、構成、機能まで様々な場所に影響を及ぼす、WordPress サイトの「キモ」

---

### ディレクトリ構成

* 例えばこんな感じ :

```
my-theme/
  L inc/
    L customizer.php
    L related-posts.php
  L footer.php
  L functions.php
  L header.php
  L index.php
  L readme.txt
  L screenshot.png
  L single.php
  L style.css    
```

^ index.php, style.css は必須・テンプレートファイルについて

---

### テーマでは何をするべき ?

---

### テーマでは何をするべき ?

* テーマは結局プラグインと同じただの PHP ファイルなので、やろうと思えば何だってできる

^ ただテーマテンプレートファイルは使いやすいので

* ただしテーマはプラグインと違って1つしか有効化できない

^ あまりに機能をテーマに入れすぎると、テーマを変えた時にその機能が動かなくなる事件が発生する

* そのため WordPress.org のテーマディレクトリの要求事項では「テーマは基本的に見た目を司ることのみすべき」つまり、

**=> 見た目に直接関係ない機能をテーマに入れるべきではない**

^ 例 : Open Graph タグ・Google Analytics 機能

^ テーマに入れてはいけない機能のことを "plugin territory" と呼ぶ

---

### テーマでは何をするべき ?

* ただしこれは WordPress.org のテーマディレクトリの話であり、他のテーマ配布サイト等では違ったりする

* 結局は個々の機能をプラグイン化するのと、テーマで一元化してすべてを管理するのは便利さとのトレードオフ

* また受託開発などでは機能自体に汎用性がない場合・なんらかの事情によってプラグインを使いにくい場合などもある

**=> 自分の制作している目的・公開範囲などを考えて、適切なところを考えよう**

^ (last) ただし、多くの人に使ってもらいやすい (管理ページからアクセスしやすいなど目立つところにある) WordPress.org テーマディレクトリの方針は覚えておこう。特に配布テーマの場合、特定のテーマに依存させてしまうのはユーザーフレンドリーではない

---

## ライセンスについて

^ どんな人にでも知っておいてほしいライセンスの話

---

### WordPress はオープンソース

* WordPress は本体がオープンソース
* GPL ライセンスを使用している
* WordPress は思想として「パブリッシングの民主化 (Democratize publishing)」を掲げている
* オープンソースなので WordPress の開発・ディスカッション・翻訳などには誰でも貢献できる

^ (for democratization) 誰でも簡単に「パブリッシング」(ネット上で記事を公開できるように) 。(今こそ様々なブログサービスがあり、当然かも知れないが WordPress のリリースは2003年)。

^ (for contributing) WordPress の貢献と聞くと難しいと思うかもしれないが、簡単なものも多い (例えば誤字修正) し、とっかかりやすくしようとみんな頑張ってる。「プラグインを作る」「テーマを作る」みんなに使ってもらうことや、開発だけでなく、WordPress についてのブログを書くことでも十分貢献。

---

### GPL ライセンスとはどんなライセンスか

* **G**eneral **P**ublic **L**icense の頭文字をとって "GPL" と呼ばれるオープンソースライセンスの一つ
* いかなる**制約なし**に無保証で**4つの自由**を認めるのが基本思想

^ 「いかなる制約なし」とは本当にどんな制約もなしに -  テーマならどんなサイトでも使えるようにするなど

---

### 4つの自由とは ?

* どんな目的にも使用する自由
* ソースコードを研究し、改変する自由
* 他の人に再配布する自由
* 改変したものを共有する自由

^ (for redistribution) これにより他のテーマ・プラグインのコードを参考にしたりとかもできる (ただし著作権はあるよ)

^ これら自体はそこまで珍しいものではない

---

### 最大の特徴コピーレフト

* コピーレフトとは、制作物の改変されたものや派生プロダクト (derivative work) にも、もとの制作物と同一の自由を認めるべきという考え方
* WordPress の場合 :
	* **もとの制作物** = WordPress
	* **派生プロダクト** = テーマ・プラグインなど
	
=> **つまり、WordPress が GPL である限り、配布する作ったテーマ・プラグインも GPL にする義務が発生する**

^ (last) この流れは永遠に続くわけであり、WordPress の派生プロダクトを元に作られたテーマは GPL, そしてそれを元に作られた子テーマも GPL になって… といったようにずっと続く

<!-- ^ (for next) (スプリットライセンスについて) WordPress のテーマはすべて自由じゃないといけないのじゃないの ?  と思う人もいるかも知れない -->

<!--

---

### 100% GPL とスプリットライセンス

* 基本的にこのコピーレフトの範囲は **PHP ファイルのみ** と考えられている
* そのため、**100% GPL** と **スプリットライセンス** の2つのライセンス方法が存在する
* 100% GPL は CSS や画像等すべてを GPL もしくはその互換ライセンスでライセンスすること
* スプリットライセンスは PHP ファイルのみを GPL とし、他リソースを非 GPL 互換ライセンスでライセンスすること = つまりテーマの中に GPL と他ライセンスが混ざることになる

---

### どっちがいいの ?

* スプリットライセンスは WordPress の「自由を認める」という思考に反する
* WordPress.org のテーマディレクトリにそのテーマを掲載できなくなる他、**WordCamp などのイベントへの登壇・運営スタッフ参加・**などが出来なくなる

-->

---

### 配布しない場合について

* GPL は**配布する場合にのみ**適応されるライセンスであり、配布しない場合には GPL でライセンスする**必要はない**
* それでも WordPress を使っているということは GPL 製品を使っているということなので、是非皆さんに知っておいてもらいたい

^ GPL は変わるものではない - GPL の最初のリリースは1989年

---

## テーマの始め方

---

### スターターテーマ

---

### スターターテーマ

* 手間のかかる最初の設定や、どんなテーマでも必要になるようなコードが設定済みの、制作のもとにするテーマ
* 例えば :
	* Sass のコンパイル設定
	* index.php や single.php のループ (投稿表示部分)

---

#### \_s (underscores)

* Automattic 社 (JetPack プラグインの開発などをしている会社) の開発するスターターテーマ
* かなり中身はシンプルな PHP テンプレート + CSS (SCSS)
* シンプルに抑えたいテーマに特におすすめ

![right50%](https://raw.githubusercontent.com/mirucon/wct-2018-slide/master/screenshots/underscores.me.png)

---

### コーディング規約

---

### コーディング規約


* コーディング規約は **コードの書き方** についての決まりごと
* WordPress には **WordPress Coding Standards** という、WordPress 専用の規約がある
* これはコードのフォーマットだけでなく、後で触れる**セキュリティ**に関することも含まれる

^ ぜひ知っておいてもらいたいもの
^ _s だと設定済みなので特に簡単

---


### WordPress Coding Standards

* 例えば :

```php
if (is_single() ){
```

のようなものを以下のように書くべきと規定できる :

```php
if ( is_single() ) {
```

---

^ 自動で修正できる機能もついているので、手動で直す必要はない

^ 他の便利機能はあとで紹介します

<!--ここにもうちょっとあるといいかも-->

### 役立つとき

* 複数人開発する時に、コードの書き方の癖をなくせる
* 一人開発でも、アップデートの期間が空いてしまったときでもコードの質を保てる

---

## セキュリティについて

---

### なぜセキュリティ対策が必要なのか

^ 具体的な話の前に理由を

---

### なぜセキュリティ対策が必要なのか

* プログラムには「特別な意味を持つ文字列」があったりする
* また WordPress では HTML を扱うことが多く、**HTML を使用できる = JavaScript を使用できる** ということであり、JavaScript には色々なことができてしまうため、悪用の恐れがある

---

### なぜセキュリティ対策が必要なのか

たとえば、HTML のこんな文字列 :

```
< > ' " &
```

これらを許可してしまうと、予期しないところで HTML が使われてしまう

---

### クロスサイトスクリプティング (XSS)

* ユーザーが予期しない動作をするコード (特に JavaScript) を読み込むこと
* JavaScript で実際にできてしまうこと :
	* 勝手に他のサイト (特にウイルス配布サイトなど) に転送
	* 投稿内容を書き換え

^ こんなようなものがカスタム HTML フィールドなどの出力時に動作されてしまったりする

^ これを防ぐためには次のようなことをしよう :

---

### 大きく2つのセキュリティ対策

* サニタイズ
	=> データを**保存するとき**にデータを無害化 = 信用できない文字列を取り除く
	
* エスケープ
	=> データを**出力するとき**に特殊文字列を変換し特殊文字列としての効果を打ち消す

---

### サニタイズ

^ 「データを**保存するとき**にデータを無害化 = 信用できない文字列を取り除く」と紹介したが実際の例を見よう

---

### サニタイズの例

* `wp_kses()` 関数
	* 許可する HTML のクラス・属性を指定し、許可されないものを削除する

例えばこんな HTML :

```html
こんにちは、<br/>
<span class="my-class" style="color: red">金井</span>です。
```

---

### 普通に表示すればこうなる :

---

### 普通に表示すればこうなる :

![inline center fit](https://raw.githubusercontent.com/mirucon/wct-2018-slide/master/screenshots/strings-before-kses.png)

^ \<br\> なので改行と、\<span style\> 内の `color: red` が適応される

---

#### wp_kses() 関数を使うと

#### *`wp_kses()` 関数 を使って `<span>` タグと `class` 属性のみを許可*

---

### wp_kses() 関数を使うと :

![inline 200% center](https://raw.githubusercontent.com/mirucon/wct-2018-slide/master/screenshots/strings-after-kses.png)

![inline 160% center](https://raw.githubusercontent.com/mirucon/wct-2018-slide/master/screenshots/html-after-kses.png)

^ わかりやすさのために出力しているが、本来はデータ保存のタイミング

---

### `wp_kses()` 関数の使い方

```php
$allowed_html = [
  'span' => [
    'class' => [],
  ],
];

$data = wp_kses( $data, $allowed_html );
```

---

### 他の WordPress サニタイズ関数

* wp\_kses\_post()
* wp\_kses\_data()
* sanitize\_email()
* sanitize\_file\_name()
* sanitize\_html\_class()
* sanitize\_text\_field()

^ ぜんぶ WordPress 側で用意されている

---

### テーマカスタマイザーとサニタイズ

```php
$wp_customize->add_setting(
	'credit_text', [
		'default'           => '©2018 このサイトの運営者',
		'sanitize_callback' => 'wp_kses_post',
	]
);
$wp_customize->add_control(
	new WP_Customize_Control(
		$wp_customize, 'credit_text', [
			'label'       => __( 'クレジットを編集', 'text-domain' ),
			'section'     => 'footer',
			'type'        => 'textarea',
		]
	)
);
```

^ テーマカスタマイザーという、テーマの設定画面に追加できる設定  
^ HTML を含む文字列を扱うことや、ラジオボタンなど、特定の文字列以外でないことを確認したいこともある
	
---	

### エスケープ

---

### エスケープの例

* `esc_html()` 関数  
	=> すべての HTML をプレーンテキスト化する<br/>	

例えばこんな HTML :<br/>

```html
こんにちは、<br/>
<span class="my-class" style="color: red">金井</span>です。
```

---

### するとこうなる :

![inline fit](https://raw.githubusercontent.com/mirucon/wct-2018-slide/master/screenshots/strings-after-escape.png)

---

### エスケープの動作

* HTML の特殊な文字列を、**エスケープ文字**と呼ばれる特殊な意味が無効化される文字列に置き換える

例 :

```
< (小なり) => &lt;
> (大なり) => &gt;
```

^ こういった文字列を使用することで文字効果を打ち消すことができ、普通の文字列として表示するようになる そのため HTML タグが動かないように

---

### 他の WordPress エスケープ関数

* esc_attr()
* esc_url()
* esc_textarea()
* esc_js()

---

### セキュリティ対策のコツ

---

### セキュリティ対策のコツ

* すべてを疑うこと

* サニタイズした上でエスケープが必要なこともある

* WordPress Coding Standards を使う

---

### セキュリティ対策のコツ - WordPress Coding Standards

![inline center](https://raw.githubusercontent.com/mirucon/wct-2018-slide/master/screenshots/wpcs-xss-notice.png)

^ 「ここに変なものを入れる人はいないだろ」のような慢心をしない

---

## メンテナンスをしやすくするには

---

### 「WordPress の書き方」を覚える

* WordPress には素の PHP とは違う「WordPress 的な書き方」がある
* 例えばこのような関数など :

	* `get_template_part()`
	* `wp_enqueue_script()`,  `wp_enqueue_style()`

^ `get_template_part()` は require ではない、「テンプレートパーツを読み込むもの」  
^ `enqueue` 系は直書きをしないように
	

---

### ドキュメントを書く

* クラス・関数には極力ドキュメントを書く
	* WordPress Coding Standards を使うとコメントが抜けていると教えてくれる
* ドキュメントの書き方として **phpdoc** コメント という物がある


^ (for documenting) 時間が経つと、そもそもこのコードが何をするかよくわからなくなってしまう場合もある。その際にいちいち全部コードを読み解いていると時間がかかってしまう  
^ ドキュメントの正しい書き方も学ぶ

---

### phpdoc コメントの書き方

```php
/**
 * 指定された数の関連記事を返す.
 *
 * @param int $max_posts 表示する最大記事数.
 * @since 1.0.0
 **/
function theme_get_related_posts( $max_posts ) {
	... 
```

---

### テーマをチェックできるツール・プラグインを使う

* [テーマユニットテスト](https://wpdocs.osdn.jp/%E3%83%86%E3%83%BC%E3%83%9E%E3%83%A6%E3%83%8B%E3%83%83%E3%83%88%E3%83%86%E3%82%B9%E3%83%88)
* [Theme Check | WordPress.org](https://wordpress.org/plugins/theme-check/)
* [WPTRT/theme-sniffer: Theme Sniffer plugin using sniffs.](https://github.com/WPTRT/theme-sniffer)
* [Debug Bar | WordPress.org](https://wordpress.org/plugins/debug-bar/)

---

## WordPress.org テーマディレクトリ掲載にあたって

---

### 要求事項

* WordPress.org テーマディレクトリには **要求事項  (Requirements)** という、掲載のために沿わないといけないルールがある
* 要求事項の詳細は、[Required – Theme Review Team — WordPress](https://make.wordpress.org/themes/handbook/review/required/) を参照
* 日本語訳もあります : [https://github.com/mirucon/required-ja](https://github.com/mirucon/required-ja)


^ 前に述べた、「テーマでは何をすべき」かといったもの  
^ テーマ作者にとっては多少なりとも面倒なものもあるが、ユーザー側に便利なもの

---

### テーマレビューチームは誰でも参加できる

* やる気がある人なら誰でも歓迎
* 人のテーマを見ることで自分のテーマ制作にとても役に立つ
* 最終的に承認できる権限は限られた人にしか与えられてないので、安心して良い

---

## まとめ

* テーマ制作には、**スターターテーマ**、**WordPress Coding Standards** など便利なツールが多い
* GPL ライセンスは自由を認める、利用者にも開発者にも優しいライセンス
* セキュリティ問題には主に「サニタイズ」と「エスケープ」で対策する

---

## ありがとうございました

##### *Twitter: @mirucons*
##### *https://www.mirucon.com/* 