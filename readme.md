## What is Singleton?

The Singleton pattern is a design pattern that restricts the instantiation of a class to a single instance. It is
commonly used to represent shared resources, such as configuration settings, logging services, or database connections.

---

## Why Use it ?

- Ensures only one instance of a class is created.
- Supports lazy initialization (instance is created only when needed).
- Simple and easy-to-use API.
- Provides a utility method to check if a class follows the Singleton pattern.

---

## Installation

Install the library via Composer:

```bash
  composer require atekushi/singleton
```

## Usage

Just extend the singleton class to your target class

```php
include 'vendor/autoload.php';

use Atekushi\Singleton\Singleton;

class Config extends Singleton
{
    private array $settings;

    protected function __construct(array $settings = [])
    {
        $this->settings = $settings;
    }

    public function get(string $key, $default = null)
    {
        return $this->settings[$key] ?? $default;
    }
}

// Usage
$config = Config::getInstance(['app_name' => 'MyApp', 'debug' => true]);
echo $config->get('app_name');
```