# Magebit MCP Suite

A Composer meta-package that installs the [Magebit MCP server](https://github.com/magebitcom/magento2-mcp-module) for Magento 2 together with its core-domain tool modules, so you require one package instead of nine.

It contains no code of its own — only a dependency list. Which modules are actually *active* is decided in `app/etc/config.php`, not by what is installed.

## Installation

```bash
composer require magebitcom/magento2-mcp-suite
bin/magento setup:upgrade
```

Then follow the core module's [Quick Setup guide](https://magebitcom.github.io/magento2-mcp-module/quick-setup/) to issue a token and connect an AI client.

## Turning modules on and off

Each MCP module is an ordinary Magento module, so `app/etc/config.php` is the switch. `1` is enabled, `0` is disabled:

```php
'modules' => [
    // ...
    'Magebit_Mcp' => 1,
    'Magebit_McpCatalogTools' => 1,
    'Magebit_McpCmsTools' => 1,
    'Magebit_McpCustomerTools' => 1,
    'Magebit_McpInventoryTools' => 1,
    'Magebit_McpMarketingTools' => 1,
    'Magebit_McpOrderTools' => 1,
    'Magebit_McpReportTools' => 1,
    'Magebit_McpTaxTools' => 1,
    // Optional add-ons, not part of the suite:
    'Magebit_McpGoogleAnalyticsTools' => 0,
    'Magebit_McpDbTools' => 0,
],
```

Or from the CLI, which edits the same file:

```bash
bin/magento module:disable Magebit_McpReportTools
bin/magento setup:upgrade
```

## License

MIT — see [LICENSE](LICENSE).

---

![Magebit](https://github.com/user-attachments/assets/cdc904ce-e839-40a0-a86f-792f7ab7961f)

Magebit - Full-service e-commerce agency

[magebit.com](https://magebit.com)
