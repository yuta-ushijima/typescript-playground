## TypeScriptの基本的な型について

TypeScriptの基本的な型について理解を深めるため、以下の型について、それぞれの概要と例を示したドキュメントです。

1. boolean
2. number
3. string
4. Array
5. Tuple
6. Enum
7. any
8. void
9. null and undefined
10. never

## 概要とコード例
### boolean
- 概要
  - 真偽値
- 例
```typescript
const bool = true;
```

### number
- 概要
  - 数値
    - 整数や浮動小数点数を含む
- 例
```typescript
const number = 1;
```

### string
- 概要
  - 文字列
- 例
```typescript
const str = 'test';
```

### Array
- 概要
  - 配列
    - 同じ型の要素のリストを含む
- 例
```typescript
const array = [1, 2, 3];
```

### Tuple
- 概要
  - 要素の型が異なる、固定長の配列
- 例
```typescript
const tuple = [1, 'two']
```

### Enum
- 概要
  - 列挙型で、関連するあたいのグループを表現する
- 例
```typescript
enum Color {
  Red,
  Green,
  Blue
}
const redColor: Color = Color.Red;
const blueColor: Color = Color.Blue;
const greenClour: Color = Color.Green;
```

### any
- 概要
  - どの型にも属さない
    - 任意の型を表現する型で、型チェックを回避できます。
- 例
```typescript
   const a: any = 'test';
```

### void
- 概要
  - 戻り値なし
- 例
```typescript
function doNothing(): void {
  console.log('This function returns nothing');
}
```

### null and undefined
- 概要
  - null と undefined の値を表現する型
- 例
```typescript
const test: null = null;
const test2: undefined = undefined;
```

### never
- 概要
  - 関数が終了しないか、常に例外をスローすることを示す型
- 例
```typescript
function throwError(message: string): never {
  throw new Error(message);
}
```