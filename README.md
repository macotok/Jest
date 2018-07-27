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

テストケースの最小単位。

必ず利用することになる関数

```
test('adds 1 + 2 to equal 3', () => {
  expect(sum(1,2).toBe(3))
});
```

ラベルだけを指定することもできる
テストケースの実行がスキップされる。

またTODOを残す意味で使う

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

### beforeAll()/afterAll()/beforeEach()/afterEach()

全てのテストの実行前/実行後。またはそれぞれのテストケースの実行前/実行後に
任意の処理を差し込める機能

#### beforeEach()/afterEach()

itまたはtest毎に必ず実施した前/後処理がある場合に使う

```
beforeAll(() => console.log('top-beforeAll'));
afterAll(() => console.log('top-afterAll'));

describe('test1', () => {
  beforeEach(() => console.log('test1-beforeEach'));

  test('test1-1', () => {});
  test('test1-2', () => {});
});

describe('test2', () => {
  beforeAll(() => console.log('test2-beforeAll'));
  afterAll(() => console.log('test2-afterAll'));

  test('test2-1', () => {});
  test('test2-2', () => {});
});

describe('test3', () => {
  afterEach(() => console.log('test3-afterEach'));

  test('test3-1', () => {});
  test('test3-2', () => {});
});
```

上記の処理順序

1. top-beforeAll
2. test1-boforeEach
3. test1-1
4. test1-beforeEach
5. test1-2
6. test2-beforeAll
7. test2-1
8. test2-2
9. test2-afterAll
10. test3-1
11. test3-afterEach
12. test3-2
13. test3-afterEach
14. top-afterAll

## 非同期処理

3通りの方法がある

```
beforeAll(done => {
  someAsyncTask(() => {
    ...
    done();
  });
});
```

```
beforeAll(() => {
  return returnPromiseTask().then(() => {
    ...
  });
});
```

```
beforeAll(async () => {
  await returnPromiseTask();
  // ...
});
```

## Matcher(マッチャー)

expect(出力)に対して、それを確かめるメソッド

- toBe()
- toEqual()

## 用語

- testPathIgnorePatterns テスト除外指定「node_modules」など
- -- verbose 各テストケースごとの結果を表示

## 参考サイト
- [Jestで始める！ ユニットテスト](https://app.codegrid.net/series/2017-jest)
- [doc](https://jestjs.io/)
- [doc日本語](https://jestjs.io/ja/)
- [オプション一覧](https://jestjs.io/docs/en/configuration.html#options)
- [オプション一覧CLI](https://jestjs.io/docs/en/cli.html)
- [Facebook製のJavaScriptテストツール「Jest」の逆引き使用例
](https://qiita.com/chimame/items/e97883fd46b67529d59f)
