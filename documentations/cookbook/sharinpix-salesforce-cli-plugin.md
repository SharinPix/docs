---
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: false
  tags:
    visible: true
---

# SharinPix Salesforce CLI Plugin

{% embed url="https://github.com/SharinPix/sharinpix-sf-plugin" %}

The SharinPix Salesforce CLI plugin syncs SharinPix forms, permissions, and settings between Salesforce and files on your computer.

Use it to version, review, and deploy SharinPix configuration and files across environments.

### In this article, we will demonstrate how to:

* [Set up Node.js and install the plugin](sharinpix-salesforce-cli-plugin.md#install-the-plugin)
* [Authenticate to Salesforce](sharinpix-salesforce-cli-plugin.md#authenticate-to-salesforce)
* [Discover available commands](sharinpix-salesforce-cli-plugin.md#discover-available-commands)
* [Pull SharinPix configuration locally](sharinpix-salesforce-cli-plugin.md#synchronizing-sharinpix-configuration)
* [Push local changes back to Salesforce](sharinpix-salesforce-cli-plugin.md#synchronizing-sharinpix-configuration)

{% hint style="warning" %}
### Prerequisites

Before you begin, ensure that:

* [Node.js](https://nodejs.org/en/download) is installed
* [Salesforce CLI](https://developer.salesforce.com/docs/atlas.en-us.sfdx_setup.meta/sfdx_setup/sfdx_setup_install_cli.htm) (`sf`) is installed
* You have access to a Salesforce org
* Your Salesforce user has access to SharinPix features
{% endhint %}

### Install the SharinPix Salesforce CLI Plugin

Run the following command to install the plugin:

```bash
sf plugins install @sharinpix/sharinpix-sf-cli
```

### Authenticate to Salesforce

Use the web login flow to connect your org.

#### Connect to a production org

```bash
sf org login web
```

#### Connect to a sandbox or test org

Use `--instance-url` with the Salesforce test login domain:

```bash
sf org login web --instance-url https://test.salesforce.com
```

#### List authenticated orgs:

```bash
sf org list
```

### Commands

#### Discover available commands

Use `--help` to inspect the plugin and each command:

```bash
sf sharinpix --help
sf sharinpix form pull --help
sf sharinpix pull --help
sf sharinpix form push --help
sf sharinpix push --help
```

#### Target org

All plugin commands require a target Salesforce org.

Pass the login username with `-o`:

```bash
-o username@example.com
```

#### Pull SharinPix forms

```bash
sf sharinpix form pull -o username@example.com
```

Use this command when you only need SharinPix forms.

#### Pull all SharinPix configuration

```bash
sf sharinpix pull -o username@example.com
```

This pulls all supported SharinPix configuration from the target org.

#### Push SharinPix forms

```bash
sf sharinpix form push -o username@example.com
```

Use this command when you only need to deploy SharinPix forms.

#### Push all local configuration

```bash
sf sharinpix push -o username@example.com
```

This applies all supported local SharinPix configuration to the target org.

{% hint style="info" %}
#### Info

**Pull** updates files on your computer, and **Push** applies those files to Salesforce.

After each command, check:

* The target org is correct
* The expected files changed
* No errors were reported
{% endhint %}

{% hint style="danger" %}
#### Warning

Some flags, such as `--delete`, can remove Salesforce records that do not exist locally.

Use this only when the files on your computer are the source of truth.
{% endhint %}

{% hint style="success" %}
### Additional information

For the full command reference, see the complete documentation on GitHub:

{% embed url="https://github.com/SharinPix/sharinpix-sf-plugin/blob/main/README.md" %}
{% endhint %}
