# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.1.3] - 2021-01-19

### Docs

- Updated documentation for readme and porting existing projects

### Known Issues

- FSharpAnalyzers target doesn't run

## [1.1.2] - 2021-01-19

Should be able to run all targets except the fsharp analyzers

### Fixed
- githubrelease target repo user name

## [1.1.1] - 2021-01-19

Should now be able to run all targets

### Fixed
- first set push branch to master with `git push --set-upstream origin master`

## [1.1.0] - 2021-01-19

Update to enable use for all Informedica projects

### Changed
- Now also uses .net5
- CI using Github actions
- Contains Webserver fix for docs tool
- Changed build script enabling FSI

## [0.1.0] - 2017-03-17

First release

### Added
- This release already has lots of features

[Unreleased]: https://github.com/informedica/Informedica.Build.Template/compare/v1.1.3...HEAD
[1.1.3]: https://github.com/informedica/Informedica.Build.Template/compare/v1.1.2...v1.1.3
[1.1.2]: https://github.com/informedica/Informedica.Build.Template/compare/v1.1.1...v1.1.2
[1.1.1]: https://github.com/informedica/Informedica.Build.Template/compare/v1.1.0...v1.1.1
[1.1.0]: https://github.com/informedica/Informedica.Build.Template/compare/v0.1.0...v1.1.0
[0.1.0]: https://github.com/informedica/Informedica.Build.Template.git/releases/tag/v0.1.0
