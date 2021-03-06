# VNDR

[![Build Status](https://travis-ci.org/LK4D4/vndr.svg?branch=master)](https://travis-ci.org/LK4D4/vndr)

Vndr is simple vendoring tool, which is inspired by docker vendor script.
Vndr has no options.
For initiating you will need config `vendor.conf` with lines like:
```
# Import path             | revision                               | Repository(optional)
github.com/example/example 03a4d9dcf2f92eae8e90ed42aa2656f63fdd0b14 https://github.com/LK4D4/example.git

```
Just set `$GOPATH` and run `vndr` in your repository with `vendor.conf`.
Repository field is used for vendoring forks instead of original repos.

Also it's possible to vendor only one dependency after initial vendoring:
```
vndr github.com/example/example 03a4d9dcf2f92eae8e90ed42aa2656f63fdd0b14 https://github.com/LK4D4/example.git
```
or
```
vndr github.com/example/example
```
to take revision and repo from `vendor.conf`.

If you experience any problems, please try to run `vndr -verbose`.

# Known issues

* `vndr` vendors only top packages, i.e. `golang.org/x/net` and not
`golang.org/x/net/trace`. If there is "non-top" packages in `vendor.conf`, `vndr`
might fail badly.
* if you use symlinks for managing `GOPATH` or packages in it, `vndr` might not
be able to work properly.
