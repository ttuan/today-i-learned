# Vim delete line with pattern

In Normal mode:

* Delete lines that contain a certain word: `:g /word/d`
* Delete lines that doesn't contain certain word: `:%g! /word/d` or `:v/word/d`
* Delete lines that begin with a certain letter (ex: A): `:g/^A/d`
* Delete all blank lines: `:g/^$/d`
