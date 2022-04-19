# vscode-playground

## 対話式のエディタ機能体験

VS Code の中心であるエディタには多彩な機能が満載されています。このページでは、その中のいくつかの機能に焦点を当て、多数の埋め込みエディタを使用して対話的に試してみることが可能です。VS Code のエディタ機能に関する更なる詳細については、[ドキュメント](https://code.visualstudio.com/docs/editor/codebasics) を参照してください。

### マルチカーソル編集 (Multi-Cursor Editing)

複数のカーソルを使用することで、ドキュメントの複数の部分を同時に編集できたりと、生産性が大幅に向上します。以下のコードブロックで次の操作を試してください:

1. カーソルの追加 - **Ctrl+Alt+UpArrow** または **Ctrl+Alt+DownArrow** を押すことで、上または下の行に新しいカーソルを追加します。**Alt+Click** でマウスを使用して、どこにでもカーソルを追加することができます。
2. ボックス選択 - テキストブロックを選択するには **Shift+DownArrow**, **Shift+RightArrow**, **Shift+UpArrow**, **Shift+LeftArrow** のいずれかの組み合わせを押します。![image](https://user-images.githubusercontent.com/1501327/163929446-c265e09a-5821-4d02-9e37-d005d9760098.png) を押しながらマウスでテキストを選択することもできます。
3. 文字列のすべての出現箇所にカーソルを作成する - 文字列である 1 つのインスタンスを選択してください。 例えば、`background-color` を選択して ![image](https://user-images.githubusercontent.com/1501327/163931384-38644c7d-d597-41c8-a957-b787bb37f829.png)
 を押します。この状態で、何か文字を入力することにより、選択された全てのインスタンスを置き換えることができます。

それはマルチカーソル編集のための氷山の一角です。追加のアクションについては、`選択メニュー`の他に、便利な[キーボード操作リファレンスガイド](https://github.com/winofsql/vscode-template/blob/main/keyboard.md)を参照してください。

![image](https://user-images.githubusercontent.com/1501327/135271074-dfe0750a-ee98-42b4-84b3-c5fc5ac330c4.png)

> **CSS のヒント:** 上の例では、CSS についても色見本を提供しています。`＃p1` などの要素にカーソルを重ねると、この要素が HTML でどのように表現されるかが示されます。これは、言語固有となるエディタ機能の簡単な例でもあります。

### インテリセンス (IntelliSense)

Visual Studio Code には、JavaScript と TypeScript をサポートする強力な IntelliSense 機能があらかじめ組み込まれています。次の例では、エラーを示すアンダーライン(赤い波線)の前に配置される `.` (ドット)の直後にテキストのカーソルを置き、**Ctrl+Space** を押してインテリセンスを呼び出します。サジェスチョンが Request API からどのように提供されるかに注目してください。

```js
var express = require('express');
var app = express();

app.get('/', function (req, res) {
    res.send(`Hello ${req.}`);
});

app.listen(3000);
```

>**ヒント:** JavaScript と TypeScript 以外の言語でも、優れたインテリセンスの機能を多くの[拡張機能](command:workbench.extensions.action.showPopularExtensions)をとおして利用することが可能です。

### 行編集のアクション (Line Actions)

テキスト全体をとおし、行を処理することが常に行われるため、この操作を支援するための便利なショートカットキーを用意しています。

1. ![image](https://user-images.githubusercontent.com/1501327/163935969-adc1c298-3cc7-4d6d-a75b-5f08a9870368.png) または、![image](https://user-images.githubusercontent.com/1501327/163936038-444e1f8a-67d8-43b6-813c-ae5133f96f83.png) の操作で、行をコピーして、現在のカーソル位置の上または下に挿入します。
2. ![image](https://user-images.githubusercontent.com/1501327/163936239-cb27be62-249c-4765-be18-dd7828df3525.png) または ![image](https://user-images.githubusercontent.com/1501327/163936278-29e8b53a-68f2-415f-979d-22112a8f9d35.png) の操作で、 行全体または選択された行を上下に移動します。
3. kb(editor.action.deleteLines) の操作で、カーソルが置かれている行全体を削除します。

```json
{
    "name": "John",
    "age": 31,
    "city": "New York"
}
```

> **ヒント:** 良く利用する他の操作としては、コードのブロックをコメントアウトがあります - kb(editor.action.commentLine) を押して、コメントを切り替えることができます。

### 名前変更によるリファクタリング (Rename Refactoring)

関数名や変数名などのシンボル名をとても簡単に変更することができます。すべてのインスタンスの名前を変更するには、`Book` にカーソルを置き、kb(editor.action.rename) を押します。また、この操作は、プロジェクトに含まれるすべてのファイルに適用されます。右クリックのコンテキストメニューから実行することでリファクタリングすることもできます。

```js
// Reference the function
new Book("War of the Worlds", "H G Wells");
new Book("The Martian", "Andy Weir");

/**
 * Represents a book.
 */
function Book(title, author) {
	this.title = title;
	this.author = author;
}
```

>**JSDoc のヒント:** 上記で紹介した例以外にも、`JSDoc` コメントを使用しインテリセンスのヒントを得る方法があります。これを試すには、`Book` 関数を呼び出して、インテリセンス機能で拡張されたコンテキストとその関数のパラメータを確認します。

### フォーマット (Formatting)

コードの可読性を保つために、良いフォーマッタが助けてくれます。幸いなことに、ドキュメント全体を kb(editor.action.formatDocument) で編集するか、kb(editor.action.formatSelection) で書式を現在の選択範囲に適用することができ、コンテンツに書式設定を適用することが簡単に行えます。これらのオプションは、右クリックのコンテキストメニューからも利用できます。

```js
var cars = ["Saab", "Volvo", "BMW"];

for (var i=0; i < cars.length; i++) {
// Drive the car
console.log(`This is the manufacturer [${cars[i]}])`);
    }
```

>**ヒント:** [拡張機能ギャラリー](command:workbench.extensions.action.showPopularExtensions)にて、追加のフォーマッターを入手することができます。フォーマットのサポートは、[設定](command:workbench.action.openGlobalSettings)などで構成することもできます。例えば、`editor.formatOnSave`を有効にするなど

### コードの折りたたみ (Code Folding)

大きなファイルでは、可読性を高めるためにコードの一部を折りたたむ機能が便利です。コードを折りたたむには kb(editor.fold) を押します。展開するには、kb(editor.unfold) を押すだけす。折りたたみは、左ガターにカーソルを合わせると出現する +/- アイコンでも行うことができます。すべてのセクションを折りたたむには kb(editor.foldAll) を、またはすべてのセクションを展開するには kb(editor.unfoldAll) を押してください。

```html
<div>
    <header>
        <ul>
            <li><a href=""></a></li>
            <li><a href=""></a></li>
        </ul>
    </header>
    <footer>
        <p></p>
    </footer>
</div>
```

>**ヒント:** 折りたたみはインデントに基づいているため、すべての言語に適用されます。折りたたみ可能なセクションを作成するためには、コードをインデントするだけで、kb(editor.foldLevel1)〜kb(editor.foldLevel5)のようなショートカットで一定数のレベルを折りたたむことができます。

### エラーと警告 (Errors and Warnings)

コードを編集する際にエラーや警告が `赤い波線 (squiggles)` で強調表示され、`スクロールバーのインジケータ`にエラーを意味する赤いバーが表示されます。下のサンプルでは、実際にいくつかの構文エラーを見ることができます。エディタにカーソルを置き、kb(editor.action.marker.next) を押すと、順番にエラーをナビゲートし、詳細なエラーメッセージが表示されます。エラーを修正すると、`赤い波線 (squiggles)` と `スクロールバーのインジケータ`が更新されます。

```js
// This code has a few syntax errors
Console.log(add(1, 1.5));


function Add(a : Number, b : Number) : Int {
    return a + b;
}
```

###  スニペット (Snippets)

スニペットを使用して編集作業を大幅に高速化できます。まずはじめに、`try` を入力し、表示される提案リストから `trycatch` にカーソルをあわせ、kb(insertSnippet) を押すことで `try`->`catch` ブロックが作成され挿入されます。さらに、簡単に編集できるようにテキスト `error `にカーソルが表示されます。複数のパラメータが存在する場合は、kb(jumpToNextSnippetPlaceholder) を押してジャンプすることが可能です。

```js

```

>**ヒント:** 拡張機能ギャラリーには、ほとんどすべてのフレームワークと言語のためのスニペットが含まれる多くの素晴らしい[拡張機能](command:workbench.extensions.action.showPopularExtensions)が公開されています。 独自の[ユーザー定義スニペット](command:workbench.action.openSnippets)を作成することもできます。

### エメット (Emmet)

Emmet は、スニペットのアイデアをまったく新しいレベルに引き上げます: 動的に解析できる CSS のような式を入力し、入力された省略形の内容に応じて出力を生成することができます。Emmet の使い方はとても簡単です。Emmet 構文を入力した後で `tab` キーを押すだけで、展開が行われます。 Emmet の動作を確認するには、`ul>li.item$*5` の後にカーソルを置き、`tab` キーを押してください。

```html
ul>li.item$*5
```

>**ヒント:** [Emmet チートシート](http://docs.emmet.io/cheat-sheet/) は、Emmet 構文候補の素晴らしいソースです。 `emmet.syntaxProfiles` [setting](command:workbench.action.openGlobalSettings) を使用して、様々な言語で Emmet 機能を有効にすることもできます。詳細については、[Emmet in VS Code](https://code.visualstudio.com/docs/editor/emmet) のドキュメントをご覧ください。

