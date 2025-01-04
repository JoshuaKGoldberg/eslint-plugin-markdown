# ESLint Markdown Language Plugin

[![npm Version](https://img.shields.io/npm/v/@eslint/markdown.svg)](https://www.npmjs.com/package/@eslint/markdown)
[![Downloads](https://img.shields.io/npm/dm/@eslint/markdown.svg)](https://www.npmjs.com/package/@eslint/markdown)
[![Build Status](https://github.com/eslint/markdown/workflows/CI/badge.svg)](https://github.com/eslint/markdown/actions)

Lint JS, JSX, TypeScript, and more inside Markdown.

<img
    src="screenshot.png"
    height="142"
    width="432"
    alt="A JS code snippet in a Markdown editor has red squiggly underlines. A tooltip explains the problem."
/>

## Usage

### Installing

Install the plugin alongside ESLint v9 or greater:

```sh
npm install --save-dev eslint @eslint/markdown
```

### Configurations

| **Configuration Name** | **Description** |
|---------------|-----------------|
| `recommended` | Lints all `.md` files with the recommended rules and assumes [CommonMark](https://commonmark.org/) format. |
| `processor` | Enables extracting code blocks from all `.md` files so code blocks can be individually linted. |

In your `eslint.config.js` file, import `@eslint/markdown` and include the recommended config to enable the Markdown processor on all `.md` files:

```js
// eslint.config.js
import markdown from "@eslint/markdown";

export default [
    ...markdown.configs.recommended

    // your other configs here
];
```

### Rules

<!-- NOTE: The following table is autogenerated. Do not manually edit. -->

<!-- Rule Table Start -->
| **Rule Name** | **Description** | **Recommended** |
| :- | :- | :-: |
| [`fenced-code-language`](./docs/rules/fenced-code-language.md) | Require languages for fenced code blocks | yes |
| [`heading-increment`](./docs/rules/heading-increment.md) | Enforce heading levels increment by one | yes |
| [`no-duplicate-headings`](./docs/rules/no-duplicate-headings.md) | Disallow duplicate headings in the same document | no |
| [`no-empty-links`](./docs/rules/no-empty-links.md) | Disallow empty links | yes |
| [`no-html`](./docs/rules/no-html.md) | Disallow HTML tags | no |
| [`no-invalid-label-refs`](./docs/rules/no-invalid-label-refs.md) | Disallow invalid label references | yes |
| [`no-missing-label-refs`](./docs/rules/no-missing-label-refs.md) | Disallow missing label references | yes |
<!-- Rule Table End -->

**Note:** This plugin does not provide formatting rules. We recommend using a source code formatter such as [Prettier](https://prettier.io) for that purpose.

In order to individually configure a rule in your `eslint.config.js` file, import `@eslint/markdown` and configure each rule with a prefix:

```js
// eslint.config.js
import markdown from "@eslint/markdown";

export default [
    {
        files: ["**/*.md"],
        plugins: {
            markdown
        },
        language: "markdown/commonmark",
        rules: {
            "markdown/no-html": "error"
        }
    }
];
```

You can individually disable rules in Markdown using HTML comments, such as:

```markdown
<!-- eslint-disable-next-line markdown/no-html -- I want to allow HTML here -->
<custom-element>Hello world!</custom-element>

<!-- eslint-disable markdown/no-html -- here too -->
<another-element>Goodbye world!</another-element>
<!-- eslint-enable markdown/no-html -- safe to re-enable now -->

[Object] <!-- eslint-disable-line markdown/no-missing-label-refs -- not meant to be a link ref -->
```

### Languages

| **Language Name** | **Description** |
|---------------|-----------------|
| `commonmark` | Parse using [CommonMark](https://commonmark.org) Markdown format | 
| `gfm` | Parse using [GitHub-Flavored Markdown](https://github.github.com/gfm/) format | 

In order to individually configure a language in your `eslint.config.js` file, import `@eslint/markdown` and configure a `language`:

```js
// eslint.config.js
import markdown from "@eslint/markdown";

export default [
    {
        files: ["**/*.md"],
        plugins: {
            markdown
        },
        language: "markdown/gfm",
        rules: {
            "markdown/no-html": "error"
        }
    }
];
```

### Processors

| **Processor Name** | **Description** |
|---------------|-----------------|
| [`markdown`](./docs/processors/markdown.md) | Extract fenced code blocks from the Markdown code so they can be linted separately. | 

## Editor Integrations

### VSCode

[`vscode-eslint`](https://github.com/microsoft/vscode-eslint) has built-in support for the Markdown processor.

### Atom

The [`linter-eslint`](https://atom.io/packages/linter-eslint) package allows for linting within the [Atom IDE](https://atom.io/).

In order to see `@eslint/markdown` work its magic within Markdown code blocks in your Atom editor, you can go to `linter-eslint`'s settings and within "List of scopes to run ESLint on...", add the cursor scope "source.gfm".

However, this reports a problem when viewing Markdown which does not have configuration, so you may wish to use the cursor scope "source.embedded.js", but note that `@eslint/markdown` configuration comments and skip directives won't work in this context.

## Contributing

```sh
$ git clone https://github.com/eslint/markdown.git
$ cd markdown
$ npm install
$ npm test
```

This project follows the [ESLint contribution guidelines](https://eslint.org/docs/latest/contribute/).

<!-- NOTE: This section is autogenerated. Do not manually edit.-->
<!--sponsorsstart-->

## Sponsors

The following companies, organizations, and individuals support ESLint's ongoing maintenance and development. [Become a Sponsor](https://eslint.org/donate)
to get your logo on our READMEs and [website](https://eslint.org/sponsors).

<h3>Platinum Sponsors</h3>
<p><a href="https://automattic.com"><img src="https://images.opencollective.com/automattic/d0ef3e1/logo.png" alt="Automattic" height="128"></a> <a href="https://www.airbnb.com/"><img src="https://images.opencollective.com/airbnb/d327d66/logo.png" alt="Airbnb" height="128"></a></p><h3>Gold Sponsors</h3>
<p><a href="https://trunk.io/"><img src="https://images.opencollective.com/trunkio/fb92d60/avatar.png" alt="trunk.io" height="96"></a></p><h3>Silver Sponsors</h3>
<p><a href="https://www.serptriumph.com/"><img src="https://images.opencollective.com/serp-triumph5/fea3074/logo.png" alt="SERP Triumph" height="64"></a> <a href="https://www.jetbrains.com/"><img src="https://images.opencollective.com/jetbrains/fe76f99/logo.png" alt="JetBrains" height="64"></a> <a href="https://liftoff.io/"><img src="https://images.opencollective.com/liftoff/5c4fa84/logo.png" alt="Liftoff" height="64"></a> <a href="https://americanexpress.io"><img src="https://avatars.githubusercontent.com/u/3853301" alt="American Express" height="64"></a> <a href="https://www.workleap.com"><img src="https://avatars.githubusercontent.com/u/53535748" alt="Workleap" height="64"></a></p><h3>Bronze Sponsors</h3>
<p><a href="https://cybozu.co.jp/"><img src="https://images.opencollective.com/cybozu/933e46d/logo.png" alt="Cybozu" height="32"></a> <a href="https://www.crosswordsolver.org/anagram-solver/"><img src="https://images.opencollective.com/anagram-solver/2666271/logo.png" alt="Anagram Solver" height="32"></a> <a href="https://icons8.com/"><img src="https://images.opencollective.com/icons8/7fa1641/logo.png" alt="Icons8" height="32"></a> <a href="https://discord.com"><img src="https://images.opencollective.com/discordapp/f9645d9/logo.png" alt="Discord" height="32"></a> <a href="https://www.gitbook.com"><img src="https://avatars.githubusercontent.com/u/7111340" alt="GitBook" height="32"></a> <a href="https://nx.dev"><img src="https://avatars.githubusercontent.com/u/23692104" alt="Nx" height="32"></a> <a href="https://opensource.mercedes-benz.com/"><img src="https://avatars.githubusercontent.com/u/34240465" alt="Mercedes-Benz Group" height="32"></a> <a href="https://herocoders.com"><img src="https://avatars.githubusercontent.com/u/37549774" alt="HeroCoders" height="32"></a></p>
<h3>Technology Sponsors</h3>
Technology sponsors allow us to use their products and services for free as part of a contribution to the open source ecosystem and our work.
<p><a href="https://netlify.com"><img src="https://raw.githubusercontent.com/eslint/eslint.org/main/src/assets/images/techsponsors/netlify-icon.svg" alt="Netlify" height="32"></a> <a href="https://algolia.com"><img src="https://raw.githubusercontent.com/eslint/eslint.org/main/src/assets/images/techsponsors/algolia-icon.svg" alt="Algolia" height="32"></a> <a href="https://1password.com"><img src="https://raw.githubusercontent.com/eslint/eslint.org/main/src/assets/images/techsponsors/1password-icon.svg" alt="1Password" height="32"></a></p>
<!--sponsorsend-->
