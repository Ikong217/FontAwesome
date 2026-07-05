# FontAwesome Icons for Filament

Expand your icon choices in [Filament](https://filamentphp.com) beyond the default Heroicons. This package brings in the **free** icon set from [Font Awesome](https://fontawesome.com/search?ic=free) as ready-to-use PHP enums, so you can drop them straight into any Filament component that accepts an icon.

## Why?

Filament ships with Heroicons out of the box, which is great — but limited. If you need more variety (brand icons, extra styles, more coverage for niche use cases), this package gives you access to the full Font Awesome **Free** collection (Solid, Regular, and Brands) without needing a Pro license.

## Requirements

- PHP 8.1+
- Filament 3.x
- Font Awesome Free (icons are bundled — no separate FA account or license needed)

## Installation

Install via Composer:

```bash
composer require your-vendor/filament-fontawesome-icons
```

> Replace `your-vendor/filament-fontawesome-icons` with your actual package name once published.

## Usage

### Option 1: Add it directly to your project

If you don't want to install it as a package, you can just copy the enum(s) straight into your app, for example under:

```
app/Enums/
```

This is the same approach used internally — no extra configuration needed, it just works like any other enum in your project.

### Option 2: Use a custom location/namespace

If you'd rather keep it somewhere else (e.g. `app/Support/Icons` or `app/Filament/Icons`), just move the file there and update the namespace at the top to match, for example:

```php
namespace App\Filament\Icons;
```

### Option 3: Install via Composer (vendor package)

If installed as a Composer package, the enum will be autoloaded from the vendor namespace and ready to use right away — no publishing step required.

### Using the icons

Once available, reference the icon anywhere Filament accepts an icon string or enum, e.g.:

```php
use App\Enums\FontAwesomeIcon;

Forms\Components\TextInput::make('name')
    ->prefixIcon(FontAwesomeIcon::User),
```

```php
Actions\Action::make('export')
    ->icon(FontAwesomeIcon::FileExport),
```

Works the same way in table columns, navigation items, buttons, and any other Filament API that takes an icon.

## Icon Coverage

Includes all icons available in the **Font Awesome Free** tier:

- Solid style
- Regular style
- Brands style

Pro-only icons are **not** included.

## Contributing

Found a missing icon, a naming issue, or want to help keep this in sync with new Font Awesome releases? Contributions are welcome — feel free to open an issue or a pull request.

## License

This package is open-sourced under the [MIT license](LICENSE). Font Awesome Free icons are used under the [Font Awesome Free License](https://fontawesome.com/license/free).
