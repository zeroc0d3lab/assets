# Laravel Assets management

## Installation

```bash
composer require zeroc0d3lab/assets
```

For version <= 5.4:

Add to section `providers` of `config/app.php`:

```php
// config/app.php
'providers' => [
    ...
    Zeroc0d3lab\Assets\Providers\AssetsServiceProvider::class,
];
```

And add to `aliases` section:

```php
// config/app.php
'aliases' => [
    ...
    'Assets' => Zeroc0d3lab\Assets\Facades\AssetsFacade::class,
];
```

All assets resource will be manage in config file so we need to publish config to use.

```bash
php artisan vendor:publish --provider="Zeroc0d3lab\Assets\Providers\AssetsServiceProvider" --tag=config
```

Add to your master layout view, in `head` tag:

```php
{!! \Assets::renderHeader() !!}
```

and before `body` tag close:

```php
{!! \Assets::renderFooter() !!}
```

## Methods

### Add scripts

```php
\Assets::addScripts(['key-of-assets-in-config-file']);
```

Example:

```php
\Assets::addScripts(['app', 'bootstrap', 'jquery']);
```

### Add styles

```php
\Assets::addStyles(['key-of-assets-in-config-file']);
```

Example:

```php
\Assets::addStyles(['bootstrap', 'font-awesome']);
```

### Remove scripts

```php
\Assets::removeScripts(['key-of-assets-in-config-file']);
```

Example:

```php
\Assets::removeScripts(['bootstrap']);
```

### Remove styles

```php
\Assets::removeStyles(['key-of-assets-in-config-file']);
```

Example:

```php
\Assets::removeStyles(['font-awesome']);
```

### Others

- Set version for assets. Add to `.env`

```bash
ASSETS_VERSION=1.0
```

Then all assets will be added `?v=1.0`

- Change to online mode

```bash
ASSETS_OFFLINE=false
```

Then assets will be loaded from CDN if it's defined in config file.

- To disable versioning:

```bash
ASSETS_ENABLE_VERSION=false
```

## License
[MIT](LICENSE) © ZeroC0D3 Team
