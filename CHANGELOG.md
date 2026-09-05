# 🕰️ Changelog

All notable changes to this project are documented in this file.

This project adheres to [Semantic Versioning](http://semver.org/).


## [0.1.0] - 05/09/2026

### 💥 Breaking changes

- The repository is now a [Copier](https://copier.readthedocs.io/) template instead of a GitHub
  template repository. Generate projects with
  `uvx copier copy gh:Dantos7/python-project-template <destination>`.
- The project body moved from the repository root into `template/`, declared via `_subdirectory`
  in `copier.yml`.

### ✨ Features

- Added `copier.yml` with questions for project identity, license (MIT / Apache-2.0 / BSD-3-Clause /
  none), target Python version, ruff line length, and toggles for MkDocs, the `data/` scaffold, DVC,
  dynamic versioning and a private package index
- ruff, ty, pytest (split into `tests/unit/` and `tests/integration/`), coverage, poethepoet, prek,
  typos, EditorConfig, `.gitattributes` and `CHANGELOG.md` are always included and are not
  configurable — they are the opinionated core of the template
- Generated projects record their answers in `.copier-answers.yml`, so `copier update` can pull in
  later template changes
- Optional MkDocs Material setup (`mkdocs.yml` + `docs/index.md`)
- `poe render`, `poe check` and `poe clean` tasks for developing the template itself

### 🐛 Bug fixes

- [pyproject.toml] pytest settings now live under `[tool.pytest.ini_options]`; under the previous
  `[tool.pytest]` table pytest silently ignored `addopts` and the asyncio loop scope


## [0.0.3] - 16/11/2025

### 🐛 Bug fixes

- [pyproject.toml] Fixed bad Coverage configuration

### 📝 Documentation

- [README] Re-written "Usage" section and added "Contributing" section


## [0.0.2] - 16/11/2025

### ✨ Features

- Added `data/` folder and subfolders for public and private data management
    - Added `.gitignore` and `.gitkeep` files to properly manage data visibility
- Added `src/pkg/` folder for Python package source code
- Added initial test structure in `tests/` folder
- Added `.python-version` file to pin a specific Python version

### 📝 Documentation

- Updated README


## [0.0.1] - 16/11/2025

### ✨ Features

- Initial release
