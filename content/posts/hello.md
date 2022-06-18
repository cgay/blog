+++
draft = false
date = 2022-06-15T14:05:37Z
title = "Hello"
description = "description"
slug = ""
authors = []
tags = []
categories = []
externalLink = ""
series = []
+++

Greetings! I'll be using this space to write about technical things, mostly
revolving around my hobby, the [Dylan](https://opendylan.org) programming
language.

Since I'll be mostly writing about geeky Dylan stuff, let's see if my website
software, Hugo, knows how to highlight Dylan code. It should, since I
[added](https://github.com/alecthomas/chroma/pull/466) a Chroma lexer for it.

```dylan
define class <point> (<object>)
  slot point-x :: <integer>;
  slot point-y :: <integer>;
end;
define variable *everything* = "everything";
define method factorial (n == 0) 1 end;  // called when n = 0
define method factorial (n == 1) 1 end;  // called when n = 1
define method factorial (n)              // called for any other n
  n * factorial(n - 1)
end;
```

Hmm. Needs work. I'd like to see three things in a code highlighter:

1. Highlight new bindings. Wherever a new variable/function/class/etc name is
   *introduced*, it should be highlighted.

2. Highlight unusual flow of control. Any non-local exit, like `return`,
   `signal`, `error` should stand out.

3. I think a different color for comments (and perhaps strings) does help to
   orient me when I'm paging through code quickly, so this can be useful.

In the above code this would mean highlighting `<point>`, `*everything*`,
`"everything"` (but not in red), the first three instances of `factorial`, and
the comments. If you're reading this in the future, and I've done my job well,
that's what you'll see.

It's common for syntax coloring themes to make **everything** a different
color. "We know this is a type so we'll make it yellow. We know this is a
number so we'll make it blue." To me this removes the usefulness of the
highlighting in the first place. If every syntactic element is a different
color the color ceases to carry useful information.

That's all for now...
