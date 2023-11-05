# 第5回課題


## URLとは何か?

- 「 _Uniform Resource Locator_ 」の略。
- ホームページの **ファイルがある場所やファイルの名前などを示す** 住所のようなもの。


* * * 


## クエリ文字列とは何か?

-  **クエリ文字列とは、サーバーに情報を送るためにURLの末尾につけ足す文字列（変数）** のこと。
-  **「?」をURLの末尾につけ、その次に「パラメーター＝値」をつける。** 
-  **複数のパラメーターをつけたい場合は、値の後に「&」を使用する。** 
- この形式で、サーバーに送信したいデータをURLにつけ加えることが可能。
- また、クエリ文字列には「パッシブパラメーター」と「アクティブパラメーター」の2種類が存在する。
>  
> `https:// ○△×□.jp/?●=▲×■&○=△×□` 
>  
> - 「https:// ○△×□.jp/」→基本のURL
> - 「?●=▲×■&○=△×□」→クエリ文字列

### パッシブパラメーター

- パッシブパラメーターは、 **表示されるコンテンツに影響はない。** 
- パラメーターがついていてもついていなくても、表示されるページは同じ。
- パッシブパラメーターをつけ加えるのは、 **Webサイトのアクセス解析をする** ため。
- ユーザーがどこから自分のWebサイトへたどり着いたのかを知るために、固有のパラメーターをつけて計測する。
- 一般的には、 **集客のためにWebサイトへの流入元を分析したいときや、リスティング広告からの流入情報を知りたいときなど** に使われる。


### アクティブパラメーター

- アクティブパラメーターは、パッシブパラメーターと異なり、 **表示されるコンテンツに影響する。** 
- つまり、パラメーターをつけ加えて、 **Webサイトの表示内容を変更する** ことになる。
- ショッピングサイトでアクティブパラメーターを使用することにより、 **商品一覧をサイズごとにフィルタリングしたり、価格順に並べ替えたりすることができる。** 

> 例、Tシャツの商品一覧ページを、Sサイズだけフィルタリングできるようにする。  
> 基本のTシャツの商品一覧ページは、「http://○△×□.jp/category/tshirt/ 」。  
> SサイズをフィルタリングしたTシャツの商品一覧ページは、「http://○△×□.jp/category/tshirt/?t=shirt_size=S」 となる。  


### クエリ文字列についてのまとめ

-  **URLの末尾の「?」の後の文字列のこと。** 
-  **ユーザーの流入元が分かり、自然検索で入ってきたのか、広告から入ってきたのかを区別することができる** 。
- より効率的にWebサイトの集客が可能になる。


* * * 


## パス変数（パスパラメーター）とは何か

- パス変数とは、 **ファイルシステム上の場所を指定するための変数である。** 
- パス変数を使用すると、ファイルシステム上の固定場所への参照を回避できる。
-  **ユーザーIDや記事IDなどを指定するのによく使われる** 。
- 世の中の様々なサービスでパス変数を指定することで、 **特定のユーザーの情報や、記事の情報を表示する** ために活用されている。
-  **URLの末尾に「/」をつけ、その次に「パラメーター＝値」をつける。** 
-  **複数のパラメーターをつけたい場合は、値の後に「/」を使用する。** 
-  **パス変数は省略できない** 。  

> 下記の例はユーザーIDが「１」のユーザーのプロフィールを表示するようなサイトのイメージ。  
> 
>  `http://example.com/user/1`


* * * 


## クエリ文字列とパス変数の違いとは


### 見た目の違い

```
 
 ①https://zenn.dev/search

 ②https://zenn.dev/search?q=Laravel

 ```


- ①と②の見た目違いとして「search」の後に **「?〜」があるかどうか** 。  
- ①の場合、パス変数は「search」、クエリ文字列はなし。  
- ②の場合、パス変数は「search」、クエリ文字列は「?q=Laravel」。  


### 中身の違い

例:株式会社アニメ（ドメイン：Anime.co.jp）に営業部（Sales）があり、チームが以下のように分かれているとする。

SalesTable

 | id |	  name   |
 |:--:|:---------|
 | 1  |	Isono    |
 | 2  |	Doraemon |


チームの中のユーザーは以下の通り


