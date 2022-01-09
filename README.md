# オブジェクト指向@Github
Qiitaのスライドモードをそのまま持ってきてるので線が多く入ってます。気にしないでください。

---
# 前置き
　オブジェクト指向とは、大きなプログラムを書くときには必ず必要になる考え方です。
　概念に少し難しいところがあるかもしれませんが、できる限りわかるように書くつもりです。
　覚えるところだけしっかり覚えながら読めば、問題なく理解できるようにしますので、がんばって覚えてください！

---
## 何ができるの？
　プログラムの構造をはっきりさせることができます。
　構造がはっきりすると、プログラムの修正、拡張、削除を簡単にすることができます。
　構造がしっかりしていないと、削除してはいけない部分を削除してしまったり、1つ仕様変更しようとしただけでたくさんの部分を変更しなければならなくなったりします。
　なので、構造をはっきりさせることは大きなプログラムを書く上で非常に重要です。

---
### 利点
　オブジェクト指向では、プログラムの構造を明確にさせることができる、というのが一番の利点です。
　関数とは比べ物にならないほど、柔軟性のある書き方ができ、一度習得してしまうと、元のプログラミング方法に戻れなくなるほどに便利です。

### 欠点
　ないといっても過言ではありません。というか、思い当たるものが全くありません。
　強いて言うなら、実行速度が多少下がるのでしょうが、実行速度を下げないためにオブジェクト指向を利用しないという選択肢がとられることはまずありません。

