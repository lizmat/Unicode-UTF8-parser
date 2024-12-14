[![Actions Status](https://github.com/raku-community-modules/Unicode-UTF8-parser/actions/workflows/linux.yml/badge.svg)](https://github.com/raku-community-modules/Unicode-UTF8-parser/actions) [![Actions Status](https://github.com/raku-community-modules/Unicode-UTF8-parser/actions/workflows/macos.yml/badge.svg)](https://github.com/raku-community-modules/Unicode-UTF8-parser/actions) [![Actions Status](https://github.com/raku-community-modules/Unicode-UTF8-parser/actions/workflows/windows.yml/badge.svg)](https://github.com/raku-community-modules/Unicode-UTF8-parser/actions)

NAME
====

Unicode::UTF8-Parser - Convert a Supply of bytes to a Supply of unicode characters

SYNOPSIS
========

```raku
use Unicode::UTF8-Parser;

my $stdin = supply {
    while (my $b = $*IN.read(1)[0]).defined {
        emit($b)
    }
}
my $utf8 = parse-utf8-bytes($stdin);

$utf8.tap({ say "got $_" });
```

DESCRIPTION
===========

Rakudo's built-in UTF8 parser will wait for a possible combining character before `getc()` returns. Using this module, you can read bytes from `$*IN` and use this module to get unicode characters.

The module exports the sub parse-utf8-bytes, which take a `Supply` as input and returns a new `Supply`.

If there are Non-UTF8 bytes in the stream, they will be emitted as Int. You have to implement handling of these yourself ($val ~~ Int).

AUTHOR
======

Karl Rune Nilsen

COPYRIGHT AND LICENSE
=====================

Copyright 2015 - 2017 Karl Rune Nilsen

Copyright 2024 Raku Community

This library is free software; you can redistribute it and/or modify it under the Artistic License 2.0.

