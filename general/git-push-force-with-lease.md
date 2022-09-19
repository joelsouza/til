# Safer git push --force

`--force-with-lease` is a safer option that will not overwrite any work on the remote branch if more commits were added to the remote branch.

Syntax:

```bash
--[no-]force-with-lease
--force-with-lease=<refname>
--force-with-lease=<refname>:<expect>
```

From git documentation:

> `--force-with-lease` alone, without specifying the details, will protect all remote refs that are going to be updated by requiring their current value to be the same as the remote-tracking branch we have for them.
> `--force-with-lease=<refname>`, without specifying the expected value, will protect the named ref (alone), if it is going to be updated, by requiring its current value to be the same as the remote-tracking branch we have for it.
> `--force-with-lease=<refname>:<expect>` will protect the named ref (alone), if it is going to be updated, by requiring its current value to be the same as the specified value `<expect>` (which is allowed to be different from the remote-tracking branch we have for the refname, or we do not even have to have such a remote-tracking branch when this form is used). If `<expect>` is the empty string, then the named ref must not already exist.
