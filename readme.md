
# henna language

### syntax

- **lisp-like syntax**
  *prefix notation, s-expressions*
  ```(say (add 2 2))```

- **with lots of sugar syntax**
  *all sugar could be represented as expression (and doing so at some point)*

  ```[1 2]```, ```[]``` → ```(lst 1 2)```, ```(lst)```
  ```<lst of=bit>``` → ```(kin lst of=bit)```
  ```{sub (max $2=nums) $1}``` → ```(act [$1 $2=nums] (sub (max $2) $1))```
  ```'hello world!\n'``` → ```(str hello\ world!\\n)```
  ```"hello world!\n"``` → ```(str hello\ world!\\\\n)```

  ```A~```, ```[1 2]~``` → ```(escape A)```, ```(escape [1 2])```
  ```A=B```, ```A,B=C``` → ```(pair A B)```, ```(pair (enum A B) C)```
  ```A...B```, ```A..B``` → ```(range A B)```, ```(range A (dec B))```

  ```# fixme #``` → ```(comment 'fixme')```
  comments starting with ```#``` ends at the end of line or another ```#``` 
  comments starting with ```###``` ends at at the end of file or another ```###``` 

- **batteries**
  *carcinogen syntax sugar*
  
  imitation of infix notation by omitting whitespace between expressions:
  ```4(mul 4)(sub 8)``` → ```(sub (mul 4 4) 8)```
  ```[1 2 4](flip)(fold div)``` → ```(fold (flip [1 2 4]) div)```
  ```B[1..4](pick)``` → ```(pick (at B 1..4))```

  rules:
  ```*(A B C)```, ```*{A B C}``` → ```(A * B C)```, ```{A * B C}```
  ```*<A B>```, ```*A``` → ```(<A B> *)```, ```(A *)```
  ```*[A]```, ```*[A B]``` → ```(at * A)```, ```(at * [A B])```
  ```*'%s'``` → ```(mold '%s' *)```


### other

- **names**

  *lowercase for names*
  to avoid choosing between zlib/Zlib/ZLib/ZLIB

  *uppercase for variables*
  to make them notable from other names
  one letter usually: A/B/C...
  (if you need to have long meaningful names for variables, then you doing something wrong)

- **name choosing** (from more to less important)

  *similar acts should have similar names*
  ```and or xor nand nor xnor``` → ```and ior xor nand nior nxor```
  ```less? equal? greater?``` → ```less? same? more?```
  ```less_or_equal? not_equal? greater_or_equal?``` → ```nmore? nsame? nless?```

  *names should be short*
  ```function lambda``` → ```act```
  ```exception``` → ```fault```
  ```greater?``` → ```more?```
  ```reverse``` → ```flip```

  *names should have meaning*
  ```fn fun``` → ```act```
  ```le?``` → ```nmore?```

  *if theres many apropriate names, the one less used in another languages should be choosed*
  ```function lambda``` → ```act```
  ```error``` → ```fault```
  ```or nor xnor``` → ```ior nior nxor```
  ```equal? greater?``` → ```same? more?```

