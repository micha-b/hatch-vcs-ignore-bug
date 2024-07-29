# README

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
