## Optionals

[Optionals][sbopt] encode the presence or absence of a value in its type.

> An optional says:
>
> - There is a value, and it equals x, or
> - There isn’t a value at all

In languages without the [option type][optt], *every* type can be nullable,
with null hanging around every corner waiting to jump out at you. With
optionals, we can not only identify to the reader where null might pop up, but
we can use option unwrapping to properly handle such cases.

### Further reading

- [Option type (Wikipedia)][optt]
- C++’s [`std::optional` template][cppopt]

[optt]: https://en.wikipedia.org/wiki/Option_type
[cppopt]: http://en.cppreference.com/w/cpp/experimental/optional

[sbopt]: https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/Swift_Programming_Language/TheBasics.html#//apple_ref/doc/uid/TP40014097-CH5-XID_428
