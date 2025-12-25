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


# 言語仕様

### import
ファイルの内容をその場に展開する。（トークン列ではなくパースされた構文木を取り込む）
ファイル名の拡張子 `.fire` は不要。
```
import SubFile;
```

フォルダ内の任意のものを指定する場合、スコープ解決演算子を使用する。
複雑なフォルダ構成はできないように、深さ 3 層目のファイルまでのみ取り込み可能。
```
import SubFolder::File;                   // OK.

import SubFolder::Folder2::File;          // OK.

import SubFolder::Folder2::Folder3::File; // Error!!
```

また、フォルダ名そのものを指定すると、そのフォルダの中にあるファイルとフォルダを全て取り込む。
```
import SubFolder;
```

パスは絶対パスを推奨していて、相対パスを使用すると警告メッセージで絶対パスに変換されたものを通知する。


### タプル `(T, U, ...)`
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
