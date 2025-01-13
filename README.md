# SimpleCache

[![Scc Count Badge](https://sloc.xyz/github/boyter/simplecache/)](https://github.com/boyter/simplecache/)

A simple cache implementation using Go generics.

## Why?

While many excellent cache solutions exist, what I often want for smaller projects is a map, with some expiration 
abilities over it. That is intended to full that role. This is because different types can have
different caching needs, such as a small group of items that should never expire, items that should exist in cache
forever only being removed when the cache is full.

### What isn't it

1. A generic cache for anything E.G. redis/memcached
2. Aiming for extreme performance under load
3. Implementing any sort of persistence

# Usage

```go
sc := NewSimpleCache[string]()

_ = sc.Set("key-1", "some value"), Sample{})

v, ok := sc.Get("key-1")
if ok {
	fmt.Println(v) // prints "some value"
}
v, ok = sc.Get("key-99")
if ok {
	fmt.Println(v) // not run "key-99" was never added
}
```

# Benchmarks?

I don't have any. It's a Go map with some locking. It should be fine. Being 5% faster or slower than any other
cache isn't the point here.
