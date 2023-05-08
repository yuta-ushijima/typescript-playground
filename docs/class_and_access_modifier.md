# TypeScriptのクラスとアクセス修飾子について

TypeScriptのクラスとアクセス修飾子についてについて理解を深めるため、以下の項目について、それぞれの概要と例を示したドキュメントです。

1. クラスとは何ですか？
2. アクセス修飾子とは何ですか？
3. TypeScriptで利用できるアクセス修飾子の種類は何ですか？
4. それぞれのアクセス修飾子について、簡単な説明とコード例を示してください。

## 概要と使用例
### クラスとは何ですか？
- 概要
  - クラスはオブジェクト指向プログラミングにおける設計図のようなもの。
  - クラスを使って、オブジェクト（実際のデータを持ったインスタンス）を作成する際の基本的な構造となる属性とメソッドを定義する。
  - 属性はオブジェクトの状態を表し、メソッドはオブジェクトができることや振る舞いを表す。
  - 同じクラスから生成されたオブジェクトは、同じ属性とメソッドを持つ。
    - これにより、同じ構造を持つオブジェクトを効率的に作成できる。
### アクセス修飾子とは何ですか？
- 概要
  - クラスの中で定義した関数やプロパティの使用範囲を定義したもの
### TypeScriptで利用できるアクセス修飾子の種類は何ですか？
- 概要
  - TypeScriptで利用できるアクセス修飾子の種類は、以下の3つ
    - public
    - protected
    - private
### それぞれのアクセス修飾子について、簡単な説明とコード例を示してください。
- 概要
#### public
- 説明
  - クラス内外からアクセスが可能
- コード例
```typescript
class Animal {
  public name: string;

  constructor(name: string) {
    this.name = name;
  }
}
const dog = new Animal('Dog');
console.log(dog.name); // "Dog"
```
#### protected
- 説明
  - クラス内と継承先のクラスからアクセス可能
- コード例
```typescript
class Animal {
  protected name: string;

  constructor(name: string) {
    this.name = name;
  }
}

class Dog extends Animal {
  sayName(): void {
    console.log(this.name);
  }
}

const dog = new Dog('Dog');
dog.sayName(); // "Dog"
console.log(dog.name); // Error: Property 'name' is protected and only accessible within class 'Animal' and its subclasses.
```
#### private
- 説明
  - クラス内からのみアクセス可能
- コード例
```typescript
class Animal {
private name: string;

constructor(name: string) {
this.name = name;
}
}

class Dog extends Animal {
sayName(): void {
console.log(this.name); // Error: Property 'name' is private and only accessible within class 'Animal'.
}
}

const dog = new Animal('Dog');
console.log(dog.name); // Error: Property 'name' is private and only accessible within class 'Animal'.
```