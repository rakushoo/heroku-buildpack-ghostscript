## 目的
Music21をHeroku環境で動作させるために必要な、
Ghostscriptのv9.21をインストールするbuildpackです。

## 詳細
Music21をHeroku環境で動作させるためには、  
LilyPondとGhostscriptが必要になります。

LilyPond(2.20.0)はbuildpackからインストールします。  
LilyPond内のgsバイナリはv9.26なのですが、なぜかgs_init.psに対してリビジョン不一致のエラーが出ていました。  
> Invoking `gs -dSAFER -dEPSCrop -dGraphicsAlphaBits=4 -dTextAlphaBits=4 -dNOPAUSE -dBATCH -sDEVICE=png16m -sOutputFile=test.png -r101 -ftest.eps'...
> gs: Interpreter revision (926) does not match gs_init.ps revision (921).

そのため、このbuildpackではgsのインストールに加えて、LilyPond内のgsファイルを置き換える処理をしています。
事前にLilyPondがインストールされている前提で動作するのでご注意ください。
