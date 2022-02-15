# Why should we learn a new data type?

Imagine an app for playing chess. One of the functions is responsible for promoting pawns that make it to the other side of the board. It takes one input `$piece` to specify the piece that the pawn will become.

```php
function promote($piece) {
  // ...do the things to promote a pawn to a new piece...
}
```

A teammate working on this project will not inherently know the acceptable types of input. They may try different values:

```php
// Are any of these correct?
function promote('Queen');
function promote('rook');
function promote(2);
```

One way to improve this code is by adding type hinting to the input. Scalar types have been a part of PHP since version 7. Specifying that the input must be a string will help developers better understand what is expected for this function and will provide better errors if the wrong type of data is passed.

```php
function promote(string $piece) {
  // ...do the things to promote a pawn to a new piece...
}
```

This is good but not great. There is still a lot of room for mistakes. In a chess game, a limited number of pieces exist. Furthermore we need to refer to these pieces in a standard way so that the program can make sense of the input.

```php
// Just because they are strings doesn't mean they are correct.
function promote('Queen');
function promote('queen');
function promote('Castle');
function promote('Horsey');
function promote('Megatron');
```

Before enums we may have used a series of variables, a helper class, or an array to organize these related constants. This leads to verbose solutions.

```php
const PIECES = ['Pawn', 'Knight', 'Bishop', 'Rook', 'Queen', 'King'];

function promote(string $piece) {
  if (!in_array($piece, PIECES)) {
    // Throw error and exit function.
  }
  // ...do the things to promote a pawn to a new piece...
}
```

Now with enums we can create a datatype that directly addresses this set of values. This supports DRY coding principles by organizing a list of related constants into something that can be used in a meaningful way across many parts of the application.

```php
enum ChessPiece {
  case Pawn;
  case Knight;
  case Bishop;
  case Rook;
  case Queen;
  case King;
}

function promote(ChessPiece $piece) {
  // ...do the things to promote a pawn to a new piece...
}
```
