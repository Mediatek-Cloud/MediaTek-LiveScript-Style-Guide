MediaTek-LiveScript-Style-Guide
===============================

## Code Layout

### 縮排
使用2個space，不可使用tab。

### 空白行
Class與Function的前面必須要有空白行。

### 結尾空白
行的末端不可以有任何空白。

### 行結束
每行的結束都必須使用分號( ; )，除非前後行有物件或陣列關係。

### 行語句
每行應該只表達單一意思或執行單一任務。

```
# good
x = 1;
y = 10 if 1 < x;
z = x = 10;

# bad
x = 1; y = 2;
x++; x-- if 1 == y;
```

### Package
- 檔頭require必需使用單個object require
- 檔中的每個require都必需單行表示
- Package Name必需使用單引號
- 冒號( : )後必須要有一個空白

```
# good
require! {
  fs
  path
  lib: 'lib4'
}

require! $: 'jQuery';
require! schema: 'mysql'.Schema;

# bad
fs = require('fs')
require! [fs, path]
require! <[ fs path ]>
```

### 命名方式
- Class 名稱一律使用大駝峰方式命名
- Variable 與 Function 名稱一律使用小駝峰方式命名
- Variable第一個單詞必須使用名詞
- Function 第一個單詞必須使用動詞
- Variable 最後一個單詞是型態(Int, Str, Bool, Date, Time, DateTime, Float, Ary, Obj, Buffer, Mixed)，
- 區域Variable前置增加底線( _ )。

### Constant
使用全大寫加底線 NAMES_LIKE_THIS for constant values.

## Literals

### Booleans
必須使用全小寫的true和false

### Numbers
建議加上單位幫助可讀性
limitInt = 7days * 24hours

### Strings
使用單引號( ' )，當字串內需要讀取變數時改用雙引號，並在變數前後使用大括號。
Multiline strings( ''' ) 不可使用。
```
# good
'hello world'
"hello #{name}"

# bad
\hello
"hello #name"
```

### Object OR Array
- 每個Value/Property使用換行表示，不使用逗號( , )
- Property Name前後不使用引號
- 冒號( : )後面必需要有一個空白
- 前後不使用中括號( [ )或大括號( { )
- 不可以使用 <[ list of words ]>，除了framework require需求

```
# good
total =
  100
  'apple'
  "banana #{color}"
  today: 3
obj =
  * name: 'tessa'
    age:  23
  * name: 'kendall'
    age:  19
```

### This
使用@取代this，當要使用上層Scope時，優先使用 !->，使用@@。

### Prototype
使用雙冒號( :: )取代prototype

## Operators

### Spacing
每個運算元前後都必需要有空白。

### Logic
邏輯比較值在前變數在後。
```
# good
if ( 1 == x )

# bad
if ( x == 1 )
```

## Aliases

### English vs Symbols
使用 &&, ||, ! ... 等, 不使用 and, or ... 等。

### Parentheses
- 必需使用括號，在任何可以使用括號的地方
- 參數間必需使用逗號( , )區隔
- 物件操作換行時行首必需是從點( . )開始。

```
# good
getCar().getMaxPeople();

openFile(
  'filename',
  'readonly'
)
.close();

# bad
openFile(
  'file'
).close();
```

## Access

### List Access
使用 list.0 優於 list[0]，除非需要在key裡面做運算，像是list[i - 1]。

### Automatic Dot Insertion
物件操作一律要使用點( . )做操作。

### With
禁止使用with

### Switch
- Switch僅限使用於單行處理的狀況，多行一律使用if else，
- 一律使用Short方式。

```
# good
x = switch name
| "some thing"     => 'hello'
| \explosion \bomb => 'boom'
| <[ the moto ? ]> => 'here it is'
| otherwise        => 'something'
```