# Wildcards & Replacements

## Expansion

Usage example:

```bash
  touch file-{1,2,3,4}.txt
  # file-1.txt  file-2.txt  file-3.txt  file-4.txt

  touch file-{1..4}.txt
  # file-1.txt  file-2.txt  file-3.txt  file-4.txt

  touch file-{a..c}.txt
  # file-a.txt  file-b.txt  file-c.txt

  # with scape every "n" occurrences
  echo {0..100..10}
  # 0 10 20 30 40 50 60 70 80 90 100

  # with permutations
  echo {a..c}{1..3}
  # a1 a2 a3 b1 b2 b3 c1 c2 c3
```
