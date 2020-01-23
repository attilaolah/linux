# Arch Linux Setup

TODO: Add base setup.

## Pacman packages

Install the following additional packages:

- the\_silver\_searcher

# AUR packages

AUR packages are installed under `~/third_party/aur`.

```shell
export THIRD_PARTY="${HOME}/third_party"
export AURPATH="${THIRD_PARTY}/aur"
```

### Meshroom

Install Meshroom from AUR, along with its dependencies:

- meshroom
  - alice-vision
    - ceres-solver
    - coin-or-lemon
    - flann
    - geogram
    - opengv
    - popsift
    - uncertainty-framework

```shell
pushd "${AURPATH}"
for package in ceres-solver coin-or-lemon flann geogram opengv popsift uncertainty-framework alice-vision meshroom; do
  rm -rf "${package}"
  git clone "https://aur.archlinux.org/${package}.git"
  pushd "${package}"
  makepkg -sic
  popd
done
popd
```
