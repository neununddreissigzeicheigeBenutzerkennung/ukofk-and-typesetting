# alist.tex Documentation

This document provides an overview of how to use the `alist.tex` package.

## Control Sequences

### `\copy`

The control sequence `\copy` copies the **definition** of the **control sequence** in `#2` and changes the **definition** of the **control sequence** in `#1`.

```tex
\def\a{a}
\def\b{b}
\copy\a\b
\a % → b
```

Note that since the **definition** is actually copied, it stays the same even if the **control sequence** it was copied from is redefined.

```tex
\def\b{c}
\a % → b
```

In contrast, if you were to just redefine `\a` as `\b`, its value would be bound to the **definition** of `\b`.

```tex
\def\a{\b}
\a % → c
\def\b{d}
\a % → d
```

You can also copy a **control sequence**'s **definition** into itself.

```tex
\copy\a\a
\a % → d
```

### `\append`

The control sequence `\append` appends the **definition** of the **control sequence** in `#2` to the end of the **definition** of the **control sequence** in `#1`.

```tex
\def\a{a}
\def\b{b}
\append\a\b
\a % → ab
```

You can also append a **control sequence**'s **definition** to itself.

```tex
\append\a\a
\a % → abab
```

### `\contextwidth`

The **control sequence** `\contextwidth` takes a `\dimen` register in `#1` and anything in `#2`. It then stores the width `#2` would have, were it written next to the arguments this control sequence previously accepted in `#2`.

```tex
\newdimen\dimena
\newdimen\dimenb
\contextwidth{\dimena}{\advance\dimenb10pt}
\the\dimena % → 0pt
\contextwidth{\dimena}{\vrule width\dimenb}
\the\dimena % → 10pt
```

## Lists

### Basic Lists

The **control sequence** `\list` provides an adjustable method of typesetting lists. Its argument `#1` defines the bullets to be used for the content given in `#2`. The simplest form of list only uses `\item` elements. These are automatically aligned behind the specified bullets.

```tex
\list{-\ }{
\item{This is the content of the first item.}
\item{This is the content of the second item. Items may consist of multiple rows. For a text of sufficient length I had to strain my imagination.}
}
```

The previous code produces the following list:

- This is the content of the first item.
- This is the content of the second item. Items may consist of multiple rows. For a text of sufficient length I had to strain my imagination.

### Numbered Lists

`\bullet` is defined such that bullets may be influenced by previous ones in the same list. Bullets may also be redefined within a list. This can happen either in bullets or in between items. The content of items is encapsulated and can therefore not influence `\bullet`.

```tex
\newcount\bulletcount
\list{\advance\bulletcount1 \number\bulletcount)\ }{
\item{Using this method one can number items. This item is labeled the first.}
\item{This item is labeled second. It's number conveniently increased without extra work.}
{\def\bullet{$\bullet$\ }
\item{Bullets may also be redefined in between any two items.}}
\item{When counting}
\item{high enough}
\item{you will see,}
\item{that}
\item{the list}
\item{automatically}
\item{chooses}
\item{the appropriate spacing.}
\def\bullet{.}
\item{a}
}
```

The previous code produces the following list:

1. Using this method one can number items. This item is labeled the first.
2. This item is labeled second. It's number conveniently increased without extra work.
   - Bullets may also be redefined in between any two items.
3. When counting
4. high enough
5. you will see,
6. that
7. the list
8. automatically
9. chooses
10. the appropriate spacing.

### Mixed Content Lists

You can't just redefine `\bullet` in between `\item`s but also put regular text.

```tex
\list{-\ }{
\item{The text below this item is not an item itself.}
\noindent This is not an item.
\item{The text above this item is not an item itself.}
}
```

The previous code produces the following list:

- The text below this item is not an item itself.
  
  This is not an item.
- The text above this item is not an item itself.

### Nested Lists

Lists can also be nested within other lists.

```tex
\list{$\bullet$\ }{
\item{\list{-\ }{
  \item{Some text.}
  \item{\dots}
}}
\item{Second item.}
}
```

The previous code produces the following list:

- - Some text.
  - \dots
- Second item.