# コードの実行
#### クラスファイルの作成コンパイル
javac -d 作成したい場所を指定 /../../(ルートからのパス）/Main.java
```
javac -d classes src/com/se/Main.java
```
#### 実行
java -cp classファイルの場所 パッケージ名.class名
```
java -cp classes com.se.Main
```
#### mainメソッド
java Main 実行時、JVMは次の完全一致のシグネチャだけを探す。
```
public static void main(String[]args)または(String...args)
```
例えば配列ではないmain(String args) はJava文法としては正しいメソッドだが、JVM がエントリーポイントとして認識するmain(String[] args) ではないため、コンパイルは通り、実行時にエラーになる。
