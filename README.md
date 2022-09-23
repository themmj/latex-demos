# latex-demos

A small collection of fun demos with latex. It is probably breaking a plethora of latex conventions, so feedback is
always welcome.

Latex's token evaluation is something I'm still readin up on [here](https://www.overleaf.com/learn/latex/Articles/How_does_%5Cexpandafter_work%3A_An_introduction_to_TeX_tokens).
Once I am more comfortable with it, I'll probably refactor a lot of the code in this project.

1. [Loops](#loops)
2. [Arrays](#arrays)
3. [HashMaps](#hashmaps)
4. [Context](#context)

## Loops

Latex has some builtin commands to loop over a set of values or until a certain condition is matched. This in
combination with conditional statements makes implementing algorithms fairly straight forward.

## Arrays

By defining commands in the format <arrayname><index> which contain the value to be stored at this index,
it is possible to model arrays. Combine this with a size counter and you got a stack.

## HashMaps

Combining two arrays and a basic string hashing function, one can build something which at least somewhat resembles
a hash map. It does not have buckets or any other clever logic. The hashing function uses the strings length and word
count to calculate a somewhat random value. The underlying array has a set size `\hashMapSize`. Finally, the collision
strategy is just looking for the next free slot.

## Context

This is the reason I even bothered with the above topics. Basically, I think it would be handy so store meta information
along with the written text which can be edited and retrieved at any time.

Example usages:  
- Track established concepts throughout the text
- Track character traits in your story
- Track worldbuilding details the reader has been introduced to

The goal is to ease restructuring of already witten content, going back and adding more details / plot points,
or just simply coming back to an ongoing work after a long time.

First each relevant context needs to be created (preferably in the praeamble) with `\contextCreate{<name>}`. Note that
the name of a context has to be a single word.

Then you can add and remove items from a context in your text with
`\contextAdd{<name>}{<info to add>}` and `\contextRemove{<name>}{<info to remove>}`.

Finally you can print an individual context `\contextPrint{<name>}` or all contexts `\contextPrintAll` at any point
in your text to find out what is currently established/known/...

Checkout `content/context.tex` for example usage and reference `demos.pdf` to see how it plays out.

