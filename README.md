# `@uchilaka/mw--cami--cms`

Monorepo with:

- Marketing Website (MW)
- Customer Account Management & Invoicing (CAMI)
- Content Management System (CMS)

## Setting up git-crypt

Ensure your GitHub GPG credentials have been added to the project. Review [this guide](https://docs.github.com/en/authentication/managing-commit-signature-verification/adding-a-gpg-key-to-your-github-account) to add check for/setup a GPG key for your GitHub account.

As a user with project access, run the following code to grant access to another GitHub account:

```shell
git-crypt add-gpg-user <github-email-address>
```

### Locking encrypted files

To unlock encrypted files:

```shell
yarn unlock
```

### Checking encryption status

```shell
git-crypt status
```

## Setting up hostname(s)

### 1. Update `/etc/hosts`

First, add this line to your `/etc/hosts` file (e.g. with `sudo nano /etc/hosts`):

```shell
127.0.0.1  cms.larcity.local
```

### 2. Run the script to symlink the NGINX server configuration

```shell
bin/setup-server-config
```

## Troubleshooting issues

Review the notes on [troubleshooting your local environment](./md/TROUBLESHOOTING.md)

## Resources

- [Strapi tutorials](https://strapi.io/blog/categories/tutorials)
- [Strapi templates](https://github.com/strapi/strapi/tree/develop/templates)
