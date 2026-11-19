# FontAwesome Icons for Filament

Expand your icon choices in [Filament](https://filamentphp.com) beyond the default Heroicons. This package provides a single PHP enum covering the **free** [Font Awesome](https://fontawesome.com/search?ic=free) icon set (v7 metadata), built on top of [`owenvoke/blade-fontawesome`](https://github.com/owenvoke/blade-fontawesome), so you get free icons directly usable anywhere Filament accepts an icon.

## Why?

Filament ships with Heroicons out of the box, which is great — but limited. `owenvoke/blade-fontawesome` already registers every Font Awesome Free icon as a Blade Icon component (e.g. `<x-fas-cloud/>`), and since Filament resolves icon strings through Blade Icons under the hood, those same component names (`fas-cloud`, `far-bell`, etc.) work directly as Filament icon values. This package just wraps them in a typed enum so you get autocomplete instead of memorizing icon slugs.

## What's included

- **1,422 Solid icons** (`fas-`) — the full Free solid set.
- **169 Regular/Outlined icons** (`far-`) — generated as `Outlined{Name}` cases, for the subset of icons that ship an outlined counterpart.
- Brand icons (`fab-`, e.g. GitHub, X/Twitter) are **not** included — they're a separate style family. Add a separate `FontAwesomeBrand` enum if you need those.

## Requirements

- PHP 8.1+
- Laravel 12.x (per current `owenvoke/blade-fontawesome` requirements)
- Filament 3.x
- [`owenvoke/blade-fontawesome`](https://github.com/owenvoke/blade-fontawesome) (see installation below)

## Installation

<!-- Install the underlying Font Awesome Blade Icons package:

```bash
composer require owenvoke/blade-fontawesome
```

Then add the `FontAwesome` enum to your project — either copy it in directly or install it as its own package (see below).

### Option 1: Drop it into your project directly

Copy the enum file into:

```
app/Enums/FontAwesome.php
```

It works like any other native PHP enum, no extra config required beyond having `owenvoke/blade-fontawesome` installed.

### Option 2: Custom location/namespace

Prefer to keep it elsewhere (e.g. `app/Support/Icons`)? Move the file and update the namespace at the top to match:

```php
namespace App\Support\Icons;
```

### Option 3: Install as a Composer package

If you package this up yourself, once installed the enum autoloads from the vendor namespace and is ready to use immediately. -->

### Option 1: install via composer

Install the package and owenvoke/blade-fontawesome is already attached

```bash
composer require ikongdev/font-awesome
```

### Option 2: Create Your Own Enum

#### Step 1: Donwload the file

You can Download the enum file located inside source(src) folder

#### Step 2: Change the namespace

after downloading, it is recommended for you to put the file inside App\Enums\ folder
[click to redirect to the file](https://github.com/Ikong217/FontAwesome/blob/feature/add-composer-to-to-make-a-package/src/FontAwesome.php)
change the namespace using:

```
namespace App\Enums;
```

or which folder it is located on your project

#### Step 3: Install dependency

You must install the depenency ovenvoke/blade-fontawesome to make it work.

```bash
composer require owenvoke/blade-fontawesome
```

## Usage

Each case's value matches the Blade Icon component name registered by `owenvoke/blade-fontawesome`, so you can pass it straight to Filament:

```php
use App\Enums\FontAwesome;

Forms\Components\TextInput::make('name')
    ->prefixIcon(FontAwesome::User->value), // "fas-user"
```

```php
Actions\Action::make('export')
    ->icon(FontAwesome::FileExport->value), // "fas-file-export"
```

You can also use the icons directly in Blade views, since they're registered Blade Icon components:

```blade
<x-fas-user class="w-5 h-5" />
```

### Solid vs. Outlined

Most icons are solid-only, but 169 also have an outlined counterpart:

```php
FontAwesome::Bell->hasOutline();      // true
FontAwesome::Bell->outlined();        // FontAwesome::OutlinedBell
FontAwesome::OutlinedBell->solid();   // FontAwesome::Bell

FontAwesome::User->hasOutline();      // false
FontAwesome::User->outlined();        // null
```

### Other helpers

```php
FontAwesome::User->iconName();     // "user"
FontAwesome::User->getIconClass(); // "fas fa-user" (for webfont/CSS-class based rendering, not Blade Icons)
```

> Note: `getIconClass()` / `getIconForSize()` / `sizeClass()` target the classic Font Awesome webfont + CSS approach (useful if you're rendering icons outside of Blade Icons/Filament). For Filament and Blade usage, stick to `->value` as shown above.

## Contributing

Found a missing icon, a naming issue, or want to help keep this in sync with new Font Awesome releases? Contributions are welcome — feel free to open an issue or a pull request.

## License

This package is open-sourced under the [MIT license](LICENSE). Font Awesome Free icons are used under the [Font Awesome Free License](https://fontawesome.com/license/free). Icon rendering is powered by [`owenvoke/blade-fontawesome`](https://github.com/owenvoke/blade-fontawesome), also MIT licensed.
