# やあ　こんばんわ
ということで本日はLaravelのRouting機能を覚えたよ

ひとまずは理解できたと思う

## 特定のアドレスにアクセスしたら紐付けられた処理をおこうなう

的な

くっそ簡単にね

```PHP
Route::controller(NewsController::class)->prefix('admin')->name('news.')->group(function(){
    Route::get('news/create', 'add')->name('add');
});
```

こんな感じでやるんだって(適当).


## まあ簡単に

```PHP
Route::get(アドレス　、関数やら);
```
getの静的メソッドで設定　今回はControllerで関数を指定するよ

# なぜgroup化するのか

間に挟まれてる prefix('admin') と無名関数君の中の全てのRoutingに適用させたいからです

## prefix('admin')とは

無名関数の中のURLをhttp://XXXX.jp/ **admin** /　から始まるURLに変えてるだけ

ちなみにadminを書き換えれば好きな文字に変えれます

## name('news.')とは

名前付きルートの紐付けです。名前つけりゃあとで名前で呼べます。

## 最後にRoute::get('news/create', 'add')とは

http://XXXX.jp/admin/news/create にアクセスが来たら、

**Admin\NewsControllerのAction addに渡す** という設定をしています。

とても複雑なことをしていますね。(笑)

ちなみにこっちにも　name('add')　としていることで　Route::get('news/create', 'add');　に対して　add　という名前で紐付けをできます

なので**http\://XXXXXX.jp/admin/news/create**はnews.addと指定することもできます。便利だね


実はこれと同じ設定はgroupを使用しなくても次のように書くこともできるからです。(小声)

```PHP
Route::get('admin/news/create', [NewsController::class, 'add']);
```

以上！本日3月1日でした！
