# sme_deps [![Release Builds](https://github.com/spatial-model-editor/sme_deps/actions/workflows/release.yml/badge.svg)](https://github.com/spatial-model-editor/sme_deps/actions/workflows/release.yml)

Static compilation of [spatial-model-editor](https://github.com/spatial-model-editor/spatial-model-editor) build dependencies.
These libraries are used to produce the binary releases, see [spatial-model-editor/ci](https://github.com/spatial-model-editor/spatial-model-editor/blob/main/ci/README.md) for more information.

This contains all of the libraries from [sme_deps_common](https://github.com/spatial-model-editor/sme_deps_common), as well as:

- [dune-copasi](https://gitlab.dune-project.org/copasi/dune-copasi)

Get the latest versions here:

- linux (clang 19 / Ubuntu 22.04): [sme_deps_linux.tgz](https://github.com/spatial-model-editor/sme_deps/releases/latest/download/sme_deps_linux.tgz)
- linux-arm64 (clang 19 / Ubuntu 22.04): [sme_deps_linux-arm64.tgz](https://github.com/spatial-model-editor/sme_deps/releases/latest/download/sme_deps_linux-arm64.tgz)
- osx (Xcode 15.2 / macOS 13): [sme_deps_osx.tgz](https://github.com/spatial-model-editor/sme_deps/releases/latest/download/sme_deps_osx.tgz)
- osx-arm64 (Xcode 16.1 / macOS 14): [sme_deps_osx-arm64.tgz](https://github.com/spatial-model-editor/sme_deps/releases/latest/download/sme_deps_osx-arm64.tgz)
- win64-mingw (mingw-w64-x86_64-gcc 14): [sme_deps_win64-mingw.tgz](https://github.com/spatial-model-editor/sme_deps/releases/latest/download/sme_deps_win64-mingw.tgz)

## Updating this repo

Any tagged commit will result in a github release.

To make a new release, update the library version numbers in [release.yml](https://github.com/spatial-model-editor/sme_deps/blob/main/.github/workflows/release.yml#L6) (and the build script [build.sh](https://github.com/spatial-model-editor/sme_deps/blob/main/build.sh) if necessary), then commit the changes:

```
git commit -am "revision update"
git push
```

This will trigger GitHub Action builds which will compile the libraries. If the builds are sucessful, tag this commit with the date and push the tag to github:

```
git tag YYYY.MM.DD
git push origin YYYY.MM.DD
```

The tagged commit will trigger the builds again, but this time they will each add an archive of the resulting static libraries to the `YYYY.MM.DD` release on this github repo.
