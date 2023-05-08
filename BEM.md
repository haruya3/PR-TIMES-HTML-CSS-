# CSSの設計のフレームワーク
BEMを使う利点は、CSSを扱う際に独立したBlockを作ることができるので再利用性が高い。また、とても直感的に理解しやすい構造になっているのも魅力。
BEMには、HTML要素に対して大きく分けていて、以下の3つがある。
- Block
- Element
- Modifier


**これら3つに分けてcssのクラスの命名規則を作っている**。

## Block
独立して意味を持つブロックのこと。
命名規則はblockとする。
(例)
⭕️header, body, form, input, menu...
❌red, small..

ちなみに、BlockはBlockの中に出現しても良い。また、Elementを必ず持つ必要はない。

## Element
Blockの中に存在するもの。独立した意味を持たないもの。
命名規則はblock_elementとする。
(例)
⭕️logo_description, nav_list
❌button_primary_text, menu_list_link
→block_element_elementの形はだめ。block_elementとする。

logoというのはblockにもなり得る。例えば、以下のように。
```html
<header class="header">
    <img src="~~" class="logo">
</header>
```

上記で、logoをheader-logとElementとした場合。他にも、logoを使いたいBlockはたくさんあるはず。
**そういう要素については、Blockとしておくと、他のBlockで使いたい時に汎用性が持てる**。
どうしても、特定の要素としたい場合は`logo`クラスを作った上で、`header-logo`と特定のクラスも作ることで、
上記の、headerというBlock以外のbodyでも`logo`クラスを使えて汎用性を保ちつつ、特定のクラスとできた。


## Modifier 
BlockやElementについて、動作や状態を表すものとする。
命名規則はblock_(element)--状態, block_(element)--key-value
(例)
⭕️header_button--disabling, nav--nonexistence..
❌button--color-yellow..

# 参考
- [公式ドキュメント](https://getbem.com/introduction/)
- [参考記事](https://original-game.com/css-bem/)