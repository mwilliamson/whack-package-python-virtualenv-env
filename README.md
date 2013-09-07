# whack-package-python-virtualenv-env

[Whack](https://github.com/mwilliamson/whack) package for Python virtualenvs.
Allows reloctable virtualenvs to be created using whack.

Run `whack deploy ${env_path} --in-place` after installing additional scripts
to create appropriate scripts under `${env_path}/bin`.

This package is compatible with Whack 0.6 and 0.7.

## Example

```
$ whack install \
    git+https://github.com/mwilliamson/whack-package-python-virtualenv-env.git \
    venv
$ venv/bin/pip install glances
(Snipping pip output)
$ whack deploy venv --in-place
$ # Now we can copy the virtualenv to any other path,
$ # and it will continue to work
$ mv venv venv2
$ venv2/bin/glances -v
Glances version 1.7.1 with PsUtil 1.0.1
```

Compared to attempting to move the virtualenv without Whack:

```
$ virtualenv venv
$ venv/bin/pip install glances
(Snipping pip output)
$ mv venv venv2
$ venv2/bin/glances -v
bash: venv2/bin/glances: /tmp/venv/bin/python: bad interpreter: No such file or directory
```

## Alternatives

virtualenv itself supports a `--reloctable` argument.
However, to quote from the package itself:

> The --relocatable option currently has a number of issues, and is not guaranteed to work in all circumstances. It is possible that the option will be deprecated in a future version of virtualenv.
