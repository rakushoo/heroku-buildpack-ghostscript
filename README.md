## 目的
Music21をHeroku環境で動作させるために必要な、
Ghostscriptのv9.21をインストールするbuildpackです。

## 詳細
Music21をHeroku環境で動作させるため、  
LilyPondとあわせてインストールが必要になります。

LilyPond(2.20.0)内のgsバイナリはv9.26なのですが、なぜかgs_init.psに対してリビジョン不一致のエラーが出ていました。  
> gs: Interpreter revision (926) does not match gs_init.ps revision (921).

このbuildpackでは、gsの展開に加えて、LilyPondのgsファイルを置き換える処理をしています。
事前にLilyPondがインストールされている前提で動作します。
