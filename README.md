# Age secret management skeleton

## Prerequisites

- [Mise](https://mise.jdx.dev/)

## Setup the workspace

```sh
$ mise install
```

Setting up the `.secret` file. For this, you have two methods:

1. The first one, if your SSH public key is already in place in [`./ssh-keys/`](./ssh-keys/), then
   you can run the `./scripts/decrypt_secrets.sh` command which will automatically generate a `.secret` file.
2. Otherwise, the second method is to copy `.secret.skel` to `.secret` (`cp .secret.skel .secret`) and
   contact the person mentioned in the file to request the secrets.

Après cela, n'oubliez pas de recharger les variables d'environnement avec :

```sh
$ source .envrc
```

## How to add a new user to the secrets encryption system?

Add their SSH public key in a new file in [`./ssh-keys/`](./ssh-keys/) and then run `./scripts/encrypt_secrets.sh`.
This script will generate a new `.secret.age` file that can be decrypted with all the private SSH keys corresponding to the keys present in `./ssh-keys/`.