UsersTable

 | id | sales_id |    name    |
 |:--:|:--------:|:-----------|
 | 1  | 1        | サザエ     |
 | 2  | 1        | カツオ     |
 | 3  | 1        | ワカメ     |
 | 4  | 2        | のび太     |
 | 5  | 2        | ドラえもん |
 | 6  |	1        | 波平       |


営業部のIsono（磯野）チームのページを表示するとなるとURLは以下のようになる.

 `https://Anime.co.jp/sales/{group_id}` 



パス変数は特定のもの（画面など）を表示したいときに必要になる。
 ```
 
 https://Anime.co.jp/sales/1
// IsonoチームのSalesTableidは「１」

 ``` 

もし、メンバー一覧を画面表示にしたい場合は、下記のURLとする。

 `https://Anime.co.jp/sales/1/members` 



クエリ文字列は特定のもの（画面など）に条件を加える場合に必要になる。

> 例：上記のメンバー一覧から特定の人を検索したい場合（今回はID検索と想定）  
> 今回はUsersTableのID:3（ワカメ）を検索（条件の追加）する。  
>   
>  `https://Anime.co.jp/sales/1/members?id=3`  


### まとめ


 | 種類 | 省略 | 見た目 | 用途 |
 |:--:|:--:|:--:|:---|
 | クエリ文字列 | ○ | ?の後ろ | 特定のユーザーのアクセスを解析 |
 | パス変数 | × | /の後ろ | 特定のユーザーの情報を表示 |


* * * 


## HTTPメソッドとは何か

-  **ブラウザからサーバーに対して出されるリクエストの種類。** 
- GET、POST、PUT、PATCH、DELETE、CONNECT、OPTIONS、TRACE、LINK、UNLINK、PATCHなどがある。
- ブラウザからサーバーに出される要求は「HTTPリクエスト」という。


### HTTPリクエストの構造

>  １． **HTTPリクエストライン（リクエストライン）**  
> 　　 HTTPリクエストの部品で、送信ファイルと操作内容が書かれている（下図1行目）。 
>  
>  ２． **HTTPリクエストヘッダー（ヘッダー）** 
> 　　 HTTPリクエストの部品で、要求内容の詳細に関する情報（下図2～13行目）。 
>  
>     （空行【CR＋LF】、下図14行目） 
>  
>  ３． **HTTPリクエストメッセージボディ（メッセージボディ）**  
> 　　 POST通信のときの受け渡されるパラメータの内容など、補足のメモ書きが書いてある（下図15行目～）。  


```
POST /search.html HTTP/1.1\r\n　               //←1行目
Host: wa3.i-3-i.info\r\n　                     //←2行目
Connection: keep-alive\r\n
Content-Length: 38\r\n
Cache-Control: max-age=0\r\n
Origin: http://wa3.i-3-i.info\r\n
Upgrade-Insecure-Requests: 1\r\n
User-Agent: 何とか\r\n
Content-Type: application/x-www-form-urlencoded\r\n
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8\r\n
Referer: http://wa3.i-3-i.info/index.html\r\n
Accept-Encoding: gzip, deflate\r\n
Accept-Language: ja,en-US;q=0.8,en;q=0.6\r\n
\r\n　                                         //←14行目
q=test&submitSearch=%E6%A4%9C%E7%B4%A2　       //←15行目
```


 | HTTPメソッド | はたらき                               | 
 |:-------------:|:---------------------------------------|
 | GET           | リソース情報を取得する                   |
 | POST          | 新しいリソース情報を送り込む              |
 | PUT           | リソース情報を新しい情報で置き換える       |
 | PATCH         | リソース情報の一部を新しい情報で書き換える | 
 | DELETE        | リソース情報を削除する                   |


* * * 


## リクエストヘッダーとは何かについて調べてみてください

- リクエストヘッダーとは、Webコンテンツの伝送に用いられるHTTPで、 **クライアントからサーバーへの要求であるHTTPリクエストの前半にある制御情報を記した領域のこと。** 
- 個々のフィールドは「フィールド名: 値」という簡潔な書式になっている。
- リクエストのみで用いるフィールドの他に、レスポンスと共通の一般ヘッダー（日付を示すDateフィールドなど）やエンティティヘッダー（ボディ部のコンテンツについての情報）もある。

 **主なフィールドの例** 
