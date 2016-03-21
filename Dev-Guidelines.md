# Roundcube Development Guidelines

Here are a few rules and explanations that should make it easier for new contributors to understand the structure and guidelines of the Roundcube code base.

## Available Documentation

The code is not very well documented but using the PHPDoc comments we finally made it to create a class and functions overview. More details can be found at the [Roundcube Documentation](Dev-Docs) page.

## Naming conventions

### File names

In general all files should have the appropriate extension such as .php, .js, etc. For PHP include files that are not meant to be executed directly please use the extension _.inc_. This prevents them from being executed directly in case that the access restrictions do not work as intended.

All files should be named with lower case letters and _underlines_ (for word separation).

Because RoundCube uses PHP autoloading technology, classes need to be saved in a file named _class_name.php_ within `program/include/` to be included on demand.

### Classes, functions and variables

All class, function and variable names should only contain _lower case_ letters and numbers and use _underlines_ for word separation. No [CamelCase](http://en.wikipedia.org/wiki/CamelCase) please.

Functions providing Roundcube specific functionality should start with either `rcmail` (webmail specific functions) or `rcube` (global/framework functions).

Class names should start with `rcube`.


## Code style

All code (PHP and JavaScript) obeys the same code style guidelines:
 * Opening and closing brackets for function and class definitions are on a _new line_
 * Never write control-flow code on a line
 * Code should not exceed a limit of 80 characters per line 
 * Never omit brackets for blocks containing only one statement
 * Indentation consists of _4 spaces_ per level and no tabs!
 * Conventional operators should be surrounded by _a space_
 * Commas should be followed by _a space_
 * Semi-colons in for statements should be followed by _a space_
 * All names should be written in English
 * A function should have only one return statement at the end
 * Logical units within a block should be separated by at least one blank line
 * Iterator variables should be called "i", "j", "k", etc.
 * Globals vars (PHP) should be named in _upper case_ but better be avoided.
 * Variables should be initialized where they are declared and they should be declared in the smallest scope possible
 * _In general_, we adhere to [PEAR CS](http://pear.php.net/manual/en/standards.php)

Good code:
```php
    function foo_bar($aa, $bb)
    {
        $out = '';
    
        if ($aa == 1 || $aa > 10) {
            $out .= "Case one\n";
            write_log("Foo: $aa");
        }
        else {
            alert('Bar');
        }
    
        for ($i=0; $i < $bb; $i++) {
            $out .= $i . 'a';
        }
        return $out;
    }
```

_The bracket indentation of the existing code differs from this example but I guess we should move towards this more common indentation style._

Bad code:
```php
    function fooBar($aa,$bb) {
      if ($aa==1 || $aa>10){
        $out.="Case one\n";
        write_log("Foo: $aa");
      } else {
        alert("Bar");
      }
      for ($i=0;$i<$bb;$i++)
        $out.=$i."a";
    
      return $out;
    }
```

## PHP Coding

All code should be functional in PHP 5.3.x and higher. When working with files please also make sure that the code works with _safe_mode_ enabled. Set error reporting to E_NOTICE to see if all variables are properly declared.

## Comments/Documentation

Please add comments to logical code blocks giving a short description what this part is intended to do.
For PHP classes, please add [PHPDoc](http://www.phpdoc.org) styled descriptions for public methods. Private method descriptions are optional.

