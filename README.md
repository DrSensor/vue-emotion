# vue-emotion

[![NPM version](https://img.shields.io/npm/v/vue-emotion.svg?style=flat)](https://npmjs.com/package/vue-emotion) [![NPM downloads](https://img.shields.io/npm/dm/vue-emotion.svg?style=flat)](https://npmjs.com/package/vue-emotion) [![CircleCI](https://circleci.com/gh/egoist/vue-emotion/tree/master.svg?style=shield)](https://circleci.com/gh/egoist/vue-emotion/tree/master)  [![donate](https://img.shields.io/badge/$-donate-ff69b4.svg?maxAge=2592000&style=flat)](https://github.com/egoist/donate)

*[emotion](https://github.com/tkh44/emotion) is the Next Generation of CSS-in-JS.*

## Install

```bash
yarn add emotion vue-emotion
```

## Table of Contents

<!-- toc -->

- [Usage](#usage)
  * [Server-side rendering](#server-side-rendering)
- [Contributing](#contributing)
- [Author](#author)

<!-- tocstop -->

## Usage

Add the babel plugin first:

```json
{
  "plugins": [
    "emotion/babel"
  ]
}
```

Then create your styled component:

```js
import styled from 'vue-emotion'

const Button = styled('button')`
  font-size: 15px;
`

const PinkButton = styled(Button)`
  color: pink
`

new Vue({
  render() {
    return (
      <div>
        <Button>normal button</Button>
        <PinkButton>pink button</PinkButton>
      </div>
    )
  }
})
```

Refer to https://github.com/tkh44/emotion for more docs.

### Server-side rendering

<details open><summary>The easy way, use emotion's extractStatic mode:</summary><br>

```js
// .babelrc
{
  "plugins": [
    ["emotion/babel", { "extractStatic": true }]
  ]
}
```

*Check out the doc about [extractStatic](https://github.com/tkh44/emotion/blob/master/docs/extract-static.md).*

Then when you write something like:

```js
import styled from 'vue-emotion'

const H1 = styled('h1')`
  color: #ffd43b;
`
```

It will be compiled to:

```js
import './h1.emotion.css'
import styled from 'vue-emotion'

const H1 = styled('h1', 'css-duiy4a')
```

Basically you can treat `.emotion.css` as normal CSS file and configure the loader for it in webpack config, since we're trying to make SSR work, you will need `vue-style-loader` instead of `style-loader` for it.
</details>

<details><summary>The alternative way</summary><br>

Check out https://github.com/tkh44/emotion/blob/master/docs/ssr.md, it does **not** support streaming though.
</details>

## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D


## Author

**vue-emotion** © [EGOIST](https://github.com/egoist), Released under the [MIT](./LICENSE) License.<br>
Authored and maintained by EGOIST with help from contributors ([list](https://github.com/egoist/vue-emotion/contributors)).

> [github.com/egoist](https://github.com/egoist) · GitHub [@EGOIST](https://github.com/egoist) · Twitter [@_egoistlily](https://twitter.com/_egoistlily)
