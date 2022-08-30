# Leaky Redwood+Jest 😬

This repo is to demonstrate how the `jest` setup included with Redwood causes a memory leak.

I've added a bunch of very simple test files `./api/src/*.test.ts` that test `1 + 1 == 2`. 

If you run via:

```sh
node --expose-gc $(which yarn) jest --runInBand --logHeapUsage ./api/src/*.test.ts
```

The output on my machine shows the heap gradually creeping up:

```
 PASS   api  api/src/15.test.ts (154 MB heap size)
 PASS   api  api/src/2.test.ts (236 MB heap size)
 PASS   api  api/src/13.test.ts (315 MB heap size)
 PASS   api  api/src/1.test.ts (393 MB heap size)
 PASS   api  api/src/5.test.ts (473 MB heap size)
 PASS   api  api/src/16.test.ts (326 MB heap size)
 PASS   api  api/src/19.test.ts (404 MB heap size)
 PASS   api  api/src/8.test.ts (482 MB heap size)
 PASS   api  api/src/11.test.ts (561 MB heap size)
 PASS   api  api/src/7.test.ts (453 MB heap size)
 PASS   api  api/src/9.test.ts (525 MB heap size)
 PASS   api  api/src/10.test.ts (604 MB heap size)
 PASS   api  api/src/20.test.ts (682 MB heap size)
 PASS   api  api/src/0.test.ts (762 MB heap size)
 PASS   api  api/src/14.test.ts (606 MB heap size)
 PASS   api  api/src/18.test.ts (686 MB heap size)
 PASS   api  api/src/3.test.ts (763 MB heap size)
 PASS   api  api/src/6.test.ts (842 MB heap size)
 PASS   api  api/src/4.test.ts (672 MB heap size)
 PASS   api  api/src/12.test.ts (751 MB heap size)
 PASS   api  api/src/17.test.ts (829 MB heap size)
```
