---
toc-title: Table of contents
---

# include-code-files Extension For Quarto

Include code from files in code blocks.

::: code-with-filename
**document.qmd**

```` markdown
---
title: "Include-code-files Example"
filters:
  - include-code-files
---

```{.python include="_snippets/hello_world.py"}
```
````
:::

Adapted from
<https://github.com/pandoc/lua-filters/blob/master/include-code-files/include-code-files.lua>
and written by [Bruno BEAUFILS](https://github.com/b3).

## Installing

``` bash
quarto add SamEdwardes/include-code-files
```

This will install the extension under the `_extensions` subdirectory.
You will want to check in this directory if you're using version
control.

## Using

To use the include-code-files filter, add it to your documents YAML
front matter:

``` yaml
---
title: "My doc"
filters:
  - include-code-files
---
```

With the include-code-files filter, you can include code snippets
directly from a file using `include`. For example, you may have a python
script like this:

::: code-with-filename
**\_snippets/hello_world.py**

``` {.python .number-lines}
for name in ["Sam", "jake"]:
    print(f"Hello {name}!")
```
:::

To render this file in a code chunk, use the `include` attribute:

```` markdown
```{.python include="_snippets/hello_world.py"}
```
````

``` python
for name in ["Sam", "jake"]:
    print(f"Hello {name}!")
```

You can combine this with other quarto attributes like `filename` or
`code-line-numbers`:

```` markdown
```{.python include="_snippets/hello_world.py" filename="hello_world.py" code-line-numbers="true"}
```
````

::: code-with-filename
**hello_world.py**

``` {.python .number-lines}
for name in ["Sam", "jake"]:
    print(f"Hello {name}!")
```
:::

## Example

Here is the source code for a minimal example: [README.qmd](README.qmd).
