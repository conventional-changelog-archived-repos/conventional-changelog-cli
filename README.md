# conventional-changelog-cli

[![Join the chat at https://gitter.im/conventional-changelog/conventional-changelog-cli](https://badges.gitter.im/conventional-changelog/conventional-changelog-cli.svg)](https://gitter.im/conventional-changelog/conventional-changelog-cli?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

[![NPM version][npm-image]][npm-url] [![Build Status][travis-image]][travis-url] [![Dependency Status][daviddm-image]][daviddm-url] [![Coverage percentage][coveralls-image]][coveralls-url]

> Generate a changelog from git metadata

*[Changelog?](https://speakerdeck.com/stevemao/compose-a-changelog)*

**Note** You don't have to use the angular commit convention. For the best result of the tool to tokenize you commit and produce flexible output, it's recommended to use a commit convention.


## Quick start

```sh
$ npm install -g conventional-changelog-cli
$ cd my-project
$ conventional-changelog -p angular -i CHANGELOG.md -s
```

This will *not* overwrite any previous changelog. The above generates a changelog based on commits since the last semver tag that match the pattern of a "Feature", "Fix", "Performance Improvement" or "Breaking Changes".

If you first time use this tool and want to generate all previous changelog, you could do

```sh
$ conventional-changelog -p angular -i CHANGELOG.md -s -r 0
```

This *will* overwrite any previous changelog if exist.

All available command line parameters can be listed using CLI: `conventional-changelog --help`.

**Hint:** You can alias your command or add it to your package.json. EG: `"changelog": "conventional-changelog -p angular -i CHANGELOG.md -s -r 0"`.

To fully customize the tool, please checkout [conventional-changelog](https://github.com/ajoslin/conventional-changelog) and [conventional-changelog-core](https://github.com/conventional-changelog/conventional-changelog-core) docs. You can find more details there. **Note: `config` here can work with `preset`, which is different than `options.config` in conventional-changelog.**


## Example output

- https://github.com/ajoslin/conventional-changelog/blob/master/CHANGELOG.md
- https://github.com/karma-runner/karma/blob/master/CHANGELOG.md
- https://github.com/btford/grunt-conventional-changelog/blob/master/CHANGELOG.md


## Recommended workflow

1. Make changes
2. Commit those changes
3. Make sure Travis turns green
4. Bump version in `package.json`
5. `conventionalChangelog`
6. Commit `package.json` and `CHANGELOG.md` files
7. Tag
8. Push


The reason why you should commit and tag after `conventionalChangelog` is that the CHANGELOG should be included in the new release, hence `gitRawCommitsOpts.from` defaults to the latest semver tag.

If you use `npm version`, it auto tags immediately after changing the version in package.json. In such case, you might want to specify the version manually and generate the changelog before `npm version`.

Please use this [gist](https://gist.github.com/stevemao/280ef22ee861323993a0) to make a release or change it to your needs.


## Why

- Used by AngularJS, JSHint and related projects.
- Easy fully automate changelog generation. You could still add more points on top of it.
- Ignoring reverted commits, templating with [handlebars.js](https://github.com/wycats/handlebars.js) and links to references, etc. Open an [issue](../../issues/new) if you want more reasonable features.
- Intelligently setup defaults but yet fully configurable with presets of [popular projects](https://github.com/ajoslin/conventional-changelog#preset).
- Everything internally or externally is pluggable.
- A lot of tests and actively maintained.

### Problems with [github-changelog-generator](https://github.com/skywinder/github-changelog-generator) or similar projects

- Opinionated on how to write commits, issues or PRs.
- No or partially support reference links.
- Not system agnostic. Only support GitHub.
- No template support. The output is mostly certain format of markdown.
- No presets of popular commit message conventions.
- Not modularized. Over the years [modularization is proven to be the best practice](https://github.com/sindresorhus/ama/issues/10#issuecomment-117766328).
- No tests or coverage is too low. Program might be buggy.
- Do not read your project's environment.
- No or few task runner or build tool integrations.


## Related

- [conventional-changelog](https://github.com/ajoslin/conventional-changelog) - API of this module
- [standard-changelog](https://github.com/conventional-changelog/standard-changelog) - Similar to this module but only with angular convention
- [conventional-github-releaser](https://github.com/conventional-changelog/conventional-github-releaser) - Make a new GitHub release from git metadata
- [conventional-recommended-bump](https://github.com/conventional-changelog/conventional-recommended-bump) - Get a recommended version bump based on conventional commits
- [conventional-commits-detector](https://github.com/conventional-changelog/conventional-commits-detector) - Detect what commit message convention your repository is using
- [commitizen](https://github.com/commitizen/cz-cli) - Simple commit conventions for internet citizens.
- [angular-precommit](https://github.com/ajoslin/angular-precommit) - Pre commit with angular conventions
- [conventional-changelog-lint](https://github.com/marionebl/conventional-changelog-lint) - Lint commit messages against your conventional-changelog preset


## License

MIT © [Steve Mao](https://github.com/stevemao)


[npm-image]: https://badge.fury.io/js/conventional-changelog-cli.svg
[npm-url]: https://npmjs.org/package/conventional-changelog-cli
[travis-image]: https://travis-ci.org/conventional-changelog/conventional-changelog-cli.svg?branch=master
[travis-url]: https://travis-ci.org/conventional-changelog/conventional-changelog-cli
[daviddm-image]: https://david-dm.org/conventional-changelog/conventional-changelog-cli.svg?theme=shields.io
[daviddm-url]: https://david-dm.org/conventional-changelog/conventional-changelog-cli
[coveralls-image]: https://coveralls.io/repos/conventional-changelog/conventional-changelog-cli/badge.svg
[coveralls-url]: https://coveralls.io/r/conventional-changelog/conventional-changelog-cli
