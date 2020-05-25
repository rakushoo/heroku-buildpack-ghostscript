# 目的
Music21をHeroku環境で動作させるために必要な、
Ghostscriptのv9.21をインストールするbuildpackです。

# 注意
Music21をHeroku環境で動作させるためには、  
LilyPondとGhostscriptが必要になります。

LilyPond(2.20.0)はbuildpackからインストールします。  
LilyPond内のgsバイナリはv9.26なのですが、なぜかgs_init.psに対してリビジョン不一致のエラーが出ていました。  
> Invoking `gs -dSAFER -dEPSCrop -dGraphicsAlphaBits=4 -dTextAlphaBits=4 -dNOPAUSE -dBATCH -sDEVICE=png16m -sOutputFile=test.png -r101 -ftest.eps'...  
> gs: Interpreter revision (926) does not match gs_init.ps revision (921).

そのため、このbuildpackではgsのインストールに加えて、LilyPond内のgsファイルを置き換える処理をしています。
事前にLilyPondがインストールされている前提で動作するのでご注意ください。

# 使用方法
Step 1: Heroku Dashboard -> (App name) -> Settings -> Buildpacks の Add buildpack を押下してリポジトリを追加  
Step 2: コマンドラインから環境変数を追加  
$> heroku config:add BUILDPACK_URL=https://github.com/rakushoo/heroku-buildpack-ghostscript.git
