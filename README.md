# lando-git-hook

Based on https://github.com/lando/lando/issues/904

Run `lando start`.

Create and add the following to .git/hooks/pre-commit:
```
#!/bin/bash

echo "Output of 'lando'"
lando -- -v

echo "Output of 'lando drush'"
lando drush -- -v

echo "Output of 'lando my_script'"
lando my_script -- v
```

Change permissions on the file to be executable
`chmod 755 .git/hooks/pre-commit`

Run `git commit` to see that

* the output of `lando` is full (same as if you would run lando from the
  command line + plus the verbose messages of the initializing scripts prior)
* when running `lando` with a sub-command it is not run (only the initializing
  scripts are).
** `lando drush` should have shown all available commands for,
  drush, as if you would type it into the command line.
** same with `lando my_script` - no output here (only initializing), not though
when executed from the command line.
