To pass this exercise write a module that takes a two or four-letter
_(hyphenated)_ language specifier from the `process.env.LANG`  environment
variable to respond with a greeting to a person with his name in the
appropriate language.
この課題では、名前を入力すると適切な言語で挨拶を返すモジュールを作成します。
適切な言語を判定する為には、環境変数 `process.env.LANG` から2つまたは4つの言語指定子を取得して判断します。

```javascript
module.exports = function greet (name) {
    return // your code
}
```

For example: If your module is called like `greet("Michael")` and the
environment variable contains `process.env.LANG === 'ja-jp'` then it should
return `こんにちは、Michaelさん！`.
例：もし今回のモジュールに対して `greet("Michael")` のような関数が呼び出された時、`process.env.LANG === 'ja-jp'` が真であれば `こんにちは、Michaelさん！` と返さなければなりません。

The following file contains greetings in all the languages you need:
以下のファイルには、およそ必要とされる複数の言語での挨拶文が定義されています:

    {rootdir}/data/hello.json

Translations in the file will have a placeholder specified as `%s` which can
be used to personalize the greeting.
ファイル内の訳語には、必ず `%s` という文字列が含まれており、それを置換することで挨拶の対象を指定します。


---

## Hints
## ヒント

To load a `.json` file you can simply require it:
`.json` ファイルを読み取りたい場合は、単純に `require` を用いる事ができます:

```javascript
var data = require(filePath)
```

---

You are free replace the String in any way you want, but Node.js's `util.format`
method might come in handy.
好きな方法で文字列を置換することは出来ますが、Node.jsが持つ `util.format` 関数が役に立つかもしれません。

---

ISO standardised language codes under the [ISO 639] system. In this exercise
we use two-letter [ISO 639-1] language codes. At the moment only 184 languages
are specified this means that very minor languages are not covered by
this standard. In practice that is almost never a problem.
In the ISO 639 specification `de` stands for german, `en` for english, etc.

言語指定子はISOによって[ISO 639]として定義されています。
この課題では、アルファベット2文字による言語指定子の定義である[ISO 639-1]を使用します。
[ISO 639]には184の言語が定義されていますが、現代において主要でない言語は定義されていません。
しかし、それが問題になることはほぼ無いと言って良いでしょう。
[ISO 639]規格では、 `de` はドイツ語、 `en` は英語などというように定義されています。

Lets be more specific! The language codes can come with [ISO 3166-1]
two-letter country code attached. `de-at` stands for
_"german language used in austria"_ or `zh-tw` for _"chinese language used
in taiwan"_.

実例を示しましょう。往々にして、先述の言語指定子を含む変数には[ISO 3166-1]で定義されているアルファベット2文字の国コードが添えられている事があります。
これは、いわゆる方言を考慮したものです。
例えば `de-at` であれば、それは「オーストリア(at)で使用されているドイツ語(de)」を意味し、
`zh-tw` であれば、それは「台湾(tw)で使用されている中国語(zh)」を意味します。

_Side Note:_ Beside those common occuring combinations, in your project it
might also make sense to have uncommon combinations. `en-jp` could stand
for "english language used in japan" which does have a few special
expression!

補足：実例のような一般的な組み合わせだけでなく、一般的でない組み合わせの場合もあることに留意しましょう。
例えば、`en-jp` であれば「日本(jp)で使用されている英語(en)」であり、これは数の少ない特別な例であると言えるでしょう。

---

The provided file contains all the languages you will need. However, the language code might sometimes be for a local variation that is not an exact fit: i.e. we only have a greeting for "ja" but you might be asked for "ja-jp". You will have to fall back to the two-letter language code if the combination is not available.

提供されている定義ファイルには、本課題でテストを行うすべての言語が定義されています。
しかし、言語指定子には往々にして曖昧なものが存在します。
例えば定義ファイルには `ja` のみを対象とした挨拶文が定義されていますが、入力が `ja-jp` である可能性があります。
もしそのような言語指定子が入力された場合には、次善の言語指定子としてアルファベット2文字の `ja` とみなす必要があります。

[ISO 639]: https://ja.wikipedia.org/wiki/ISO_639
[ISO 639-1]: https://ja.wikipedia.org/wiki/ISO_639-1
[ISO 3166-1]: https://ja.wikipedia.org/wiki/ISO_3166-1