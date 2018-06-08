# lando-git-hook

Based on https://github.com/lando/lando/issues/904

Add the following to .git/hooks/pre-commit:
```
#!/bin/bash

echo "Output of 'lando'"
lando -- -v

echo "Output of 'lando drush'"
lando drush -- -v
```
