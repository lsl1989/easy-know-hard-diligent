---
id: redis-list
title: Redis For List
---
## Redis - list

## Command

### Get Value

> lrange key start stop

start or stop can be negative. -1 means the first one from right to left.

```redis
127.0.0.1:6379> lrange li 0 -1
1) "a"
2) "c"
3) "b"
```

### Insert value into list

> rpush key value [value ...]  
lpush key value [value ...]

push value from left or right to list key.

```reids
127.0.0.1:6379> lpush li x1 x2 x3
(integer) 6
127.0.0.1:6379> rpush li y1 y2 y3
(integer) 9
127.0.0.1:6379> lrange li 0 -1
1) "x3"
2) "x2"
3) "x1"
4) "a"
5) "c"
6) "b"
7) "y1"
8) "y2"
9) "y3"
```

> linsert key before|after pivot value

this command will found the first one which matches the pivot. and insert value before or after the pivot.
```redis
127.0.0.1:6379> lrange li 0 -1
1) "a"
2) "c"
3) "b"
127.0.0.1:6379> linsert li before c x
(integer) 4
127.0.0.1:6379> linsert li after c y
(integer) 5
127.0.0.1:6379> lrange li 0 -1
1) "a"
2) "x"
3) "c"
4) "y"
5) "b"
```
