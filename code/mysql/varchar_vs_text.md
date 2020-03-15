# Difference between VARCHAR vs TEXT

---
**`TEXT`**

- fixed max size of 65535 characters (you cannot limit the max size)
- takes 2 + `c` bytes of disk space, where `c` is the length of the stored string.
- cannot be (fully) part of an index. One would need to specify a prefix length.

**`VARCHAR(M)`**

- variable max size of `M` characters
- `M` needs to be between 1 and 65535
- takes 1 + `c` bytes (for `M` &le; 255) or 2 + `c` (for 256 &le; `M` &le; 65535) bytes of disk space where `c` is the length of the stored string
- can be part of an index


Ref: https://stackoverflow.com/questions/25300821/difference-between-varchar-and-text-in-mysql/25301046
