## 基本型・組み込み型
```
i8
i16
i32
i64

u8
u16
u32
u64

f32
f64

char
string
bool

usize  // <- alias of u64

List<T>

Vector<T>

Option<T>
```

## プロジェクトの作成
- パッケージマネージャである Oil を使用し、プロジェクトフォルダを作成する。
- その中に src フォルダと src/Main.fire, package.json が自動で作成される。
- "Hello, World!" を出力するプログラムが最初から生成される。


## ソースファイルの作成
- プロジェクトフォルダ内に
- ファイル名は UpperCamelCase で、拡張子は `.fire` 。

## フォルダの使用


## 言語仕様

タプル `(T, U, ...)`
```
var tu = (1, 'c', "aiueo");

println(tu.0);
println(tu.1);
// インデックスを数値で指定して、要素を取得する。
// 0 から始まる。

println(tu.first);
println(tu.second);
println(tu.third);
// ３つめの要素までは first ~ third のメンバ名を使用可能

var index = 2;
println(tu.(index));
// ( ) を使用すると変数や式をインデックスの値として指定可能。
