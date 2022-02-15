# Examples

```php
enum Status {
  case DRAFT;
  case PUBLISHED;
  case ARCHIVED;
}

enum AccountStatus {
  case Active;
  case Blocked;
  case Disabled;
}

enum Decision {
  case Yes;
  case No;
  case Maybe;
}

Chess {
  case Pawn;
  case Knight;
  case Bishop;
  case Rook;
  case Queen;
  case King;
}

enum Direction {
  case North = 0;
  case East = 90;
  case South = 180;
  case West = 270;
}

enum httpStatus {
  case ClientErrorBadRequest = 400;
  case ClientErrorConflict = 409;
  case ClientErrorExpectationFailed = 417;
  case ClientErrorFailedDependency = 424;
  case ClientErrorForbidden = 403;
  case ClientErrorGone = 410;
  // Etc...
}
```
