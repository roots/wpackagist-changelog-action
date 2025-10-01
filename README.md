# WPackagist Changelog Action

Automatically comment WordPress plugin changelogs on pull requests when WPackagist dependencies change in your `composer.lock` or `composer.json` files.

## Usage

### Basic Setup

Create a workflow file in your repository (e.g., `.github/workflows/wpackagist-changelog.yml`):

```yaml
name: WPackagist Changelog

on:
  pull_request:
    paths:
      - 'composer.lock'
      - 'composer.json'

jobs:
  changelog:
    runs-on: ubuntu-latest
    permissions:
      pull-requests: write
    steps:
      - name: Comment changelogs on PR
        uses: roots/wpackagist-changelog-action@v1
```

## Example Comment

The action creates a formatted comment like this:

> # 🔌 WordPress Plugin Changelogs
>
> ## woocommerce
>
> <details>
> <summary>View changelog</summary>
>
> #### 10.2.2 2025-09-29
> **WooCommerce**
> - Fix - Check if template part is from file system before building the result from file #61171
> - Fix - Fix low-resolution images displayed in the Classic Template block gallery #61182
> - Fix - Make legacy gallery filters available while rendering blocks #61173
>
> [View full changelog on WordPress.org](https://wordpress.org/plugins/woocommerce/#developers)
>
> </details>
