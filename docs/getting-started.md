# Getting started

## Declaring enums

Enums are declared with the reserved `enum` keyword and use syntax similar to classes and interfaces.

```php
enum Status {
  case DRAFT;
  case PUBLISHED;
  case ARCHIVED;
}
```

## Instantiating an enum

Values (also called elements, members, or enumerators) behave like constants on a class. A variable created with an enum may be assigned any of the values.

```php
$newStatus = Status::DRAFT;
```

## Type hinting with enums

The main use case of Enums is type safety. Enums are especially useful when a function requires a limited number of possible inputs. This creates self documenting code and ensures meaningful errors are thrown if the wrong input is sent to the function.

```php
enum Suit {
  case Clubs;
  case Diamonds;
  case Hearts;
  case Spades;
}

function pick_card(Suit $suit) {
  // Some business logic.
}

pick_card(Suit::Clubs);    // ✅ Cool beans.
pick_card(Suit::Diamonds); // ✅ Right on.
pick_card(Suit::Hearts);   // ✅ You got it.
pick_card(Suit::Spades);   // ✅ Groovy.
pick_card('Clubs');        // ❌ Nope! That's a string type.
```

## Backed values and the 'from' methods

Enums have the option of declaring backed values for each of the enumerators. These may be strings or integers. The backed value can be accessed as a property of an instance of the enum. Backed values are read only and must be unique.

```php
enum Direction {
  case North = 0;
  case East = 90;
  case South = 180;
  case West = 270;
}

// Get the value from the enum.
// Has value 180.
$heading = Direction::South->value;

// Create an enum from the value.
// Has value Direction::East.
$bearing = Direction::from(90);

// Backed values are read only similar to a 'final' property.
Direction::South->value = 100; // ❌ Nuh-uh.
```

## Getting All Enum Values

Enums have a `cases` method for listing all enumerators.

```php
enum Status {
  case DRAFT;
  case PUBLISHED;
  case ARCHIVED;
}

// Returns array: [Status::DRAFT, Status::PUBLISHED, Status::ARCHIVED]
Status::cases();
```
