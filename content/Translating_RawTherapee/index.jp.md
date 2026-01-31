---
title: Translating RawTherapee
contributors:
  - Yz2house
tags:
  - 'Localization'
---

<div class="pagetitle">

RawTherapeeの翻訳

</div>

　この項ではRawTherapeeのインターフェイスの翻訳に協力する手順を説明します。

## イントロダクション

　RawTherapeeのグラフィカルユーザーインターフェイスは多くの部分でテキストが使われています。このテキストを様々な言語で表示するために、コードにキーだけを包含し、テキストを表示する場合は、ユーザーの選択した言語に対応するコードのキー値ペア（[key--value
pair](https://en.wikipedia.org/wiki/Attribute–value_pair)）の翻訳ファイルの中で、そのキーを探します（或いは、RawTherapeeに設定されている自動検知機能で探します）。選択された翻訳ファイルの中にキーが見つかれば、キーに対応したテキストが使われますが、キーが見つからない場合は、元に戻って英文が使われます。

　参照するキー値ペアを含んだファイルのことを[`default`](https://github.com/Beep6581/RawTherapee/blob/dev/rtdata/languages/default)と呼びます。ファイルは米国英語で書かれています。全ての翻訳がこのファイルを基本に行われます。翻訳の中にキーが見つからない場合は、このdefaultファイルの値（テキスト）が使われます。

　翻訳ファイルは[`/rtdata/languages`](https://github.com/Beep6581/RawTherapee/blob/dev/rtdata/languages/)の中に格納されています。

　時々、私たちは`default`ファイルに追加された新しいキーで翻訳ファイルを更新するために`/tools/generateTranslationDiffs`スクリプトを実行します。新しいキー値ペアがdefaultに追加されると、翻訳ファイルにそれが存在しない場合は、スクリプトがそのペアをコピーして貼り付けます。但し、その時点で値（テキスト）は英文であるため、そのキーに接頭語“！”を付けます-RawTherapeeは翻訳された文字列を探す時には、接頭語“！”が付いた文字列を無視します。翻訳協力者がバリュー（英文テキスト）を翻訳する時は、この“！”を削除し、プログラムに無視されないようにします。

　このシステムの不都合は、`default`のキーに対応している値が変わりエントリーが既に翻訳されてしまっている場合、その翻訳が古くなってしまいますが、このことを注意喚起する手段がないことです。この理由から、翻訳の管理にはdefaultの既存値が変更されているかどうか確認する必要があります。変更されていれば、それに応じて翻訳を更新します。`default`の変更に注意するには、時折\[<https://github.com/Beep6581/RawTherapee/commits/dev/rtdata/languages/default>　ファイルに影響するgit
commits\]を確認します。

“露光量補正”のラベルを例にとって説明すると:

- コードの中で使われているキーは`TP_EXPOSURE_EXPCOMP`です。
- `default`ファイルのキー値ペアは:
    
  `TP_EXPOSURE_EXPCOMP;Exposure compensation`です。
- `English (US)`ファイルはこれと同じペアを持っていますが、“！”という接頭語が付いています:
    
  `!TP_EXPOSURE_EXPCOMP;Exposure compensation`です。
- 翻訳はキーと翻訳された値（テキスト）を含みますが、接頭語“！”はありません、つまり以下のように:
    
  `TP_EXPOSURE_EXPCOMP;Lorem ipsum`です。

## 翻訳の手順

1.  まず、[`/rtdata/languages`](https://github.com/Beep6581/RawTherapee/tree/dev/rtdata/languages)フォルダーの中に貴方が翻訳したい言語の翻訳ファイルがあるかどうか確認します。
    - ない場合は、[`English (US)`](https://github.com/Beep6581/RawTherapee/blob/dev/rtdata/languages/English%20(US))ファイルをダウンロードし（“Raw”ボタンを右クリックして、“リンクを保存します”を選択します）、翻訳する言語にファイル名を変更します-例えば、イヌクティトゥット語であれば、`Inuktitut`というように（以下もこれを例として使います）。
    - ある場合は、それをダウンロードします（“Raw”ボタンを右クリックして、“リンクを保存します”を選択します）。
2.  新しい文字列を翻訳する
      
    `Inuktitut`を最近のテキストエディターで開きます（Windowsユーザーは、テキストエディターに“Notepad”ではなく、Notepad++を入手して使います）。翻訳が必要な文字列には全て行の先頭に”！“マークが付いています。既に存在する翻訳ファイルの中の新しい文字列を翻訳する場合、それら文字列はファイルの末尾に置かれています。それらを翻訳した後、接頭語の”！“を削除します。

    先の例を使って説明すると、

    `!TP_EXPOSURE_EXPCOMP;Exposure compensation`

    という新しい文字列を

    `TP_EXPOSURE_EXPCOMP;Lorem ipsum`

    の様に翻訳し、“！”を外します。
3.  既存の文字列を更新する
      
    `Inuktitut`ファイルがかなり以前に翻訳されたものだと、その翻訳の一部が現状にそぐわないことがあります。それらを更新するには、最新の[`default`](https://github.com/Beep6581/RawTherapee/blob/dev/rtdata/languages/default)ファイルをテキストエディターの右側に開き、`Inuktitut`ファイルを左側に開きます、そして翻訳されている`Inuktitut`の各文字列を`default`の文字列と比べ、デフォルトの文字列と内容がそぐわないものを更新します。
4.  翻訳が終わったら、[GitHubの新規イシュー](https://github.com/Beep6581/RawTherapee/issues/new)を開き、その翻訳を添付します。その際に、翻訳部分だけを切り取って添付しないで下さい。更新した翻訳ファイル全体を添付します。それに対して、私たちが`/tools/generateTranslationDiffs`スクリプトを実行し、更新された文字列を整理し、新しいキーを追加し、古い文字列を削除します。そして、それをコードベースに記録します。
5.  将来、貴方が翻訳文を更新する際には、[`/rtdata/languages`](https://github.com/Beep6581/RawTherapee/tree/dev/rtdata/languages)に格納されている最新のファイルをダウンロードして下さい。

## マークアップ

　文字列の中には、太文字や斜体、特殊な形で表示される必要のある要素を持っているものがあります。それらは[マークアップ](https://en.wikipedia.org/wiki/Markup_language)を使って行われます。しかし、マークアップの構文解析は平文のそれに比べ若干遅くなります。そのため、RawTherapeeでは、それが必要と分かっているキーのマークアップだけをサポートします。従って、サポートされていないマークアップを使うとそれが正しく表示されません。常に`default`で使われている形式を守って下さい。`default`のキーにマークアップが無ければ、貴方の翻訳文にも使いません。

　キーがマークアップを使う場合は、特定の文字は
[HTMLの文字参照](https://en.wikipedia.org/wiki/List_of_XML_and_HTML_character_entity_references)名を使って書かれなければなりません:

- `<`は`<`と書きます;
- `>`は`>`と書きます;
- `&``&`と書きます;

　マークアップが何時必要なのかを知るには、`default`を見ます。例えば:

- `HISTORY_MSG_251;B&W – Algorithm`という文字列は＆を表示するためにマークアップを使っていますので、貴方が翻訳する時もマークアップを使います。
- `PARTIALPASTE_RAWCACORR_CAREDBLUE;CA red & blue`という文字列は＆を表示するためにマークアップは使っていないので、貴方の翻訳にも使いません。
- `FILEBROWSER_EMPTYTRASHHINT;`<b>`Permanently`</b>` delete all files in trash`は
  RawTherapeeで表示する時に"Permanently"
  が太文字になるようにマークアップを使っていますので、貴方の翻訳でも同じように使います。
