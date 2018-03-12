# PHP 7.2

_John Coggeshall_ **https://joind.in/talk/9883d**



PHP 7 is ~50% of installations (only 25% of wordpress)

## Speed

- PHP 7.x much faster than 5.6.
- PHP 7.2 is faster than HHVM.

## Language improvements

- Adds generic `object` type (not necessarily a specific type) for better static typing.

- Bending the rules for matching method signatures in child classes, allows removing type hints for overridden methods, and add return values.

  - Also applies to abstract class.

- Trailing commas are now allowed in more places than just arrays (function parameters, namespaces, object properties, anywhere you can create a list of things with a comma).

- Improved Exif extension.

- Encrypted ZIP files, can be accessed for reading and writing (requires libzip 1.2.0+).

- The ZipArchive class now implements Countable.

- GD Image Library improved

  - BMP image file format.
  - Creating an image clipping region.
  - Drawing open-ended polygons.

- Cryptography

  - Argon2 - new hashing algorithm.

    ```php
    $hash = password_hash($password, PASSWORD_ARGON2I, $options);
    ```

  - Libsodium

    - `sodium_crypto_keypair_from_secretkey_and_publickey($mySecretKey, $$joesPublicKey)`
    - Many more functions

## Deprecations

Things that are headed towards a prompt code death no later than PHP 8.

- `__autoload()` => `spl_autoload_register()` 
- `$PHP_ERRORMSG` => `error_get_last()`
- `create_function()` => closures
- `parse_str($string)` with variable injecton => `parse_str($string, &$out)`
- `each()` => `foreach()`