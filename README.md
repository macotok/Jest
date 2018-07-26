# Jest

オールインワンなJestだけを依存に追加すれば、すぐにテストコードを書き始められるようになる

## test対象ディレクトリ/ファイル

- __tests__ディレクトリ配下のすべてのファイル
- .spec.js or .test.jsで終わるファイル

## watch指定

```
npm test -- --watch
jest --watch
```

## グローバル変数として定義している関数

- test()
- describe()
- beforeAll()
- afterAll()
- beforeEach()
- afterEach()

### test(name, fn)

テストケースの最小単位。必ず利用することになる関数

```
test('adds 1 + 2 to equal 3', () => {
  expect(sum(1,2).toBe(3))
});
```

ラベルだけを指定することもできる
テストケースの実行がスキップされる。またTODOを残す意味で使う

```
test('adds 0 + 0 to equal 0');
```

### describe(name, fn)

test()によって書かれたテストケースをグルーピング

```
describe('a number given', () => {
  test('adds 1 + 2 to equal 3');
  test('adds 0 + 0 to equal 0');
});
```

適切な単位でスコープを形成。コードの見通しをよくする
describe()はいくつもネストさせることができる

### .skip / .only

test()、describe()に付与できるプロパティ

- .skip そのブロック、そのテストの実行をスキップ
- .only そのブロック、そのテストのみを実行

テストケースが多く書かれていて確認に時間がかかるときなどに使用

```
describe('a number given', () => {
  // このテストケースのみ実行
  test.only('adds 1 + 2 to equal 3', () => {
    ...
  });

  // ここはスキップされる
  test('adds 0 + 0 to equal 0', () => {
    ...
  })
});
```

## 用語

- testPathIgnorePatterns テスト除外指定「node_modules」など
- -- verbose 各テストケースごとの結果を表示

## 参考サイト
- [Jestで始める！ ユニットテスト](https://app.codegrid.net/series/2017-jest)
- [doc](https://jestjs.io/)
- [doc日本語](https://jestjs.io/ja/)
- [オプション一覧](https://jestjs.io/docs/en/configuration.html#options)
- [オプション一覧CLI](https://jestjs.io/docs/en/cli.html)
