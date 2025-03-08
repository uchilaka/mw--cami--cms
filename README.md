# `@uchilaka/mw--cami--cms`

Monorepo with:

- Marketing Website (MW)
- Customer Account Management & Invoicing (CAMI)
- Content Management System (CMS)

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
