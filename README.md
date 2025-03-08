# `@uchilaka/mw--cami--cms`

Monorepo with:

- Marketing Website (MW)
- Customer Account Management & Invoicing (CAMI)
- Content Management System (CMS)

## Running the app for the first time

### 1. Install dependencies

```shell
# Install system dependencies
brew bundle 

# Install NPM dependencies
yarn cms:setup
```

### 2. Set up git-crypt

Ensure a GPG key linked to your account has been added by a user with access to the project. Review the [using git-crypt guide](./md/GIT-CRYPT.md) for details on getting setup. **You will need to complete this step to setup your `packages/cms/.env` file with secrets needed to run the CMS services**.

You can also try setting the git-crypt key to `<repo-root>/.git/git-crypt/keys/default`.

## 3. Set up hostname(s)

### Update `/etc/hosts`

First, add this line to your `/etc/hosts` file (e.g. with `sudo nano /etc/hosts`):

```shell
127.0.0.1  cms.larcity.local
```

### Run the script to symlink the NGINX server configuration

```shell
bin/setup-server-config
```

### 4. Start the CMS

```shell
yarn cms:develop
```

## Using the GraphQL Explorer

Ensure you have completed the steps to setup your hostname, then visit: <http://cms.larcity.local/graphql>

## Troubleshooting issues

Review the notes on [troubleshooting your local environment](./md/TROUBLESHOOTING.md)

## Resources

- [Food Advisor demo app](https://github.com/strapi/foodadvisor)
- [Tutorials](https://strapi.io/blog/categories/tutorials)
- [Strapi client guide](https://docs.strapi.io/dev-docs/api/client)
- [Customization guide](https://docs.strapi.io/dev-docs/customization)
- [Templates](https://github.com/strapi/strapi/tree/develop/templates)
- [What are document service middleware?](https://strapi.io/blog/what-are-document-service-middleware-and-what-happened-to-lifecycle-hooks-1)
- [Using built-in plugins](https://docs.strapi.io/dev-docs/plugins/using-plugins)
- [Discord](https://discord.com/invite/strapi)
- [Forum](https://forum.strapi.io/)
- [Awesome Strapi](https://github.com/strapi-community/awesome-strapi)
