# assorted-pre-commit-hooks / version-tag

[pre-commit] hook to automatically create a [Git] tag for a new software
version.

The hook (which actually runs in the post-commit stage) parses the subject line
of the latest Git commit. If it matches a pattern indicating a new software
version, the version number is extracted from the commit message and used to
create a new Git tag for that version.

To use the hook, add the following to `.pre-commit-hooks.yaml`:

```
default_install_hook_types: [pre-commit, post-commit]

repos:
  - repo: https://github.com/assorted-pre-commit-hooks/version-tag
    rev: # see repository for latest tag
    hooks:
      - id: version-tag
        args: # optional arguments
```

Optional arguments are:

* `--subject-prefix`: Prefix which, when the subject line of the latest Git
  commit, indicates a new software version. The version number is extracted from
  the remainder of the subject line. Default: `Version`

* `--tag-prefix`: Prefix to add to version number to create new Git tag for that
  version. Default: `v`.

* `--git-tag-options`: Options to pass to `git tag` to create the new
  tag. Default: `-a` (creates an unsigned, annotated tag object).

[pre-commit]:   https://pre-commit.com/
[Git]:          https://git-scm.com/
