# モジュール
プログラムの最小単位 クラスをグループ化する仕組みとしてパッケージが使用され、モジュールはパッケージの上位としてパッケージをグループ化する。

### モジュールの目標
- 信頼性の高い構成
    モジュール間の依存性を明示的に宣言するメカニズムが提供されるため、コンパイル、実行時の両方で依存性を認識できる
- 強力なカプセル化
    モジュール内のパッケージは、モジュールで明示的にエクスポートされた場合のみ他のモジュールからアクセス可能になる。
    パッケージのエクスポート元モジュールの機能が必要であることを明示的に宣言しない限り、エクスポートされたパッケージを他のモジュールから使用できない。
    これにより攻撃者がアクセスできるクラスが減り、プラットフォームのセキュリティが向上する。  
- スケーラブルな Java プラットフォーム
- プラットフォームの整合性向上
    プラットフォームに同梱されているクラスのうち、その上で稼働するアプリケーションから利用できてしまう問題があったが、モジュールシステムにより、内部APIは完全にカプセル化され、アプリケーションには非公開にすることができる。
- パフォーマンスの向上
    JVM での最適化手法を使ってアプリケーションのパフォーマンス改善が、モジュールによりさらに向上する。

### モジュール宣言
パッケージと同じく、ドットで区切った名前を使用できる。
requires java.base;は、すべてのモジュール宣言で暗黙的に行われるため省略可能。

構文)
```
module モジュール名{}
```
例)
```
module com.seshop.sample{
requires java.base;
}
```
### モジュールにクラスを配置する
```
package com.seshop.sample.main;
```
### モジュールの実行
モジュールが格納されている場所を指定する
```
 java -module-path.--module com.seshop.sample/com.seshop.sample.main.Main
```
省略形(-module-path → -p)(--module → -m)
```
java -p.-m com.seshop.sample/com.seshop.sample.main.Main
```
#### モジュール記述子の情報の参照
--describe-moduleオプション
```
java -p.--describe-module comseshop.sample
実行結果)
com.seshop.sample file:/1/com.seshop.sample/./①
requires java.base②
contains com.seshop.sample.main③
```
①モジュール名とその格納場所
②このモジュールには標準モジュール java.baseが必要である
③com.seshop.sample.mainパッケージが含まれている
#### 依存関係を調べる
jdeps コマンドはmoduleの依存関係を調べる。依存関係を調べたいclassファイルやJARファイル名を指定する。
```
jdeps com¥seshop¥sample¥main¥Main.class
java.base
```

#### module-info.java
モジュールの設定ファイル。module-info.javaをコンパイルして生成されたmodule-info.classはモジュールのルートディレクトリに配置される。
何も利用せず、何も公開しないモジュールであれば、module-info.java内を空にすることができる。
