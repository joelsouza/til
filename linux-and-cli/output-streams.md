# Output Streams: Stdout and Stderr are different places

To redirect just `stdout` we use `1>` and we use `>2` if we want to redirect just errors.

```bash
ls -lsah 1> ls.txt
cat ls.txt

# total 16K
# 4.0K drwxr-xr-x 2 root root 4.0K Jun 24 12:33 .
# 4.0K drwxr-xr-x 1 root root 4.0K Jun 24 12:33 ..
#    0 -rw-r--r-- 1 root root    0 Jun 24 12:33 ls.txt

cat non-existant-file.txt 2> error.txt
cat error.txt
# non-existant-file.txt: No such file or directory

# or both at the same time
# ls -lsah 1> ls.txt 2> error.txt
```

If we want to redirect both to the same place we use just use the usual `>`

```bash
  ls -lsah > ls.txt
```
