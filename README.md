# 職務経歴書
## 一覧
-  |分野      |時期      |会社      |
   |:---------|:---------|:---------|
   |Robotics  |2020〜2021|[Re-al](#アンカー1)|
   |AI        |2019〜2020|[リクルート派遣1:XXXXX](#アンカー2)|
   |AI-Robotics  |2019      |[XXXXX](#アンカー3)  |
   |Robotics  |2018〜2019|[リクルート派遣2:XXXXX](#アンカー4)|
   |FA        |2018      |[リクルート派遣3:XXXXX](#アンカー5)|
   |3D/AI     |2017〜2018|[リクルート派遣4:XXXXX](#アンカー6)|
   |CMOS Image Sensor Test     |2016〜2017|[インテリジェンス派遣:XXXXX](#アンカー7)|
   |アルバイト|2015〜2016|[日雇いetc](#アンカーZ)|
   |DRAM      |2008〜2014      |[エルピーダメモリ](#アンカー8)  |
   |ソフトウェア|2005〜2008|[XXXXX](#アンカー9)|
   |CAE       |2003〜2005|[XXXXX](#アンカー10)|
   |CAE       |2002〜2003|[XXXXX](#アンカー11)|

 <div id="アンカー1"></a>   

## リモート釣りロボットシステムの開発
### 東京都イベント向け釣りロボットシステムの開発、導入
- 対応技術
  - Webアプリによるロボット状態遷表示ツールの開発
  - Webアプリによる釣り釣歴/映像データ再生ツールの開発
  - データサーバの構築
  - リモート(VPNワイド)のネットワーク設計、デバイスのIP設定及び検査
  - 参考: https://www.youtube.com/watch?v=rJ-qyWjQkr0
  - ネットワーク検討IpV6光通信、5G、AWS
### バーチャル版釣りロボットシステムの開発
- 対応技術
  - Unity3D, PUN2
  - Unity<-> ロボットデバイス通信

 <div id="アンカー2"></a>   

## AI-NLP
### テキスト区間型タグ付け環境
- 対応技術
  - テキストアノテーションツール bratを元に改良。javascript/python/Git(auto commit)
  - DtaSetをオリジナルに作成
### テキストタグ付け環境と DNN 予測の連携
- 対応技術
  - transformer/pytorch,NFS,日本語BERTModel(京大)
  - 本技術により、自動でテキスト区間型タグ付けが可能(文章解析)

 <div id="アンカー3"></a>   

## AIソリューション
### 自動ピッキングロボットの開発
- 使用アーム
  - デンソーウェーブ製アーム
    -  6軸テーティングで操作可能だが、姿勢による特異点が多々あり、AI(画像認識)で目的位置自動にする際に不便だった。
- 対応技術
  - ハンド設計対応。モータを使用し、1軸制御でのワーク接触部回転制御機構(ベルトギア)を設計。FreeCADを使用。
  - AIプログラムであるMask-RCNNを常駐プログラムにする対応。tensor-flowを使用しているので初回起動にし、入力画像を与えると推論だけ行うように対応。
### 製薬工程自動化ロボット
- 使用アーム
  - デンソーウェーブ製アーム
    - モータ過負荷により、実証実験が途中で止まっていた原因をハンド部重量オーバーと特定
- 対応技術
  - ハンド軽量化対応。SUSで作成された重量ハンドをアルミ化(チタン化)。部分的な図面しかなく難航。

<div id="アンカー4"></a>

## ロボットハンドの開発
- 使用技術
&ensp; &ensp; 某大学ハプティクス研
- 対応領域
  - ソフトウェア(小型 PC: raspberry pi) :プログラム Python/C 接続: GPIO/UART/ USB
  - ソフトウェア(マイコン:esp32, stm32):プログラム C/C++ 接続: GPIO/UART/ SPI
  - ハードウェア(制御ボード) :マイコンとの繋ぎ配線
  - ネットワーク(IoT 向け): 小型デバイスのインタネット接続 UDP,TCP ネットワーク施策
    近距離の Wifi 接続や長距離の GlobalIP(IP 制限)での接続
- 対応機能
  - マスター/スレーブのバイラテラルコントロール
    - 汎用基盤をUSB(UART)経由でラズパイ(3B+)に繋いで、ラズパイ間の通信を行う。
      プログラムにPythonを使用したが1msecの通信間隔で得られず遅くて断念。その後はC言語版を流用。
  - 多軸アーム構成での重力保障
    - 鉛直方向とのモータ回転軸が異なる軸を対象。医療系7軸ロボットに対し、鉛直方向の角度成分を持つ1軸に2軸分の角度成分を合成し、A*Cos(θ1-θ2)キャンセル入力実装: Aは特定角度での測定値。
  - 経路計画
    - 医療系7軸ロボットに対し、各設定を行う際に各軸可動域を手動確認。プログラム制御もできたが、実物ストッパーあり。
  - 慣性モーメントの設定、ゲインチューニング(位置、速度)
    - 基本のゲインチューニングは某社モータドライバ付属のソフトでモータ設定行ってオートチューニング。そこから位置固定がオーバシュートしないところでで手動設定。慣性モーメントは設計値では設定できず、暴シーソー状態になるので、低め設定で感度が落ち着くところを手動設定。
  - 汎用ボード内通信検証(制御周期の確認含む) 
    - オシロスコープ(電圧確認やタイミング解析)やプロトコルアナライザ(SPI)を使用。
    - UART変換にはFTDI High Speed を使用。
    - 内部のUART/SPI のプロトコルは独自であり、SDK(部分的に修正の上)使用。
  - UI(ポテトチップ掴みハンド)
    -  ラズパイ(3B+)用タッチパネルディスプレーを用いて、PySideでプログラムし、バイラテスタート、停止、記録、再生を行うUI+デモ用制御プログラムを作成。 

 <div id="アンカー5"></a>   

## FA
### 液晶テレビの検査
- 使用技術
  - 画像処理(某社専用ライブラリを使用)
- 対応技術
  - C#, MELSEC-Q, CC-Link, modbus(pymodbus→C#への書き換え), Giga-E

 <div id="アンカー6"></a>   

## 某社横浜研究所 
### AIシステムの信頼性評価手法の開発
- 使用ツール
  - TensorFlow/Keras/Chainer, OpenCV, Python, SKLearn, Numpy
- 対応技術
  - Adversarial Examples 
- 使用サンプル
  - mnist, 交通道路標識
### 3Dセンサーの精度検証技術の開発
- 使用ツール
  - FreeCAD, Python, Gocator
- 対応技術
  - FreeCAD改良

 <div id="アンカー7"></a>   

## 半導体チップのテスト工程
### CMOSイメージセンサ検証向けソフトウェア開発
- 使用技術
  - 画像処理(点欠陥、線欠陥、ベイヤー配列でコンボルーションなど使用)
- 対応技術
  - TeraDyne製半導体テスタ向けのテスト自動化に関するソフトウェアを開発
  - ExcelVBA, .NET basic, C#, IG-XL 

 <div id="アンカー6"></a>   

## DRAM開発(半導体メーカー)
### 10年保障向け検証系ソフトウェアの開発(社内専用)
- 使用技術
  - Hpsice, Hsim, SmartSpice, BSIM4, 劣化モデル
- 対応技術
  - トランジスタのホットキャリア経年劣化を過渡解析(SPICE)で10年後の回路動作を検証できるシステムの開発。実測（DC寿命）に基づく換算式をBSIM4などのTrモデルコードに直接実装。
  - C++, Spiceベンダーの開発元USAのメンバと共同開発, Exceed, Red Hat Enterprise Linux

### 回路レイアウト(配線)の検証系ソフトウェアの開発(内製ソフト)
- 使用技術
  - Virtuoso System Design Platform,Star-RCXT, CalibreDRC
- 対応技術
  - タングステン乗り換え配線チェッカーの開発。ツール名WINET。チップ内の回路の配線分岐をツリー構造とみなして検索を行う大規模データ解析。配線抵抗は実負荷ツールにより抽出。GUIはVirtuoso上での結果表示。2014年はMicron社との統合で本システムをMicron社設計環境へ移植。テキサス及びアイダホのマネージャーと連携。　
  - C++, マルチCPU(2CPUjob*32), GPGPU(再帰処理のため未使用), Exceed, Red Hat Enterprise Linux

### 回路レイアウト(配線)の検証系ソフトウェアの開発(内製ソフト)
- 使用技術
  - Virtuoso System Design Platform,Star-RCXT, CalibreDRC
- 対応技術
  - 半導体配線の劣化要因のエレクトロマイグレーションの電流密度レイアウト検証システムの開発。　
  - C++, マルチCPU(2CPUjob*32), GPGPU(再帰処理のため未使用), Exceed, Red Hat Enterprise Linux

### TCADソフトウェア運用
- 使用技術
  - Sentaurus(プロセスシミュレータ/ デバイスシミュレータ)
- 対応技術
  - 新デバイス向け(PRAM)や新機能(量子効果関連)により新たに解析可能となった事例の社内への展開、サポート。
  - 実験計画法
- 特許出願
  - 特開2012-164038

<div id="アンカー9"></a>   

## ソフトウェア開発
### CAE地震波強度解析システムGUI開発
- 対応技術
  - GiD(CAD,CAE), Tcl/Tk及びCAEソルバーとの互換部分はC++
### ASIC・FPGA設計向けC言語ベース高位合成ツールの開発
- 開発ツール
  - CyberWorkBench(Cベース)
- 対応技術
  - 高位論理合成ツールの開発言語もC言語
  - Qt, veilogHDL/VHDL

<div id="アンカー10"></a>   

## CAE
### 衝突安全性能をCAEで評価
- 開発車種
  - 2006年リリースMove
- 対応技術
  - LS-DYNA, トヨタ内製CAD, 材料力学, 衝突安全ボディ, 有限要素法, NEC SX、, Octane2 WS

<div id="アンカー11"></a>   

## CAE
### 3DCAD/CAE
- 対応技術
  - 衝突/強度向け3Dモデリング、, トヨタ内製CAD, ANSA

<div id="アンカーZ"></a>   

## アルバイト(日雇いetc)
- アマゾン倉庫内ピッキング(服)、ドラッグストア倉庫内ピッキング(ドリンク、洗剤)、冷凍倉庫内ピッキング(冬季、練り製品)、地盤改良工事（設計、工事アシスト）、杜仲茶(栽培、産業機器を使用して乾燥加工)、東京電力コールセンター、配膳人(東京會舘、フレンチ)

## 学歴
信州大学理学部物理学科卒業(2002)



