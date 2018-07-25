# Jest

オールインワンなJestだけを依存に追加すれば、すぐにテストコードを書き始められるようになる。

## test対象ディレクトリ/ファイル

- __tests__ディレクトリ配下のすべてのファイル
- .spec.js or .test.jsで終わるファイル

## watch指定

```
npm test -- --watch
jest --watch
-- verbose 各テストケースごとの結果を表示
```

## 用語

- testPathIgnorePatterns テスト除外指定「node_modules」など

## 参考サイト
[Jestで始める！ ユニットテスト](https://app.codegrid.net/series/2017-jest)
[doc](https://jestjs.io/)
[doc日本語](https://jestjs.io/ja/)
[オプション一覧](https://jestjs.io/docs/en/configuration.html#options)
[オプション一覧CLI](https://jestjs.io/docs/en/cli.html)
