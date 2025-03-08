# `@uchilaka/mw--cami--cms`: Using `git-crypt`

Ensure your GitHub GPG credentials have been added to the project. Review [this guide](https://docs.github.com/en/authentication/managing-commit-signature-verification/adding-a-gpg-key-to-your-github-account) to add check for/setup a GPG key for your GitHub account. You can also review adjacent documentation for:

- [Generating a new GPG key](https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key)
- [Associating an email with your GPG key](https://docs.github.com/en/authentication/managing-commit-signature-verification/associating-an-email-with-your-gpg-key)

## Setting up `git-crypt` for the first time

> **Do not run this code**. This has already been done for the project

```shell
# Initialize
git-crypt init

# Ensure your credentials directory exists (also add it to .gitignore to prevent leaking)
mkdir -p config/credentials

# Export your key (run in project root)
git-crypt export-key config/credentials/development.key
```

## Exporting your GPG public key

To display the needed information for available GPG keys on your system:

```shell
gpg --list-keys
```

Look for the string of alphanumeric characters listed for `pub` - this is the `keyID` you will need for the following command:

```shell
# Export a public key
gpg --armor --export <KeyID>
```

## Importing a GPG public key

As a user with project access, you can add other repository users (this will require a code change). This process starts by importing the GPG public key for the user you are about to add:

```shell
# Import their public key into your GPG keychain
gpg --import an-exported-user-public-key.gpg
```

Next, you will need to run git-crypt to add that user to the project:

```shell
git-crypt add-gpg-user <gpg-username-or-github-email-address>
```

## Working with the `git-crypt` encryption key

If the encryption key has been securely provided, save the contents of the file to `<project-root>/config/credentials/development.key` and this will be read when you run `yarn unlock`. **You will need to unlock the project to view/modify the contents of encrypted credentials files (like `packages/cms/.env.development`)**.

## Checking encryption status

```shell
git-crypt status
```
