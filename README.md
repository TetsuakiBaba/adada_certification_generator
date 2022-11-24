# ADADAのCertification関連を生成するためのpythonスクリプト
データの本体は馬場にご連絡ください。github上にはこのREADME.mdしか上げていません。

基本的な流れは以下の通り。
1. pythonの必要なモジュールを入れた環境をanacondaで構築しておく
2. 各ディレクトリに置かれている makeCertification.py を実行する。
   - 注）各makeCertificationでは同じディレクトリ内にあるlist.xlsxファイルを参照して生成されますので、必要に応じてそちらを修正してください。それ以外の箇所については template.ai、またはtemplate.pdfを直接編集し、ふさわしい template.png を作成しておいてくだし。makeCertifcation.py はtemplate.pngを背景画像として証明証を生成します。年度ごとに変わる署名等はそちらで対応してください。
3. pdfs/ というディレクトリに生成されたpdfファイルを利用する

## 環境構築
macOSを例に記述します。
1. anacondaを（インストールしていなければ）インストールする。
   - 私の場合は [miniforge](https://github.com/conda-forge/miniforge) をインストールしましたが、なんでもよいです。
2. ターミナルから仮想環境を作る。今回は adada_certification という名前で記述しています。
   - conda create -n adada_certification python=3.9
   - conda activate adada_certification
   - conda install pandas
   - conda install pillow
   - conda install reportlab
   - conda install openpyxl

## 証明書の生成方法
生成したい各ディレクトリ（Appreciation：招待講演者証明書、Commondation：ベストペーパー等の受賞証明証、Participation：参加証、Receipt：レジストレーション費用支払の領収書）において、以下のコマンドを実行する。なおpython実行の際は上記で作成したanaconda環境であることが必要
```
python makeCertification.py
```  
実行後同じディレクトリ内にある pdfs/ ディレクトリに生成されえたファイルが保存されている。

## カスタマイズ
各フォルダにある makeCertification.py を適時修正してください。簡単なコメントをいれています。また、賞状フォーマットについては、template.png というファイルを読み込んでその上にテキストを載せています。template.png 自体の修正を行う場合は、 template.ai がありますのでそちらを修正したのち、template.png に書き出してください。なおpngの保存形式は横幅4000pxとしています。