1. 「Host」（送信先のドメイン名とポート番号）
2. 「Referer」（参照元ページのURL）
3. 「User-Agent」（クライアントソフトの識別名）
4. 「Cookie」（ブラウザ側に保存されたサイトデータ）
5. 「Authorization」（認証データ）
6. 「Accept」（受信可能なデータのMIMEタイプ）
7. 「If-Modified-Since」（指定した日付以降に更新されていたらデータの送信を要求）


* * * 


## HTTPステータスコードとは何か

- HTTPリクエストの結果を表す3桁の数字。
-  **200番台は成功** 、 **400番台はブラウザ側のエラー** 、 **500番台はサーバー側のエラー** を意味する。
- 下図はHTTPステータスコードで頻出する代表例。

 | 番号 | 操作内容                              |
 |:----:|:----------------------------------|
 | 200  | OK (成功)                           |
 | 201  | CREATED (作成完了)                    |
 | 400  | BAD REQUEST (不正なリクエスト)            |
 | 404  | NOT FOUND (存在しない)                 |
 | 500  | INTERNAL SERVER ERROR (サーバ内部のエラー) |


* * * 


## レスポンスヘッダーとは何かについて調べてみてください

- レスポンスヘッダーとは、Webコンテンツの伝送に用いられるHTTP。
-  **サーバーからクライアントへの応答であるHTTPレスポンスの前半にある制御情報を記した領域のこと。** 
- 個々のフィールドは「フィールド名: 値」という簡潔な書式になっている。
- レスポンスのみで用いるフィールドの他に、リクエストと共通の一般ヘッダー（日付を示すDateフィールドなど）やエンティティヘッダー（ボディ部のコンテンツについての情報）もある。

 **主なフィールドの例** 
1. 「Location」（リダイレクト先URL）
2. 「Server」（Webサーバーソフトの識別名）
3. 「Age」（プロキシのキャッシュに存在する時間）
4. 「Set-Cookie」（ブラウザ側にサイトデータを保存）
5. 「Vary」（文字コードなど複数の選択肢がある場合にサーバーが選んだものを通知）


* * * 


## レスポンスボディとは何か

-  **サーバーからの応答メッセージがHTTPレスポンスで、その後半部分** がレスポンスボディと呼ばれる領域である。
-  **クライアントへ送信するファイルなどのデータ本体である。** 
- HTTPレスポンスの一部で、 **「ステータスラインに書ききれないレスポンスの情報」** が書かれている場所。


### HTTPレスポンスの構造

> １． **HTTPステータスライン** （ステータスライン、下図1行目）  
> ２． **HTTPレスポンスヘッダー** （ヘッダー、下図2行目～6行目）  
> （空行【CR＋LF】、下図7行目）  
> ３． **HTTPレスポンスボディ** （レスポンスボディ、下図8行目～）  


```
HTTP/1.1 200 OK\r\n　              //←1行目
Server: nginx\r\n　                //←2行目
Date: Tue, 11 Jul 2017 09:23:07 GMT\r\n
Content-Type: text/html\r\n
Transfer-Encoding: chunked\r\n
Connection: keep-alive\r\n
\r\n　                    //←7行目
<!DOCTYPE html>\r\n　     //←8行目
<html lang="ja">\r\n
<head>\r\n
\t<meta http-equiv="content-type" content="text/html; charset=UTF-8" />\r\n
\t<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">\r\n
\r\n
\r\n
\t<meta name="keywords" content="\350\276\236\345\205\270,IT,\347\224\250\350\252\236,\345\210\235\345\277\203\350\200\205">\r\n
\t<meta name="author" content="Makoto Sasaki">\r\n
\t<meta name="copyright" content="Copyright PCS">\r\n
\r\n
\t<meta name="application-name" content="\343\202\217\343\202\217\343\202\217IT\347\224\250\350\252\236\350\276\236\345\205\270"/>\r\n
\t<link rel="stylesheet" href="css/style.css?ver=00109">\r\n
\t<link rel="stylesheet" href="css/search.css?ver=00109">\r\n
\t<script src="./js/jquery-1.7.2.min.js?ver=00109"></script>\r\n
\t<script src="./js/common.js?ver=00109"></script>\r\n
</head>\r\n
<body>\r\n

//（中略）

</body>\r\n
</html>\r\n
\r\n
```


* * * 


## JSONとは何か

