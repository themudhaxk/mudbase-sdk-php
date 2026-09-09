# MUDBASE PHP SDK

Mudbase is a backend platform: authentication, a schema-driven database, file storage, serverless functions, webhooks, and real-time and transactional messaging behind one API. The PHP SDK is a native PHP client for that API, so you can manage users and organizations, define collections and query data, store and serve files, invoke functions, and configure webhooks without hand-rolling HTTP requests.

## Installation

```bash
composer require mudbase/sdk
```

## Quickstart

```php
<?php
require_once __DIR__ . '/vendor/autoload.php';

use MudbaseSDK\Api\CollectionsApi;
use MudbaseSDK\Configuration;

$config = Configuration::getDefaultConfiguration()->setApiKey('ApiKeyAuth', 'YOUR_API_KEY');
$collections = new CollectionsApi(new GuzzleHttp\Client(), $config);

$result = $collections->listCollections('YOUR_PROJECT_ID');
print_r($result->getCollections());
```

## What you can do

- **Authentication** - sign-up, sign-in, sessions, and API key management
- **Database** - schema-defined collections with typed CRUD and filtered queries
- **Storage** - buckets and file uploads and downloads
- **Realtime** - WebSocket events and live data subscriptions
- **Functions** - deploy and invoke serverless functions
- **Messaging** - transactional email, SMS, and push notifications
- **Webhooks** - configurable delivery with retry and logs
- **Roles & permissions** - project-level access control

## Documentation

- **Docs & API reference:** https://docs.mudbase.dev
- **Product:** https://mudbase.dev

## Support

Questions or issues: open one at https://github.com/themudhaxk/mudbase-sdk-php, or reach us at support@mudbase.dev.
