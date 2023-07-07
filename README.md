# yampy

So you want to use python to manipulate some YAML files. No problem, you just add PyYAML to your requirements and go to town, right?

Here's the problem with that - it's yet another requirement, a huge bloated library to handle 99.8% of the YAML RFC specification. Take a guess how many actual YAML files exist to use 99.8% of the spec? Order of 0.

6,000 lines of code and 250 KB of files just to parse a YAML document? That seems excessive.

And thus yampy was born. Pronounced like the proper name for a sweet potato and the word pie, so lots of room for mascots and memes.

## requirements

Python 3.5+

## usage

Add the single file to your project, use it like so:

```python
from yampy import parse, render

with open(file) as s:
    data = s.read()
    parsed = parse(data)
    print(render(parsed))
```

There is a debug flag called \_DEBUG in the file you can flip on to get detailed information as it processes the data.

There are only two functions:
`parse(data)` - take a block of text with line breaks and parse it
`render(data)` - take a dictionary or list and render it back into printable YAML

## notes

This is NOT a drop-in replacement for PyYAML at all, and does not purport to be. 

It doesn't know anything about quotes or multi-line blocks or chomping (|, >, +, -) and will break on % directives.

It also automatically removes all document separators (---) and comments (#).

Spacing is fixed at 2 (so if your source document has some other number, it won't be render-perfect).
