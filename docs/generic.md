## TypeScriptのジェネリックについて

TypeScriptのジェネリックについて理解を深めるため、以下の項目について、それぞれの概要と例を示したドキュメントです。

1. ジェネリックとは何か、その目的を説明してください。
2. ジェネリックを使用した関数を作成する方法を説明し、例を示してください。
3. ジェネリックを使用したインターフェイスを作成する方法を説明し、例を示してください。
4. ジェネリックを使用したクラスを作成する方法を説明し、例を示してください。
5. ジェネリックの制約を設定する方法を説明し、例を示してください。

## 概要とコード例
### ジェネリックとは何か、その目的を説明してください。
- ジェネリックとは
  - 型をパラメータ化して、汎用的なコードを書くための仕組み
- 目的
  - 様々な型に対応できる共通の関数やクラスを作成するため
    - 同じロジックを異なる型に適用できるようにすることが目的
      - 特定の型を扱う場合には必要ない
        - 特定の型を受け入れる場合、ジェネリックを使わずに直接その型を指定する

### ジェネリックを使用した関数を作成する方法を説明し、例を示してください。
- 作成方法
  - 関数名の後に、角括弧（<>）内に型パラメータを記述する。
- コード例
```typescript
function identity<T>(arg: T): T {
  return arg;
}

const output = identity<string>('hello');
```

### ジェネリックを使用したインターフェイスを作成する方法を説明し、例を示してください。
- 作成方法
  - インターフェイス名の後に、角括弧（<>）内に型パラメータを記述する。
- コード例
```typescript
interface GenericArray<T> {
  [index: number]: T;
}

const numArray: GenericArray<number> = [1, 2, 3];
const strArray: GenericArray<string> = ['a', 'b', 'c'];
```

### ジェネリックを使用したクラスを作成する方法を説明し、例を示してください。
- 作成方法
  - クラス名の後に、角括弧（<>）内に型パラメータを記述する
- コード例
```typescript
class GenericStack<T> {
  private items: T[] = [];

  push(item: T) {
    this.items.push(item);
  }

  pop(): T {
    return this.items.pop() as T;
  }
}

const numberStack = new GenericStack<number>();
numberStack.push(42);
console.log(numberStack.pop()); // 42
```

### ジェネリックの制約を設定する方法を説明し、例を示してください。
- 作成方法
  - extendsキーワードを使って、制約となる型を指定する。これにより、ジェネリック型が特定のプロパティやメソッドを持つことを保証できる。
    - 特定のインターフェイスを実装している型だけを受け入れたいケースで利用する
- コード例
```typescript
interface HasLength {
  length: number;
}

function getLength<T extends HasLength>(arg: T): number {
  return arg.length;
}

// 正常に動作する
console.log(getLength('hello')); // string型はlengathプロパティを持っているため5を出力
console.log(getLength([1, 2, 3])); // Array型はlengathプロパティを持っているため3を出力
console.log(getLength({ length: 7 })); // lengthプロパティを持つオブジェクトを直接渡しているため7を出力

// エラーになる
const obj = {
  name: 'Alice',
  age: 30
};

getLength(obj); // objオブジェクトにlengthプロパティが存在しないためエラーが発生
```

### 型パラメータのTについて
- TypeScriptのジェネリックで一般的に使われる慣例。
- `T`は「Type」の頭文字を表しており、どのような型でも受け入れることができるプレースホルダー（仮の型）を示している。

例えば、以下のジェネリック関数`identity`では、型パラメータ`T`を使って引数と戻り値の型を指定している。

```typescript
function identity<T>(arg: T): T {
  return arg;
}
```

上記の関数は、どのような型の引数でも受け入れ、そのままの型で戻り値を返すことができる。