---
# 実践！
　この先では、Javaを用いてプログラムの例を示します。
　Javaはオブジェクト指向にある要素がかなり強く表れているので、曖昧な部分が少なく、オブジェクト指向を最初に学習するのには最適化と思われます。
　Javaを試しに動かしたりしたい場合は、[Paiza.io](https://paiza.io/ja/projects/new?language=java)などを使って遊んでみてください。
　ソースコードは写すだけでもいくらか覚えることができますので、ぜひ手を動かして遊んでみてください。

---
## 基本の「キ」
---
　この章では、オブジェクト指向の概念の基本のキとなる部分を説明していきます。
　そのため、差し当たってまず以下の用語についての説明を行いながら、説明をしていきます。。

1. クラス
1. インスタンス
1. 静的
1. 動的
1. new
1. this

---
### クラス
　__`クラス`__とは、__`インスタンス`__の設計図です。
### インスタンス
　__`インスタンス`__とは、__`クラス`__をもとに生成された実体です。
### ...例えば?
　今、目の前にアンドロイドの設計図があります。このとき、
　__アンドロイドの設計図__が__`クラス`__に当たり、
　その設計図をもとに作った__アンドロイド本体(実体)__が__`インスタンス`__に当たります。

---
### そういえば、クラスって？
　__`クラス`__とは、__`インスタンス`__の設計図です。
### そういえば、インスタンスって？
　__`インスタンス`__とは、__`クラス`__をもとに生成された実体です。
### 同じこと2回言ってませんか？
　この2つは覚えておかないと、この先が全く意味不明の呪文のようになるので、___絶対に___覚えてください。

---
### で、プログラムではどう書くの？
　Javaでは、クラスは以下のように定義します。

```java:クラス名.java
public class クラス名{
    // クラスの内容...
}
```
　Javaでは、クラスの宣言に以下の規則があります。

1. ファイル名と、クラス名は、同じにしなければならない。
1. 1つのファイルに、2つ以上のクラスを宣言してはならない。

:::note
　上記の制約は、正確ではありません。
　本当は以下の条件が正しいのですが、まだやっていない要素がいくらか含まれているため、わからないなら今は無視してもらって問題ありません。

1. publicなクラスは、ファイル名と同じ名前にしなければならない。
2. publicなクラスは、ファイル内に2つ以上宣言してはならない。
:::
---
### インスタンスを生成、とは？
　__`インスタンス`__は何から生成するかは覚えていますか？
　__`インスタンス`__は、__`クラス`__から生成するのでしたね。
　__`クラス`__(設計図)から生成されたものを__`インスタンス`__(実体)というのでしたね。
### クラスを定義、とは？
　以下のように書きます(2回目)。

```java:クラス名.java
public class クラス名{
    // クラスの内容...
}
```
---
### 設計図はできたよ！
　今回は、アンドロイドの設計図を書いてみました。
　まだ何も説明していないので、意味が分からなくて当然です。

```java:Andorid.java
public class Android{
    final String name;
    Android(String name){
        this.name = name;
    }
    void sayHello(){
        System.out.printf("My name is ... %s", name);
    }
}
```
　試しに、`Android.java`にこのコードをコピペして、実行してみてください。

　実行しても何も起こりませんね。それはもちろん、設計図を描いただけで動き出すわけはないからですね。

---
### 実体化してみるよ！
　前回は、アンドロイドの設計図をAndroidクラスとして定義しましたね。
　今回は、実体化して__`インスタンス`__を取得してみましょう

```java:Andorid.java(変更なし)
public class Android{
    final String name;
    Android(String name){
        this.name = name;
    }
    void sayHello(){
        System.out.printf("My name is ... %s", name);
    }
}
```
---
```java:Main.java
public class Main{
    public static void main(String[] args){
        Android android1 = new Android("Aji");
        android1.sayHello();
    }
}
```
:::note
ここで、「メインメソッド」という単語がわからない場合は、先にこの記事を読んできてください。
<a href="https://qiita.com/gomaoaji/private/90b7ebf45d6a05bc5d06">＞＞Javaの基礎事項＜＜</a>
:::
---
　実体化する際には、つまり、インスタンスを取得する際には以下のように記述します。

```java
インスタンスを入れる変数 = new クラス名(引数);
```
　ここで一つ覚えて下さい。

　__「「「変数には数以外も入ります。！！」」」__

　よく考えてみてください。変数に文字列入れたことあるでしょ？
　文字列は数ですか？いや違いますよね。

　変数に文字列を入れるのと同じノリで、変数にインスタンスを入れることができます。

---
### クラスとインスタンスの違いは？
ここで、休憩がてら1つ質問をします。

> クラスとインスタンスの違いは？

説明できますか？紙に書いたり、口に出したり、頭の中に書くのでもいいですが、考えてみてください。

　ここで考えないと、この後全くわからなくなります。

---
　「そんなの説明されてないからわからないよ...？」
　いや、説明しましたよ。

　クラスとはどんなものでしたか？

　インスタンスとはどんなものでしたか？

　それらの違いは何ですか？

　もうわかりましたね。

---
　答えはこれです。
> そもそも、比べるものじゃないだろ！

　はい。論外な回答ですが、勘違いはしていません。
　「クラス ≒ インスタンス」という説明をしてしまった人は、このドキュメントを一番最初から読み返してきてください。
　どこにもクラスとインスタンスが似ているとは書いていないはずです。

　クラスとは、インスタンスの設計図でしたね。
　インスタンスとは、クラスから生成されたものでしたね。

　それぞれが似るわけはないですね。当たり前です。
　「設計図 ≒ 実体」だったら、世の中崩壊しますよ。

　設計図書いただけで動き出す車とかあったら怖いでしょ？

---
### ソースコードの説明待ちのお客さんがいらっしゃいます。
　そろそろソースコードを見ていきましょう。

```java:Andorid.java(再掲)
public class Android{
    final String name;
    Android(String name){
        this.name = name;
    }
    void sayHello(){
        System.out.printf("My name is ... %s", name);
    }
}
```
　まずは、クラスの中をざっくり見ます。
　わかることは以下の3つかと思われます。

1. `final`な`String`型の変数`name`が宣言されている。
1. 戻り値のない関数`Android`が宣言されている。
1. 戻り値が`void`の関数sayHelloが宣言されている。

---
#### 1. `final`な`String`型の変数`name`
　残念、これは変数とは呼ばないんですね。`フィールド`と呼びます。(メンバ変数と呼ぶこともあります。)
　なので、正しくは「`final`な`String`型のフィールド`name`」といいます。

##### ...フィールドと変数、何が違うんだ？
　変数が関数の中にあるときは「変数」と呼び、変数がクラス直下にあるとき、「フィールド」と呼びます。要するに、呼び名が違うだけです。
　今回の例では、名前はインスタンス生成時に決定して、後から変えることができないように、finalとしました。

---
#### 2. 戻り値のない関数`Android`
　この関数の重要な点は、「「関数名がクラス名と同じである」」というところです。
　Javaでは、クラス名と同じ名前を持つ関数を「__コンストラクタ__」と呼び、クラスからインスタンスが実体化されるときに一番初めに呼ばれます。

　コンストラクタの引数には、`String`型の`name`があります。
　コンストラクタは、インスタンス(実体)の上で、動きます。
　クラス(設計図)の上で動くわけではありません。
　名前を付けるのはインスタンスのほうであって、クラスではないと考えるとわかりやすいかもしれません。

---
##### `this`ってなんぞや。そんな変数宣言されてない。
　Androidクラスのコンストラクタを再掲します。

```java
    Android(String name){
        this.name = name;
    }
```
　ここで、変数と思われる「`this`」というキーワードが唐突に現れました。
　キーワード`this`は、インスタンスを示します。
　つまり、ここでは、作成されたAndroidを示します。
　なので、`this.name`は、作成されたAndroidのname、という読み替えができます。
　`this`は、あくまでインスタンスを示します。クラスを示すわけではないということを頭に入れておいてください。

---
:::note
補足：「<code>.</code>(ドット)」とは。
<code>.</code>は、プログラミングにおいて、例えば<code>A.B</code>と書いてあったら
「AのB」という意味になります。  
<code>A.B.C</code>とあったら、「(AのB)のC」となり、前から順番に評価されます。
:::

　ところで、このコンストラクタには、`this.name`と`name`が存在します。
　前者は先ほど説明したからいいとして、後者の`name`とは何でしょう。
　後者の`name`は、コンストラクタ引数のnameです。
　コンストラクタ引数は、どこから渡されてくるかというと、ここです。

---
```java:Main.javaより抜粋
        Android android1 = new Android("Aji");
```

　Androidが新しく実体化されるときに、「`"Aji"`」が渡されていることがわかります。
この`"Aji"`が、コンストラクタの引数nameに入ります。
　そこで、もう1度Androidのコンストラクタを見てみましょう。

```java
    Android(String name){
        this.name = name;
    }
```
---
　コンストラクタの中には、代入演算子「`=`」が1つあるだけですね。
　左辺は`this.name`で、右辺は`name`です。
　つまり、引数で受け取った名前を自分の名前としている、というだけです。

　勘違いされがちなのですが、`this.name`と`name`に関係は全くないのです。`this.name`の省略形が`name`であるわけでは全くありません。
　__フィールド__の`name`と__引数__の`name`を区別するためにthisを付けているのです。
　次に説明しますが、フィールドと引数の名前が異なり、区別しなくても示す場所が自明な場合は、thisを省略することができます。
　簡単だったでしょう...？.....。(って自分で言うのはどうなんだ。)

:::note
この場合での<code>this.name</code>を「グローバルなname」、<code>name</code>を「ローカルなname」と区別して呼ぶことがあります。  
グローバルな変数は、クラスまたはインスタンスに紐づけられている変数の総称で、ローカルな変数は、関数内でのみ使うことができる変数の総称です。
:::
---
#### 3. 戻り値が`void`の関数sayHello
　`関数sayHello`と言いたいのですが、実はJavaには関数というものはないんですね。
　というのも、Javaには「すべての要素はクラスの中に書かなくてはならない」という決まりがあるため、素の関数を書くことができないのです。　
　また、クラスの中にある関数をメンバ関数、またはメソッドと呼びます。
　Javaでは、クラスの外にある関数は存在できないので、すべての関数がメソッドです。
　ですから、Javaで関数という呼び方は普通しません。

---
　該当部分を再掲します

```java
    void sayHello(){
        System.out.printf("My name is ... %s", name);
    }
```
　ここで注目すべきは、`printf関数`の中で、「`name`」が登場しているという点です。
　しかし、この関数内にローカルな変数`name`を宣言している箇所は見当たりません。
　この場合、以下のルールが適用されます。

:::note info
<code>this.変数名</code>と<code>変数名</code>を明示的に区別しなくても、ローカルかグローバルかが自明な時は、<code>this.</code>を省略することができる。
:::
　今回の例では、ローカルな変数`name`は存在しないので、グローバルな`name`、つまり`this.name`と解釈されます。

　`printfメソッド`の説明は割愛します。

## 設計図に対して、実体は1つか？
