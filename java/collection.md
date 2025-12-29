# コレクション
#### compareTo

#### sort(コンパレータa,b)->a.compareTo(b);
コンパレータインタフェースを実装したクラスのオブジェクト（コンパレータ）が示す順序に従ってリストがソートされる。
```
(o1,o2)->o2.compareTo(o1) 
```
コンパレータの2つの値を o2.compareTo(o1)により比較して、0,正数、負数を返す。その値によりsort()メソッドは並べ替えを行う。

正数：並び順は、自オブジェクトが比較対象オブジェクトの後ろにくる
負数：並び順は、自オブジェクトが比較対象オブジェクトの前にくる
```
System.out.print("banana".compareTo("apple"));
```
→　1が返る　sortは、apple,bananaの順になる
```
System.out.print("apple".compareTo("banana"));
```
→ -1が返る　sortは、apple,bananaの順になる

#### list.of()
固定のリストを返すメソッドであり、add などで追加しようとすると、実行時例外が出る。UnsupportedOperationException
