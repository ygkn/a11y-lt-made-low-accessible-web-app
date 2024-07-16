---
theme: eloc
# some information about your slides (markdown enabled)
title: 「アクセシビリティが低い>Webアプリ」を作ってみた話
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# https://sli.dev/guide/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/guide/syntax#mdc-syntax
mdc: true
---

<h1 class="text-center important:text-[5rem]">「アクセシビリティが<span text-blue>低い</span>Webアプリ」<br />を作ってみた話</h1>

ygkn / 2024年7月16日 YUMEMI.grow アクセシビリティLT会


---
layout: two-cols-header
---

<h1 class="important:mb-0">自己紹介</h1>

::left::


- やぎたと申します
- 株式会社ゆめみ 23卒
- WebとGUIが好きです
-
- $\mathbb {X}$ [@ygkn35034](https://x.com/ygkn35034)

::right::

![プロフィール画像](/images/logo.png)

---

<h1 class="text-center important:text-[5rem]">アクセシビリティが<span text-blue>低い</span>Webアプリ<br>「Not Accessible ToDo List」</h1>


https://ygkn.github.io/not-accessible-todo-list/

---

# 作った経緯

1. [LT「アクセシビリティのレビューを仕組み化してコストを下げる」](https://scrapbox.io/ygkn/%E3%82%A2%E3%82%AF%E3%82%BB%E3%82%B7%E3%83%93%E3%83%AA%E3%83%86%E3%82%A3%E3%81%AE%E3%83%AC%E3%83%93%E3%83%A5%E3%83%BC%E3%82%92%E4%BB%95%E7%B5%84%E3%81%BF%E5%8C%96%E3%81%97%E3%81%A6%E3%82%B3%E3%82%B9%E3%83%88%E3%82%92%E4%B8%8B%E3%81%92%E3%82%8B)を発表することに
2. いろいろツールを動かして比較してみたい！
3. でもいい感じのサイトがないな…
3. せや！　検証用のアプリを作ったれ！
4. ＼爆誕／

---

# 仕込んだネタ（問題点）

- To do 入力欄の文字が小さすぎる（特に iOS Safari で拡大されてしまう）
- キーボード操作時もフォーカスインジケータが表示されない
- フォームが`<form>`を使って実装されていない（<kbd>Enter</kbd>で送信できない）
- 「追加」ボタンやチェックボックスが`<div>`や`<svg>`で実装されている
- モーションアニメーションが自動再生され、止められない
- ページタイトルが適切に設定されていない
- 画像やアイコンに適切な代替テキストが設定されていない/重複している
- などなど

---

# 作ってどうだったか


---

## 知識は力

- 知っていればすぐに修正できるものも多い
- むしろ知らなければ小手先で回避して余計手間がかかるものも
  - 例: `<form>`を使っていないフォーム
    1. <kbd>Enter</kbd>で送信ができない！
    2. `keydown`イベントで処理
    3. 文字変換時にも送信されてしまう！

---

## ツールの特性を理解して使いたい

- チェックツールの得意分野の違い
  - 例:「追加」ボタンが `<div>` で実装されている問題は、Lighthouseでは発見できないが、biomeやeslint-plugin-jsx-a11yでは発見できる
- チェックツールのみでは発見できない問題もある
  - むしろできるのは2〜3割程度（デジタル庁『ウェブアクセシビリティ導入ガイドブック』より）
  - 意味と実装のずれなど、機械的に判別できないもの


---

## 最初から考慮して設計、開発したい

- UIライブラリ、Reset CSS など
- 開発初期から考慮できれば以外と大変でないものも
- あとから変えるのは大変…

---

## 「誰もが困る」と「特定の状況で困る」の グラデーション

- 「使用者の多くが困る」と「支援技術使用者が困る」は延長線上にある
  - 間に「この端末だと困る」「キーボード操作だと困る」などがある
- 「これは特別な『アクセシビリティ対応』だから…」
  - 本当に？
- 誰がどういう状況で困るかを考えて実装していきたい

---

## まとめ

- 「アクセシビリティが低いWebアプリ」を作ってみたよ
- 「これこういうときに困るやろなぁ〜ｗ」と考えながら実装するのはなかなか無い貴重な経験でした




