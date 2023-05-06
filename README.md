# pypi-upload

GitHub action for publishing your Python 2 distribution files to PyPI or any other repository.

## Usage

To use this action, add the following step to your workflow file (e.g. `.github/workflows/publish.yaml`).

```yml
name: publish

on:
  release:
    types:
      - published

jobs:
  main:
    uses: coatl-dev/action-pypi-upload@v0.1.0
    with:
      password: ${{ secrets.PYPI_API_TOKEN }}
```

## Uploading to TestPyPI

```yml
- name: Publish package to TestPyPI
  uses: coatl-dev/action-pypi-upload@v0.1.0
  with:
    user: ${{ secrets.TEST_PYPI_USER }}
    password: ${{ secrets.TEST_PYPI_API_TOKEN }}
    url: "https://test.pypi.org/legacy/"
```

## Disabling metadata verification

It is recommended that you run `twine check` just after producing your files,
but this also runs `twine check` before upload. You can also disable the
`twine check` with:

```yml
   with:
     check: no
```

## For debugging

Sometimes, `twine upload` can fail and to debug use the verbose setting as follows:

```yml
   with:
     verbose: yes
```