JSONとは、JSONとは、JavaScriptにおけるオブジェクトの表記法を応用したテキスト（文字）ベースのデータ形式。
多数の要素が複雑な構造で組み合わせられたデータを簡潔な表記で書き表すことができる。
JavaScriptプログラム上ではコードとして実行するだけで読み込みが完了する。

JavaScriptではオブジェクト定義の構文として、キーと値のペアを列挙したデータ構造を用いる。
他のプログラミング言語では連想配列、ハッシュ、マップ、辞書（ディクショナリ）などと呼ばれるものに近い。

JSONでは、これと配列を利用して複合的なデータ構造を記述することができる。
配列やオブジェクトの値として別の配列やオブジェクトを入れ子の形で記述でき、深い階層構造を持つ複雑なデータを表すことができる。

利用できるデータ型はJavaScriptに用意されているプリミティブデータ型で、整数型、浮動小数点数型、文字列型、ブール型（真偽値）、null（値無し）、配列、オブジェクトである。

配列は [“A”,“B”,“C”] のように全体を角括弧で囲み、値をカンマ区切りで列挙していく。
オブジェクトは { Key1：“Value1”, Key2：“Value2”} のように全体を中括弧で囲み、キーと値をコロン（：）で区切って表記したペアをカンマ区切りで列挙していく。


* * * 


## JASONのデータサンプル

<details><summary>データベースの中にある、個人のアカウント情報の一例。</summary>

```
"accountInformation": [
    {
        "name": "Monkey.D.Luffy",
        "gender": "male",
        "age": 19,
        "dateOfBirthday": "May 5th",
        "adress": "Fusha Village",
        "email": "luffy.kingOfPirates@strawhat.com",
        "password": "niku"
    },
    {
        "name": "Roronoa Zoro",
        "gender": "male",
        "age": 21,
        "dateOfBirthday": "November 11th",
        "adress": "Shimotsuki Village",
        "email": "world.greatest.swordsman@strawhat.com",
        "password": "neverLoseAgain"
    },
    {
        "name": "Nami",
        "gender": "female",
        "age": 20,
        "dateOfBirthday": "July 3rd",
        "adress": "Cocoyashi Village",
        "email": "orange.windmill@strawhat.com",
        "password": "iLoveMoney"
    }
]
```
</details>


* * * 


## 参考文献


- [MDN](https://developer.mozilla.org/ja/docs/Web)
- [わわわ](https://wa3.i-3-i.info/)
- [デジハリONLINE](https://online.dhw.co.jp/kuritama/query-string/ "クエリ文字列（URLパラメーター）とは？ Webサービス上の用途とその役割")
- [Zenn](https://zenn.dev/eri_agri/articles/859a3362db8386 "パスパラメータとクエリパラメータの違い")
- [DPro](https://diveintocode.jp/blogs/Technology/depUrlHttpMethod#:~:text=HTTP%E3%83%A1%E3%82%BD%E3%83%83%E3%83%89%E3%81%AF%E3%80%81%E5%AF%BE%E8%B1%A1%E3%81%A8,%E3%81%AE2%E7%A8%AE%E9%A1%9E%E3%81%A7%E3%81%82%E3%82%8B%E3%80%82 "URL / HTTPメソッドとは")
- [IT用語辞典 e-Words](https://e-words.jp/w/HTTP%E3%83%AA%E3%82%AF%E3%82%A8%E3%82%B9%E3%83%88%E3%83%98%E3%83%83%E3%83%80.html#:~:text=HTTP%E3%83%AA%E3%82%AF%E3%82%A8%E3%82%B9%E3%83%88%E3%83%98%E3%83%83%E3%83%80%E3%81%A8%E3%81%AF%E3%80%81Web%E3%82%B3%E3%83%B3%E3%83%86%E3%83%B3%E3%83%84%E3%81%AE%E4%BC%9D%E9%80%81%E3%81%AB,%E3%81%AE%E8%A9%B3%E7%B4%B0%E3%82%92%E8%A8%98%E8%BF%B0%E3%81%99%E3%82%8B%E3%80%82 "HTTPリクエストヘッダとは、Webコンテンツの伝送に,の詳細を記述する。")
- [Qiita](https://qiita.com/Qiita/items/c686397e4a0f4f11683d "Markdown記法 チートシート")
- [Techpit](https://techpit-market.gitbook.io/host-guide/4/markdown "見やすい文章を書くためのマークダウンの書き方")


