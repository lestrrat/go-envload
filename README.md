# go-envload

Restore environment variables, so you can break 'em

# WARNING

This repository has been moved to [github.com/lestrrat-go/envload](https://github.com/lestrrat-go/envload). This repository exists so that libraries pointing to this URL will keep functioning, but this repository will NOT be updated in the future. Please use the new import path.

# SYNOPSIS

# DESCRIPTION

Certain applications that require reloading of configuraiton from
environment variables are sensitive to these values being changed.

Or maybe you are writing a test that wants to temporarily change the
value of an environment variable, but you don't want it to linger afterwards.

In other languages this can be done with a "temporary" variable, like in
Perl5:

```perl
use strict;
use 5.24;

sub foo {
  $ENV{IMPORTANT_VAR} = "foo";
  say $ENV{IMPORTANT_VAR}; # "foo"

  {
    local %ENV = %ENV; # inherit the original %ENV,
    $ENV{IMPORTANT_VAR} = "bar";
    say $ENV{IMPORTANT_VAR}; # "bar"
  }
  # 

  say $ENV{IMPORTANT_VAR}; # "bar"
}
```

This library basically allows you to do this in Go
