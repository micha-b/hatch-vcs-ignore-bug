# README

This repository is a demo project for a bug with [hatch](https://github.com/pypa/hatch/) described in [this issue](https://github.com/pypa/hatch/issues/1649).

## Initial bug

Steps to reproduce:

1. Clone project
2. Add file with the name `ignored-file.txt` inside the `static` directory (File is in .gitignore and therefore cannot be checked in)
3. Set `ignore-vcs` to `false` in the `pyproject.toml` file
4. Build the project and validate that the distribution **does not contain** file `static/ignored-file.txt`
5. Set `ignore-vcs` to `true` line in the `pyproject.toml` file
6. Build the project and validate that the distribution **does still not contain** the file `static/ignored-file.txt` (This is the bug that should be reproduced.)
7. Remove `.gitignore` file
8. Build the project and validate that the distribution **now does contain** the file `static/ignored-file.txt`

Builds are run with `python -m build .`.

Either I am using the feature wrong or there is a bug with this functionality.

## Workaround / Different usage

If the `ignore-vcs` attribute is used differently, as mentioned by [z0gSh1u](https://github.com/z0gSh1u) [here](https://github.com/pypa/hatch/issues/1649#issuecomment-2337253132) the flag actually works as desired.

But in my opinion this still leaves room for improvement on either the documentation (which gives an example with the flag at `[tool.hatch.build.targets.sdist]`) or a more robust implementation that handles this case better.

