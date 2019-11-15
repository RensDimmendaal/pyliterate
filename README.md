# PyLiterate for Deckset

This is the tool Brett Slatkin used to write [Effective Python](http://www.effectivepython.com). The workflow is a variation on [Donald Knuth's Literate programming](http://en.wikipedia.org/wiki/Literate_programming). The original repo can be found [here](https://github.com/bslatkin/pyliterate).

The idea is the source code and explanatory text appear interleaved in a [Markdown formatted](https://help.github.com/articles/github-flavored-markdown/) file. Each time you edit a Markdown file, you can re-run the source code it contains using the `run_markdown` tool provided by this project. `run_markdown` will update the file in-place with the new output from running the code. If an unexpected error occurs it will be printed to the terminal instead of overwriting the file.

# This Fork

I (Rens) have forked it and made minimal changes to make it work with markdown files that are intended to be used in [Deckset](https://www.deckset.com/). The original pyliterate had different code fences for running code, expected syntax-errors, and expected exceptions.

```python
a = 5
```

```python-exception
a = 5 + "hello"
```

```python-syntax-error
print("hello')
```

Deckset only understands the first, however it does have a comment syntax `<!-- comment -->`. So I made the small change that makes it work as follows as well:

```python
a = 5
```

<!-- exception -->
```python
a = 5 + "hello"
```

<!-- syntax-error -->
```python
print("hello')
```

The result is that the errors show up in your slide, as intended, without showing the comment.

## Example usage

1. Create a virtual environment:
2. Activate the virtual environment:
3. Install this package in your virtual environment: `pip install -e .`
4. run_markdown your_file.md
