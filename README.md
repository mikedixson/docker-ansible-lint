# Docker image for `ansible-lint`

[![Tag](https://img.shields.io/github/tag/mikedixson/docker-ansible-lint.svg)](https://github.com/mikedixson/docker-ansible-lint/releases)
[![](https://img.shields.io/badge/github-mikedixson%2Fdocker--ansible--lint-red.svg)](https://github.com/mikedixson/docker-ansible-lint "github.com/mikedixson/docker-ansible-lint")
[![License](https://img.shields.io/badge/license-MIT-%233DA639.svg)](https://opensource.org/licenses/MIT)

[![lint](https://github.com/cytopia/docker-ansible-lint/workflows/lint/badge.svg)](https://github.com/cytopia/docker-ansible-lint/actions?query=workflow%3Alint)
[![build](https://github.com/cytopia/docker-ansible-lint/workflows/build/badge.svg)](https://github.com/cytopia/docker-ansible-lint/actions?query=workflow%3Abuild)
[![nightly](https://github.com/cytopia/docker-ansible-lint/workflows/nightly/badge.svg)](https://github.com/cytopia/docker-ansible-lint/actions?query=workflow%3Anightly)


> #### All [#awesome-ci](https://github.com/topics/awesome-ci) Docker images
>
> [ansible-lint][alint-git-lnk] **•**
> [ansible][ansible-git-lnk] **•**
> [awesome-ci][aci-git-lnk] **•**
> [bandit][bandit-git-lnk] **•**
> [black][black-git-lnk] **•**
> [checkmake][cm-git-lnk] **•**
> [eslint][elint-git-lnk] **•**
> [file-lint][flint-git-lnk] **•**
> [gofmt][gfmt-git-lnk] **•**
> [goimports][gimp-git-lnk] **•**
> [golint][glint-git-lnk] **•**
> [jsonlint][jlint-git-lnk] **•**
> [kubeval][kubeval-git-lnk] **•**
> [linkcheck][linkcheck-git-lnk] **•**
> [mypy][mypy-git-lnk] **•**
> [php-cs-fixer][pcsf-git-lnk] **•**
> [phpcbf][pcbf-git-lnk] **•**
> [phpcs][pcs-git-lnk] **•**
> [phplint][plint-git-lnk] **•**
> [pycodestyle][pycs-git-lnk] **•**
> [pydocstyle][pyds-git-lnk] **•**
> [pylint][pylint-git-lnk] **•**
> [terraform-docs][tfdocs-git-lnk] **•**
> [terragrunt-fmt][tgfmt-git-lnk] **•**
> [terragrunt][tg-git-lnk] **•**
> [yamlfmt][yfmt-git-lnk] **•**
> [yamllint][ylint-git-lnk]

View **[Dockerfiles](https://github.com/mikedixson/docker-ansible-lint/blob/master/Dockerfiles/)** on GitHub.


**Available Architectures:**  `amd64`, `i386`, `arm64`


Tiny Alpine-based multistage-build dockerized version of [ansible-lint](https://github.com/ansible/ansible-lint)<sup>[1]</sup>.
The image is built nightly against the latest stable version of `ansible-lint` and pushed to Dockerhub.

<sup>[1] Official project: https://github.com/ansible/ansible-lint</sup>

[![](https://img.shields.io/docker/pulls/mikedixson/ansible-lint.svg)](https://hub.docker.com/r/mikedixson/ansible-lint)
[![Docker](https://badgen.net/badge/icon/:latest?icon=docker&label=mikedixson/ansible-lint)](https://hub.docker.com/r/mikedixson/ansible-lint)

#### Rolling releaess

The following Docker image tags are rolling releases and are built and updated every night.

[![nightly](https://github.com/mikedixson/docker-ansible-lint/workflows/nightly/badge.svg)](https://github.com/mikedixson/docker-ansible-lint/actions?query=workflow%3Anightly)

| Docker Tag           | Git Ref   | Ansible Lint | Flavour | Available Architectures                      |
|----------------------|-----------|--------------|---------|----------------------------------------------|
| `latest`             | master    | latest       | default | `amd64`, `i386`, `arm64`                     |
| `alpine`             | master    | latest       | Alpine  | `amd64`, `i386`, `arm64`                     |
|                      |           |              |         |                                              |
| `6`                  | master    | **`6.x.x`**  | default | `amd64`, `i386`, `arm64`                     |
| `alpine-6`           | master    | **`6.x.x`**  | Alpine  | `amd64`, `i386`, `arm64`                     |
|                      |           |              |         |                                              |
| `5`                  | master    | **`5.x.x`**  | default | `amd64`, `i386`, `arm64`                     |
| `alpine-5`           | master    | **`5.x.x`**  | Alpine  | `amd64`, `i386`, `arm64`                     |

#### Point in time releases

The following Docker image tags are built once and can be used for reproducible builds. Its version never changes so you will have to update tags in your pipelines from time to time in order to stay up-to-date.

[![build](https://github.com/mikedixson/docker-ansible-lint/workflows/build/badge.svg)](https://github.com/mikedixson/docker-ansible-lint/actions?query=workflow%3Abuild)

| Docker Tag           | Git Ref   | Ansible Lint | Flavour | Available Architectures                      |
|----------------------|-----------|--------------|---------|----------------------------------------------|
| `latest-0.7`         | tag: 0.7  | latest       | default | `amd64`, `i386`, `arm64`                     |
| `alpine-latest-0.7 ` | tag: 0.7  | latest       | Alpine  | `amd64`, `i386`, `arm64`                     |
|                      |           |              |         |                                              |
| `6-0.7`              | tag: 0.7  | **`6.x.x`**  | default | `amd64`, `i386`, `arm64`                     |
| `alpine-6-0.7`       | tag: 0.7  | **`6.x.x`**  | Alpine  | `amd64`, `i386`, `arm64`                     |
|                      |           |              |         |                                              |
| `5-0.7`              | tag: 0.7  | **`5.x.x`**  | default | `amd64`, `i386`, `arm64`                     |
| `alpine-5-0.7`       | tag: 0.7  | **`5.x.x`**  | Alpine  | `amd64`, `i386`, `arm64`                     |


## :open_file_folder: Docker mounts

The working directory inside the Docker container is **`/data/`** and should be mounted locally to
the root of your project where your `.ansible-lint` config file is located.


## :computer: Usage

#### Display usage
```bash
# Single playbook
docker run --rm -v $(pwd):/data mikedixson/ansible-lint playbook.yml

# All playbooks via wildcard
docker run --rm -v $(pwd):/data mikedixson/ansible-lint *.yml

# Single role (run from within the role's root)
docker run --rm -v "$(pwd)":"/data/$(basename "$(pwd)" )" -e ANSIBLE_ROLES_PATH="/data" mikedixson/ansible-lint "/data/$(basename "$(pwd)" )/tests/test.yml"
```

### GitLabCI
GitLabCI requires a shell entrypoint to be specified. See here for details: [Issue #14](https://github.com/mikedixson/docker-ansible-lint/issues/14).
```yaml
default:
  image:
    name: mikedixson/ansible-lint:latest
    entrypoint: ["/bin/sh", "-c"]

stages:
  - lint

ansible-linter:
  stage: lint
  script:
    - ansible-lint *.yaml
  only:
    - merge_requests
    - master
```
### Makefiles

Visit **[cytopia/makefiles](https://github.com/cytopia/makefiles)** for dependency-less, seamless project integration and minimum required best-practice code linting for CI.
The provided Makefiles will only require GNU Make and Docker itself removing the need to install anything else.


## :page_facing_up: License


**[MIT License](LICENSE)**

Copyright (c) 2019 [cytopia](https://github.com/cytopia)
