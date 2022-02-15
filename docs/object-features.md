# Object features

In PHP, enums are a special type of object. They are defined with class-like syntax and each case acts as a single-instance objet of that class.

## Methods and interfaces

```php
interface ColorCode {
  public function color();
}

enum Status implements ColorCode {
  case DRAFT;
  case PENDING,
  case PUBLISHED;
  case ARCHIVED;

  public function color(): string {
    return match($this) {
      Status::DRAFT, Status::PENDING => 'Orange',
      Status::PUBLISHED => 'Green',
      Status::ARCHIVED => 'Grey',
    };
  }
}
```

## Static methods

Static methods are primarily used an alternative constructor.

```php
enum Status implements  {
  case GENZ;
  case MILLENNIALS,
  case GENX;
  case BOOMER;

  public static function fromYear(int $year) {
    return match(true) {
      $year >= 1997 => static::GENZ,
      $year >= 1981 => static::MILLENNIALS,
      $year >= 1965 => static::GENX,
      $year >= 1955 => static::BOOMER,
    };
  }
}
```

## Differences between enums and classes

```php
// ❌ Properties are not allowed.
enum Foo {
  private string $test;
}

// ❌ Magic methods are not allowed.
enum Bar {
  public function __get() {}
  public function __set() {}
  public function __construct() {}
  // ...not today programmers.
}

// ❌ Can not instantiate with `new`.
$direction = new DIRECTION();

// Enums can be directly compared since each case is a single instance.
new stdClass() === new stdClass(); // False.
Direction::North === Direction::North; // True.
```
