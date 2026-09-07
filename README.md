# 🐍 Python Project Template

<p>
    <a href="https://www.repostatus.org/#active"><img src="https://www.repostatus.org/badges/latest/active.svg" alt="Project Status: Active – The project is being actively developed."/></a>
    <a href="https://github.com/Dantos7/python-project-template.git"><img alt="Version" src="https://img.shields.io/github/v/release/Dantos7/python-project-template"></a>
    <a href="https://copier.readthedocs.io/"><img alt="Copier" src="https://img.shields.io/badge/made%20with-copier-1d7d6c"></a>
</p>

An *opinionated* [Copier](https://copier.readthedocs.io/) template for Python projects, providing a
standardized structure and configuration to streamline development and ensure best practices.

Unlike a GitHub template repository, a Copier template asks you a handful of questions, renders only
the pieces you asked for, and — because the answers are recorded in `.copier-answers.yml` — lets you
pull in later template improvements with `copier update`.

Every generated project comes with:

- [uv](https://docs.astral.sh/uv/) for project management and packaging
- [ruff](https://docs.astral.sh/ruff/) for linting and formatting
- [ty](https://docs.astral.sh/ty/) for type checking
- [prek](https://prek.j178.dev/) for managing hooks
- [pytest](https://docs.pytest.org/en/stable/index.html) and [coverage](https://coverage.readthedocs.io/en/stable/) for testing and code coverage
- [poethepoet](https://poethepoet.natn.io/) for task management
- [typos](https://github.com/crate-ci/typos) for spell checking
- [EditorConfig](https://editorconfig.org/) for maintaining consistent coding styles

Optional, chosen at generation time:

- [MkDocs](https://www.mkdocs.org/) for documentation
- [DVC](https://dvc.org/) for data version control, alongside a `data/` scaffold
- Version numbers derived from git tags via [uv-dynamic-versioning](https://github.com/ninoseki/uv-dynamic-versioning)
- A commented-out private package index

## 👷 Usage

Generate a new project (no installation needed beyond [uv](https://docs.astral.sh/uv/)):

```bash
uvx copier copy gh:Dantos7/python-project-template my-new-project
```

Answer the prompts, then:

```bash
cd my-new-project
git init
uv sync
uv run prek install
```

Later, to pull in template improvements:

```bash
cd my-new-project
uvx copier update
```

`copier update` performs a three-way merge, so your own edits are preserved; conflicts are written
as `*.rej` files for you to resolve.

## ❓ What you get asked

| Question | Purpose |
| --- | --- |
| `project_name`, `project_slug`, `package_name` | Human name, distribution name and Python import name |
| `project_description`, `author_name`, `author_email`, `github_username` | Metadata for `pyproject.toml`, the README and project URLs |
| `license_type`, `copyright_year` | MIT, Apache-2.0, BSD-3-Clause or no license file |
| `python_version`, `python_constraint` | Target version, pinned to `==3.x.*` or opened up to `>=3.x` |
| `line_length` | Maximum line length enforced by ruff |
| `use_docs` | MkDocs Material site under `docs/` |
| `use_data_dirs`, `use_dvc` | `data/public` + `data/private` scaffold, and DVC for large files |
| `use_dynamic_versioning` | Version derived from git tags, or a static `0.1.0` |
| `use_private_registry` | Commented-out private package index in `pyproject.toml` |

The rest of the toolchain — ruff, ty, pytest (split into `tests/unit/` and `tests/integration/`),
coverage, poethepoet, prek, typos, EditorConfig, `.gitattributes` and `CHANGELOG.md` — is always
included; it is the opinionated part of this template.

## 🏗️ Repository layout

```text
copier.yml    # the questions and template settings
template/     # the project body that gets rendered (Copier's _subdirectory)
```

Files and directories under `template/` use Jinja in their *names* to be included conditionally —
for example `{% if use_docs %}docs{% endif %}` is only created when documentation is requested.
Files ending in `.jinja` have their contents rendered; everything else is copied verbatim.

## 🧪 Developing the template

```bash
uv sync
uv run poe render   # render ./demo with the default answers
uv run poe check    # render ./demo, then run its own lint, type and test suites
uv run poe clean    # remove ./demo
```

> 💡 `poe render` passes `--vcs-ref=HEAD` so your uncommitted working tree is used. Plain
> `copier copy .` resolves to the **latest git tag** instead, which is why a new release must be
> tagged before consumers see template changes.

## 🤝 Contributing

You are welcome to open a pull request if you want to share a new cool tool to include in the
template or you want to propose alternative settings for a more efficient setup 😃
