# RecollectionModeMZ

## 概要

アドベンチャーゲーム等でよく見られる「シーン回想」や「CG閲覧」といった  
いわゆる「回想モード」機能を追加するプラグインです。
ツクールMZ対応版を作成しました。


## スクリーンショット

* タイトル画面へのメニューの追加

![スクリーンショット-タイトル](http://www.rinsymbol.sakura.ne.jp/tkool/mz/github_images/recollection00.png)


* 「回想モード」の表示

![スクリーンショット](http://www.rinsymbol.sakura.ne.jp/tkool/mz/github_images/recollection0.png)


* 閲覧する回想を選択

![スクリーンショット](http://www.rinsymbol.sakura.ne.jp/tkool/mz/github_images/recollection_mode.png)

## デモ（音がなります。ご注意ください）

[RecollectionModeMZ](http://www.rinsymbol.sakura.ne.jp/tkool/mz/RecollectionModeMZ/)


### ライセンスについて

このプラグインはMITライセンスのもとで公開されています。
詳細については、LICENSE.txtをご覧ください。


## 利用について

非商用/商用ゲーム問わずにご利用いただけます。
年齢制限のあるコンテンツでのご利用も可能です。
利用報告は必要ありません。
自由に使ってあげてください。


## サンプルプロジェクトについて

このリポジトリ自体がサンプルプロジェクトとなっております。  
Githubの右上付近にある[Code] ->[Download ZIP]より、ファイルをダウンロードして、RPGツクールMZで開いてください。


## 使い方

1. RecollectionModeMZ/js/plugins/RecollectionModeMZ.jsをダウンロードし、```ツクールプロジェクト/js/plugins/```に配置します
→このファイルがプラグイン本体です。
2. RecollectionModeMZ/img/system/RecollectionModeMZData.jsonをダウンロードし、```ツクールプロジェクト/img/system/```に配置します
→このファイルは回想情報を定義するファイルです。

3. プラグイン管理で、RecollectionModeMZ.jsを有効にします
   * 下記画像のようにプラグインを有効にします  
      ![スクリーンショット](http://www.rinsymbol.sakura.ne.jp/tkool/mz/github_images/recollection_mode_plugin_manage.png)

4. ```ツクールプロジェクト/img/pictures/``` に対して、画像ファイルを配置します
   * 以下のリンクの画像を保存し、上記ディレクトリに配置します。   
     [never_watch_picture.png](http://www.rinsymbol.sakura.ne.jp/tkool/mv/github_images/never_watch_picture.png)
   * 加えて、回想モードに利用する画像を用意し、配置します
ここでは、```a.png```と```b.png```を配置したものとします

5.  ```ツクールプロジェクト/audio/bgm``` に対して、音楽ファイルを配置します  
    * 以下のリンクの音楽を保存し、上記BGMディレクトリに配置します。  
     [blank_memories.ogg](http://www.rinsymbol.sakura.ne.jp/tkool/mv/github_images/blank_memories.ogg)

6. RecollectionModeMZData.jsonに対して、以下の設定を行います
   * ```ツクールプロジェクト/js/plugins/RecollectionModeMZData.json```の4行目のpicturesに、先ほど配置した画像の指定を行います(.pngの拡張子は省略してください)
   ```javascript
   "pictures": ["a", "b"],
   ```
   * thumbnailに、回想一覧のサムネイルを指定します。
   ```javascript
   "thumbnail": ["t"],
   ```
7. 回想イベントとして呼び出す「コモンイベント」の番号を指定します
   * common_event_idに1を指定します
   ```javascript
   "common_event_id": 1,
   ```

8. 回想が見れるようになる条件(スイッチ)を指定します
   * switch_idに1を指定します  
   (※自由なスイッチ番号が指定できます。コモンイベント番号と一致している必要はありません)
   ```javascript
   "switch_id": 1
   ```

9. 回想用のマップを設定します
   * プラグインパラメータの「回想用一時マップID」で何もないマップのIDを指定します（デフォルトは1になっています）
   ![スクリーンショット](http://www.rinsymbol.sakura.ne.jp/tkool/mz/github_images/reco_sandbox_map_setting.png)
   
   * [新規プロジェクトを利用する場合]
        * プロジェクト作成時に存在する「MAP001」の内容を以下のようにクリアします
            * 設定前
            ![スクリーンショット](http://www.rinsymbol.sakura.ne.jp/tkool/mz/github_images/recollection_mode_before.png)
            * 設定後
            ![スクリーンショット](http://www.rinsymbol.sakura.ne.jp/tkool/mz/github_images/recollection_mode_after.png)
   * [既存プロジェクトを利用する場合]
        * マップを新規作成します
        * 作成されたマップIDを確認します
        * プラグインパラメータの「回想用一時マップID」で対象のマップIDを指定します

10. [7]で指定したコモンイベントを作成します
    * 下記画像のようにコモンイベントの1番目に、回想用イベントを作成します。ここではa.pngとb.pngを画面に表示します
    ![スクリーンショット](http://www.rinsymbol.sakura.ne.jp/tkool/mz/github_images/recollection_mode_exp_common_event.png)

    * 【！重要！】回想用のコモンイベントの一番最後の行に、「プラグインコマンド」として下記のコマンド「回想に戻る」を指定します
    ![スクリーンショット](http://www.rinsymbol.sakura.ne.jp/tkool/mz/github_images/recollection_mode_plugin_add_script.png)

11. [8]で指定したスイッチをONにするイベントを作成します
    * 新たにマップを作成し、下記画像のようにイベントを作成します
      ![スクリーンショット](http://www.rinsymbol.sakura.ne.jp/tkool/mz/github_images/recollection_mode_exp_switch_on.png)
    * 設定後のマップイメージ
      ![スクリーンショット](http://www.rinsymbol.sakura.ne.jp/tkool/mz/github_images/recollection_mode_map002.png)      

12. ゲームを起動します。[11]で作成したイベントと会話し、ゲームを「セーブ」してタイトル画面に戻ります。
    すると、CGと回想が見れる状態となります。


## 回想情報設定ファイル説明（RecollectionModeMZData.json）

回想情報ファイルはjson形式で記述します。

```json
[
    {
        "title": "回想シーン1",
        "pictures": ["a", "b"],
        "common_event_id": 1,
        "switch_id": 1,
        "thumbnail": "t"
    }
]
```

|項目名|項目内容|
|---|---|
|title|回想シーンのタイトルを指定します|
|pictures|CGモードに表示する画像を指定します。[img/pictures]配下の画像を指定します。後述のthumbnailプロパティを指定しない場合はpicturesの先頭に指定した画像がサムネイルになります。|
|common_event_id|回想シーン選択時に呼び出すコモンイベントのIDを指定します|
|switch_id|回想シーンが表示されるための条件スイッチIDを指定します。該当のスイッチがONになった場合に回想が見れるようになります。|
|thumbnail|サムネイル画像を指定します。[img/pictures]配下の画像を指定します。|


## パラメータ説明

プラグインの設定から各種動作に関する設定を実施することができます。

### 回想モードBGM設定

|項目名|項目内容|
|---|---|
|BGMファイル名|回想シーンで再生するBGMを指定します|
|BGMの位相|BGMの再生位置（左右）を指定します|
|BGMのピッチ|BGMの再生速度を指定します|
|BGMの音量|BGMの再生ボリュームを指定します|

### 回想・CG選択設定

|項目名|項目内容|
|---|---|
|x座標|回想CG選択ウィンドウのx座標を指定します|
|y座標|回想CG選択ウィンドウのy座標を指定します|
|回想メニュー名|回想モード自体の表示名を指定します|
|回想の選択肢名|「回想を見る」メニューの表示名を指定します|
|CGの選択肢名|「CGを見る」メニューの表示名を指定します|
|タイトルに戻る選択肢名|「タイトルに戻る」メニューの表示名を指定します|


### 回想リストウィンドウの設定

|項目名|項目内容|
|---|---|
|1画面あたりの列数|回想選択において、1ページ内の項目数(列数)を指定します|
|1画面あたりの行数|回想選択において、1ページ内の項目数(行数)を指定します|
|CG説明テキストの表示有無|回想選択において、回想の説明テキストを表示有無を指定します(true: 表示する, false:表示しない)|
|CG説明テキストの表示位置|回想の説明テキストの位置を指定します。(left:左寄せ、center:中央、right:右寄せ）|
|未開放のときに表示する画像|閲覧したことのないCGの場合に表示するピクチャファイル名を指定します|
|未開放のときに表示するテキスト|閲覧したことのないCGの説明テキストとして表示する文字を指定します|

### その他設定

|項目名|項目内容|
|---|---|
|回想用一時マップID|回想表示用のマップIDを指定します。通常は何もないマップIDを指定します。|
|回想情報ファイル|回想情報を定義したファイル名(RecollectionModeMZData.json)を指定します。ファイルの配置先は```img/system/```です|
|起動時の開発者ツールの表示有無|デスクトップ版において、ゲーム起動時に開発者ツールも一緒に起動するかどうかを指定します。(true:起動する, false:起動しない)|


### FAQ

* Q01.エラーについて TypeError Cannot read property 'forEach' of null　こんなエラーが発生して動きません
    
   回想情報ファイル(RecollectionModeMZData.json)の一番最後の}(波括弧)のあとに、,(カンマ)が指定されている可能性があります。もしくは回想情報ファイルのJSONが適切でない場合があります。サンプルファイルをご確認ください。


### 作者について

[@rinne_grid](https://twitter.com/rinne_grid)

