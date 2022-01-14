# fontawesome6-icon-picker
Font Awesome6に対応したアイコンピッカー
![image](https://user-images.githubusercontent.com/52589133/149440263-d4b53ff5-52cc-48d9-87d0-f55468a63ec0.png)
# LISENCE
# Demo
https://marioninc.github.io/fontawesome6-icon-picker/demo.html

# How to Use 使い方

1. Githubからクローンもしくはダウンロード
3. /js/fontawesome6-icon-picker.jsを適当な場所に配置
4. HTMLで読み込む 例）`<script src="./js/fontawesome6-icon-picker.js"></script>`
5. 依存関係に必要なファイルを読み込む. ローカルでもCDNでも可
6. インスタンスを起動 例）`fa6picker = new Fa6IconPicker({targetInput : document.querySelector('input[name=icon_input]')})`;

## 依存関係

* bootstrap 5.x (popover bandle版）
* Font Awesome 6

# Options 設定
| パラメータ名（param name） | 初期値（default） | 説明（detail）|
| --- | --- | --- |
| title | `null` | `String` PopOverの上部に表示されるタイトル. `null`の場合は非表示. |
| targetInput | `null` | `Element` `必須` icon名（Font Awesomeで指定するClass情報）を渡す対象のinput Element. targetInput.value に値が渡されるため、inputでなくてもよい. |
| targetViewIcon | `null` | `Element` 選択されたアイコンをプレビューするElement. 対象のElementは、classを初期化するため任意でclassを指定しないでください. |
| popoverElement | targetInput | `Element` popoverを発生させる基準位置となるElement. 未設定の場合はtargetInputがコピーされます. |
| targetCssName | `"all.min.css"` | `String` `必須` Font AwesomeのCSSファイル名を指定します. 未設定の場合は`"all.min.css"`です. 例）`['fa-a','fa-b']`|
| enableIcons | `[]` | `Array` 有効なアイコンを指定できます。指定したものだけを表示します. 未設定の場合は全てを表示します. 例）`['fa-a','fa-b']` |
| disableIcons | `[]` | `Array` 無効なアイコンを指定できます. enableIconsと併用できdisableIconsが優先です. 例）`['fa-a','fa-b']` |
| isTargetInputClickEvent | `true` | `bool` targetInputをクリックしたときにpopoverが表示されるイベントを作成するか. |
| showBtnElement | `null` | `Element` targetInputと別に、クリックしたときにpopoverを表示するElementを指定できます.  |
| popoverOptions | `{ placement: 'bottom' }` | `Object` bootstrap popoverに与えるオプションを指定できます. 詳細は[bootstrapのDocument](https://getbootstrap.jp/docs/5.0/components/popovers/#options)をご覧ください. |
| maxWidth | `"320px"` | `String` popoverの最大幅です. アイコンの数が少ない場合を除き、最大幅 == 実際の幅 になります. |
| extProps | `{}` | `Object` 任意の変数です. constructorの引数にオプションにないものが渡された場合ここに格納されます. extPropsを指定して渡す必要はありません. |

### Options Default
```js
var option = {
    title = null; // title popoverに渡されるタイトル
    targetInput = null; // 結果を返すinput要素
    targetViewIcon = null; // アイコンのプレビューを渡す要素
    popoverElement = null; // popoverする要素
    targetCssName = "all.min.css"; // 解析するCSS名
    enableIcons = []; // ホワイトリスト
    disableIcons = []; // ブラックリスト
    isTargetInputClickEvent = true; // 結果を返すinputにイベントを与えるかどうか
    showBtnElement = null; // 結果を返すinputのほかにクリックしてpopoverを表示させる要素
    popoverOptions = { // popoverのオプション bootstrapに依存
        placement: 'bottom',
    };
    maxWidth = '320px'; // popoverの最大幅
    extProps = {}; // 任意に追加された変数
}
```

オプションは`create()`を実行するまでは直接変更可能です.  
`create()`実行後は変更しても一部の設定は適用されません.

# Methods
### constructor (settings)
param `Object` settings  起動時に指定するオプション  
  
`settings`にオプションを指定してインスタンスを起動します.  
`settings`に`targetInput`が含まれる場合、`create()が自動的に実行されます.`

### create ()
インスタンス起動時に、
`settings`に`targetInput`が含まれなかった場合、任意のオプションを指定してから、`create()`を実行してください.  
すでに`create()`されている、ピッカーを再描画したい場合は、一度`dispose()`を実行してから再度`create()`を実行してください.  

### search (key_word)
param `String` key_word  アイコンを絞り込むワード  
`search (key_word)`を実行するとアイコン名でアイコンを絞り込むことが出来ます.  
popover内の検索ボックスに文字列を入力すると、`search (key_word)`が実行されます.  

### show ()
popoverを表示します.  

### hide ()
popoverを隠します.  

### toggle ()
popoverが表示されているときは隠し、隠れているときは表示させます.  

### dispose ()
iconpickerを終了します.  
すでに`create()`されている、iconpickerを再描画したいときは`dispose ()`を先に実行してください.  

# Callbacks
未実装.
