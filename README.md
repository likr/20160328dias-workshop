# 第4回DIAS利用ワークショップ - 大気海洋データの可視化と活用

ご自身のパソコンを持込んで、海洋3次元時系列データと漁獲量データを使った好適生息域推定モデルの構築を題材に、DIAS上の大気海洋データの可視化と活用方法の演習を行います。これは陸上の動植物の好適環境推定モデリング等、大規模大気海洋データと生態系データや社会データを組み合わせた様々な空間モデルの構築にも応用できます。

## タイムテーブル

| 時間 | 内容 |
|---|---|
| 10:00〜 | オープニング |
| 10:10〜 | データセットの説明 |
| 10:20〜 | ハンズオン前半 |
| 11:00〜 | ハンズオン後半 |
| 11:30〜 | ディスカッション |
| 11:55〜 | クロージング |
| 12:00 | 終了 |

## 準備

Google Chromeが必須です。
インストールされていない方は以下のURLからダウンロードしてください。
https://www.google.co.jp/chrome/browser/desktop/index.html

# データセットカタログ

以下のURLからデータセットカタログにアクセスできます。
http://dias-tb2.tkl.iis.u-tokyo.ac.jp:10080/thredds/
ログイン情報は別途お知らせします。

MOVE-RA2014、FORA、CDAの3種類のデータセットを用意しています。
MOVE-RA2014は一つのデータセット、FORAとCDAは複数のデータセットから構成されています。
データセットはディレクトリ構造になっていて、カタログ画面で探索できます。

![fig01.png](https://likr.github.io/20160328dias-workshop/figs/fig01.png "fig01.png")

データセットを選ぶと以下のような画面が開きます。
AccessのOPeNDAPのリンクに移動してください。

![fig02.png](https://likr.github.io/20160328dias-workshop/figs/fig02.png "fig02.png")

以下のようなデータセット表示画面が開きます。
ここでは、データのメタ情報を確認することができます。
メタ情報は[CF Conventions](http://cfconventions.org/)に基づき登録されています。

![fig03.png](https://likr.github.io/20160328dias-workshop/figs/fig03.png "fig03.png")

# 大気海洋データの可視化 - OPeNDAP Viewerの利用

[OPeNDAP Viewer](http://likr.github.io/opendap-viewer/)を使ってデータセットカタログ中のデータを可視化します。

OPeNDAP Viewerにアクセスすると以下のような画面になります。
URL欄にデータセットカタログの「Data URL」に記載されているURLを入力し、「Load dataset」ボタンを押すとデータセットの情報が読み込まれます。

![fig04.png](https://likr.github.io/20160328dias-workshop/figs/fig04.png "fig04.png")

Controlメニューはタイトル部分をドラッグすることで移動できます。

## データ取得範囲の設定

OPeNDAP Viewerでは、データの全てをダウンロードすることなく、必要な部分だけをサーバーから取得し可視化することができます。
リストから可視化した変数を選び、経度、緯度、深さ(または気圧座標などの高さ情報)、時間の軸の取得範囲を選択します。
データセットや変数によっては、深さや時間が省略されている場合もあります。

![fig05.png](https://likr.github.io/20160328dias-workshop/figs/fig05.png "fig05.png")

取得範囲は添え字で指定しますが、「▼」ボタンを押すと軸の値で選択することができます。
取得範囲の形式は「開始添え字:ステップ:終了添え字」です。
OPeNDAP Viewerでは、時間は1時点だけを使用します。

![fig06.png](https://likr.github.io/20160328dias-workshop/figs/fig06.png "fig06.png")

## 可視化結果の表示

リスト右側のボタンから可視化方法を選択します。
コンター図(XY断面、XZ断面、YZ断面)と等値面の4種類があります。
ボタンを押し、不透明度を設定すると可視化結果が表示されます。

![fig07.png](https://likr.github.io/20160328dias-workshop/figs/fig07.png "fig07.png")

![fig11.png](https://likr.github.io/20160328dias-workshop/figs/fig11.png "fig11.png")

## カメラの設定

画面をドラッグすると地図を回転させることができます。
マウススクロールは地図のズームに対応しています。

ControlメニューのCameraタブで地図の中心座標を移動できます。
例えば、日本周辺を見る場合は緯度(Lat)40、経度(Lon)140に設定します。

![fig08.png](https://likr.github.io/20160328dias-workshop/figs/fig08.png "fig08.png")

![fig09.png](https://likr.github.io/20160328dias-workshop/figs/fig09.png "fig09.png")

## オブジェクトの表示・非表示

ControlメニューのObjectタブで、生成したオブジェクト(可視化結果)の表示・非表示を切り替えることができます。
チェックボックスのチェックを外すとオブジェクトが非表示になり、再度チェックを入れると再表示されます。

![fig10.png](https://likr.github.io/20160328dias-workshop/figs/fig10.png "fig10.png")

# 海洋データによる生態系モデリング

[HSIモデリングシステム](http://likr.github.io/web-squid/public/)を利用して、海洋データと漁獲データを用いた生態系モデリングを行います。
はじめに、テスト用データ[dummy.csv](https://www.dropbox.com/s/vtokhxptjep066f/dummy.csv?dl=0)をダウンロードしてコンピュータに保存してください。
dummy.csvには、2006年1月10日から19日までの10日分のダミー漁獲情報が保存されています。

HSIモデリングシステムにアクセスすると以下のような画面が表示されます。
「CPUE File」欄に、保存したdummy.csvを選択し、「Start」ボタンを押します。

![fig12.png](https://likr.github.io/20160328dias-workshop/figs/fig12.png "fig12.png")

SIモデル作成画面に切り替わりました。
「Variable Distribution」には環境変数場のコンター図が、「SI Map」には環境変数をSI関数に通したSI値のマップが表示されています。
マップには、その日漁獲のあった点も表示されています。
「Correlation Graph」には、環境変数とSI値の深さ毎の相関を表示しています。
「Scatter Plot Graph」には、平滑化スプラインによるSI関数の形状を表示しています。

環境変数、深さ、平滑化パラメータを操作することで、モデルに採用するSI関数の作成を目指します。
良さそうなSI関数ができたら、「Save SI」ボタンを押してSI関数をHSIモデルに組み込みます。

![fig14.png](https://likr.github.io/20160328dias-workshop/figs/fig14.png "fig14.png")

地図には1日分の環境場のみが表示されています。
「Target Date」を変更することで異なる日付の環境場を表示することができます。

![fig13.png](https://likr.github.io/20160328dias-workshop/figs/fig13.png "fig13.png")

「HSI」タブに移ると、これまで保存したSI関数から構築されたHSIモデルが表示されています。

![fig15.png](https://likr.github.io/20160328dias-workshop/figs/fig15.png "fig15.png")
