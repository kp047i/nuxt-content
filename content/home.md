---
title: nuxt/contentによる静的サイトの生成
tag: [Nuxt]
---

# nuxt/contentによる静的サイトの生成

## nuxtのプロジェクト作成

``` bash
create-nuxt-app nuxt-content

create-nuxt-app v2.14.0
✨  Generating Nuxt.js project in nuxt-content
? Project name nuxt-content
? Project description My magnificent Nuxt.js project
? Author name kp047i
? Choose the package manager Yarn
? Choose UI framework Tailwind CSS
? Choose custom server framework None (Recommended)
? Choose Nuxt.js modules
? Choose linting tools ESLint, Prettier
? Choose test framework None
? Choose rendering mode Universal (SSR)
? Choose development tools jsconfig.json (Recommended for VS Code)
yarn run v1.22.4
$ eslint --ext .js,.vue --ignore-path .gitignore . --fix
Done in 22.20s.

🎉  Successfully created project nuxt-content
```

## nuxt/contentのインストール

``` bash
yarn add @nuxt/content
```

## コンテンツの作成

ルートディレクトリにcontentディレクトリを作成し、その中にmdファイルを作成する。

## コンテンツの表示

scriptタグ内のasyncDataで記事を取得する。

``` js
<script>
export default {
  async asyncData({ $content, params }) {
    const article = await $content(`articles/${params.slug}`).fetch()
    return {
      article
    }
  }
}
</script>
```

nuxt-contentのdocumentにバインドすることで記事が表示される

``` html
<nuxt-content :document="article" />
```
