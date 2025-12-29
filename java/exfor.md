# 拡張for文
```
char[][] ary = { {'a','b'}, {'c','d'} };

for (char[] ar : ary) {
    for (char c : ar) {
        System.out.print(c);
    }
    System.out.print(" ");
}
```
ary
 ├─ ary[0] → char[] {'a','b'}
 └─ ary[1] → char[] {'c','d'}

外側の拡張for文をfor文にするとこうなる
```
for (int i = 0; i < ary.length; i++) {
    char[] ar = ary[i];
    ...
}

```
出力結果：ab cd

#### 誤解ポイント
char型には、２文字は絶対に入らない。
println,printの関係で、２文字連続、空白が入っただけ
内側の拡張for文をfor文にするとこうなる
```
for (int j = 0; j < ar.length; j++) {
    char c = ar[j];
    System.out.print(c);
}
```
