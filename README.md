# Louk Grammar
Cross-editor syntax highlighting for [Louk](https://louk-lang.org)

[![Atom editor](https://img.shields.io/badge/Atom-editor-green.svg?style=flat-square)](http://atom.io/packages/language-louk)
[![Sublime editor](https://img.shields.io/badge/Sublime%20Text-editor-green.svg?style=flat-square)](https://packagecontrol.io/packages/Louk)
[![VS Code editor](https://img.shields.io/badge/VS%20Code-editor-green.svg?style=flat-square)](https://marketplace.visualstudio.com/items?itemName=louk-lang.louk)

## Installation
To install editor extensions, see:
1. Atom: [`language-louk` package](http://atom.io/packages/language-louk)
2. Sublime [`Louk` package](https://packagecontrol.io/packages/Louk)
3. VS Code [`Louk` package](https://marketplace.visualstudio.com/items?itemName=louk-lang.louk)

## About
This is the core development repository for the Louk language grammar, which provides syntax highlighting to text editors. All grammar and metadata changes must be made in this repository, then built into standalone repositories for distribution.

## Tasks
This repository uses gulp tasks for its build pipeline:

* `gulp build` processes the source files and writes the output to the `staging` directory.
* `gulp preview` copies all files from the `staging` subdirectories to their respective preview directories for local testing.
* `gulp distribute` copies all files from the `staging` subdirectories to their respective distribution directories for publishing.
* `gulp test` runs basic sanity checks on the built packages.
* `gulp watch` watches for changes in the source folder, then runs `build` and `preview`.
* `gulp` runs `build`, `preview`, `distribute`, and `test`.

## Publishing

To publish package updates:

1. Ensure all editor package repositories are cloned locally as peers of this repository.
2. Update `*.version` in `source/packages.yaml` according to semantic versioning. The version chosen here should then be used for all following steps. (Note: the `version` in this repository's root package is ***not*** used for versioning the individual editor packages.)
3. Run `gulp`.
4. Commit and push the updated files to each individual editor package's repository.
5. In each editor-specific repository, create and push a Git tag with the new version: `git tag v_._._` and `git push origin tag v_._._`.
6. Publish each individual editor package according to their particular steps:
    * For Atom, publish using the specific tag: `apm publish --tag v_._._`.
    * For Sublime, no additional steps are necessary. Package Control will periodically scan the repo for new releases.
    * For VS Code, publish using the version: `vsce publish _._._`.
7. Verify the new version has been published to each package service:
    * Atom: [`language-louk`](http://atom.io/packages/language-louk)
    * Sublime: [`Louk`](https://packagecontrol.io/packages/Louk) (publishing will be delayed)
    * VS Code: [`Louk`](https://marketplace.visualstudio.com/items?itemName=louk-lang.louk)

## Editor Repos

For individual editor repositories, see:
1. Atom: [`louk-editor-atom` repository](https://github.com/louk-lang/louk-editor-atom)
2. Sublime: [`louk-editor-sublime` repository](https://github.com/louk-lang/louk-editor-sublime)
3. VS Code: [`louk-editor-vscode` repository](https://github.com/louk-lang/louk-editor-vscode)
