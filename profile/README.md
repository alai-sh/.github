A fast package and environment manager for Ansible collections, heavily
inspired by [uv](https://docs.astral.sh/uv/). alai resolves the collections a
project needs, records the exact versions in a lock file, and installs them in
a fraction of the time `ansible-galaxy` takes.

<!-- Published by alai's docs build from alai-sh/alai's docs/assets/casts/: move these if those files move.
     Kept in step with the landing page, alai-sh/alai-sh.github.io's docs/index.md. -->
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://docs.alai.sh/assets/casts/galaxy-comparison-dark.svg">
  <img alt="ansible-galaxy and alai each installing community.general with nothing cached, played side by side: alai finishes and installs it again into another project while ansible-galaxy is still running" src="https://docs.alai.sh/assets/casts/galaxy-comparison-light.svg">
</picture>

> [!WARNING]
> alai is in preview and its interface isn't stable yet. It's written with
> the help of AI coding tools, with a human arguing over every design
> decision; [the docs](https://docs.alai.sh/) say more.

## Getting started

Install alai with [uv](https://docs.astral.sh/uv/getting-started/installation/),
which puts the `alai` command on your `PATH`:

<!-- At the first PyPI release: `uv tool install alai-sh`, as in alai's docs. -->
```console
$ uv tool install https://github.com/alai-sh/alai/archive/refs/heads/main.tar.gz
```

An `alai.toml` marks the project, so create one beside your playbooks, add the
collections they use, then run Ansible with them:

```console
$ touch alai.toml
$ alai add ansible.posix 'community.general>=10,<12'
Resolved 2 collections in 522ms
Prepared 2 collections in 1.21s
Installed 2 collections in 41ms
 + ansible.posix==2.2.2
 + community.general==11.4.9
$ alai run ansible-playbook site.yml
```

Commit `alai.toml` and the `alai.lock` it writes, and anyone who clones the
project gets the same collections with `alai sync`.

**[Read the documentation →](https://docs.alai.sh/)**

## Projects

| | |
|---|---|
| [alai](https://github.com/alai-sh/alai) | The `alai` command: manage a project's collections and run Ansible with them. [Docs](https://docs.alai.sh/) |
| [alai-index](https://github.com/alai-sh/alai-index) | Build and run your own alai index, as a tree of static files, or mirror a Galaxy server into one. |
| [alai-doc](https://github.com/alai-sh/alai-doc) | Read plugin and role documentation from a collection in the terminal. |
| [alai-core](https://github.com/alai-sh/alai-core) | The library the others share. Internal, with no stable API. |
