---
title: Contribute to dots-hyprland-wiki
layout: /src/layouts/autonum.astro
sidebar:
  label: Contribute to this site
  order: 05
---

The repo of this doc site is [here](https://github.com/end-4/dots-hyprland-wiki) and it's open to contribution.

**We sincerely thanks for all contributors.**

# What to contribute
You're welcomed to submit any kind of beneficial Pull Request, though it's our final decision to merge it or not.

If you're unsure about a possible PR, you may create a Discussion before you work on it.

## Content
Typically, if you have successfully contributed a new function/workflow/... to [dots-hyprland](https://github.com/end-4/dots-hyprland),
and if it needs documentation, then you're very welcomed to submit a PR here to document it.

Troubleshooting related contents are also welcomed.

**Please see [here](../doc-site) for reference, including how to preview the site (i.e. start local dev server).**
:::caution
Always prioritize updating the English documents,
so that other languages can be uniformly updated through English translation.
:::

## Translation

This site has i18n support, and we need your help to finish l10n (i.e. translation).

:::note
Please don't waste your time on translating Dev Notes. See [#1](https://github.com/end-4/dots-hyprland-wiki/issues/1#issuecomment-1938696111) for reason.
:::

# How to contribute
The following steps details on how to contribute using Git and GitHub.

## Setup GitHub SSH
See <https://docs.github.com/en/authentication/connecting-to-github-with-ssh> for instructions.

Or, to ensure that you have GitHub SSH configured well on your local machine,
run `ssh -T git@github.com` in terminal, and if you see:
```plain
Hi <Your GitHub username>! You've successfully authenticated, but GitHub does not provide shell access.
```
Then you're all set.

## Get this repo
[Fork this repo online](https://github.com/end-4/dots-hyprland-wiki/fork), and then `git clone` the forked repo to your local machine.

## Working on this repo
`cd` to the folder of the cloned repo so that you can make futher changes.

Of course, before making every changes, you should know what you're doing.

As for l10n (translation), follow the steps below:
### Manage locales
On your local machine, go to the forked repo, edit `astro.config.mjs` and find the languages under `locales: `.

If your language is not listed or is commented, add your language.
Example:
```js title="astro.config.mjs" ins={7-10}
...
      locales: {
        'en': {
          label: 'English', // Engligh
          lang: 'en',
        },
        'zh-cn': {
          label: '简体中文', //Simplified Chinese
          lang: 'zh-CN',
        },
...
```
You may also add translation for the labels on sidebar under the `sidebar: `.
Example:
```js title="astro.config.mjs" ins={6}
...
      sidebar: [
        {
          label: 'General',
          translations: {
            'zh-CN': '通用',
          },
          autogenerate: { directory: 'general' },
        },
...
```
:::caution
Please pay attention to the formatting of `mjs` and do not omit commas, quotation marks, or parentheses.
:::

You should also translate the message in `l10n-notify.json`, e.g. for `zh-CN`:
```json title="l10n-notify.json" ins={3}
{
  "en": "This page is an outdated translation. The original version in English was last updated on: ",
  ...
  "zh-cn": "此页面的翻译已过时。其英语原文的最新版本的时间是：",
  ...
}
```

### Translate pages
Go to directory `src/content/docs/`.
- Source language (English): `src/content/docs/en/`.
- Target language (your language): `src/content/docs/<lang>/`.

If target language directory does not exists, `mkdir` to create it first.

Target language directory has exact the same folder structure and filename as the source language directory,
and non-existing files and directory in target language directory will fallback to source language (English).

E.g. for Simplified Chinese, `src/content/docs/zh-cn/general/showcase.md` is the translated version of `src/content/docs/en/general/showcase.md`.

:::note
Again, don't translate Dev Notes under `src/content/docs/en/dev/`, i.e. let them fallback to English.
:::

:::caution
Use **lowercase** for language labels, except for the `lang:` and group-label on sidebar in `astro.config.mjs`.
Take `zh-CN` as Example (in astro.config.mjs):
```js title="astro.config.mjs" {2,4,9}
...
        'zh-cn': {
          label: '简体中文', //Simplified Chinese
          lang: 'zh-CN',
        },
...
        label: 'General',
        translations: {
          'zh-CN': '通用',
        },
...
```
As well for the directory name, e.g. `src/content/docs/zh-cn`.
However, as for UI translation filename, e.g. `src/content/i18n/zh-CN.json`.
:::

If you see the "L10N-NOTIFY" at the top of a document, after you've finished updating its translation, please delete these 3 lines, e.g. for `zh-cn`:
```md del{6-8}
---
title: illogical-impulse 简介
sidebar:
  label: 简介
---
:::caution[L10N-NOTIFY]
此页面的翻译已过时。其英语原文的最新版本的时间是：2024-02-18
:::
```

### Translate UI (Optional)
Starlight UI already has built-in translation for some languages.
You may still translate to override it if you think it's necessary.

- The source file in English: see [here](https://starlight.astro.build/guides/i18n/#translate-starlights-ui).
- To translate, edit the file under `src/content/i18n/`, eg. for Simplified Chinese: `src/content/i18n/zh-CN.json`.

## Upload changes
When you've finished making changes to the repo:
  - `git add .` to track untracked changes under current directory.
  - `git commit` to commit the tracked changes with description.
  - `git push` to push new commits to the repo on GitHub.

## Create a Pull Request
Go to the forked repo online, click on `Contribute` and then `Open pull request` to submit a Pull Request.

Remember to detail what you have done when you submit.
E.g. if you've done translation, tell which language you have translated to.