Even Hemingway Wasn't Hemingway

“The first draft of anything is shit.” - Ernest Hemingway

Ernest Hemingway didn't write first drafts of sparse, clear prose. He wrote terrible first drafts and then rewrote them, over and over, until the design of the prose was right.

For Hemingway, and every good writer, Writing is Rewriting.

As programmers our first drafts are terrible as well. Perhaps we clean up that first draft with some stylistic tweaks that make it look nicer but that don't affect the underlying design. How often do we really dig in to that first draft and tear it apart, redesigning it until it is sparse and clear? Not often enough. And that's to our detriment.

For good developers, Design is Refactoring.

That sounds easy, but all too frequently refactoring doesn't lead to appreciable changes in the code's design. How do you use refactoring to improve code design? And how do you identify when you're just changing the surface style of your code? What's the difference between coding style and design, anyway? I'll answer all of these questions, hopefully, and show you how to take your code from a first draft to a clear, sparse design.

-------

# Even Hemingway Wasn't Hemingway

### Ian Whitney
### @iwhitney
### https://github.com/ianwhitney/hemingway


Writers keep changing words
  Writers write several drafts
  Writers edit
  Writers Rewrite

The Best Writing Is Rewriting
  - E. B. White

Writing is Rewriting

> Writers know the value of rewriting. They know that the final work is built on piles and piles of discarded drafts. Ernest Hemingway was blunt about drafts:

The first draft of anything is shit
  - Ernest Hemingway

https://vramon1958.files.wordpress.com/2015/01/hemingway.jpg

> Hemingway's style is known for its precision, terseness and clarity. These are all features that I strive for in my code. Hemingway knew that this style came through rewriting. As programmers we should learn that good coding style only comes through rewriting.

Hemingway sample

> Clear, simple, economical

But it didn't start like this

Hemingway photo

This one's from Jane Austen

Austen photo

> I realize that neither of these are exactly legible, but they share some things in common. A lot of deletions, some changes in word choice.

In code, that might be something like this:

```
def lemur_renamer(lemurs)
  lemurs.each do |x|
    x.update_name(LemurNames.a_lemur_name)
  end
end
```

Becomes:

```
def lemur_renamer(lemurs)
  lemurs.each { |lemur| lemur.update_name(LemurNames.random) }
end
```

> In this we've changed an opaque variable, x, to a descriptive one, lemur. We've replaced loop with a more idiomatic block. And we changed how we get a random lemur name. This is all to the good.

But how much has our code actually changed?

> We still loop through a collection of lemurs and give each one a new, randomly selected Lemur Name.

Let's look another writing example

Call me Ishmael joke

> I stole this joke from Gary Larsen's 'The Far Side'. I'd show you an image, but copyright, etc.

Are our code changes any more significant than changing a character's name?

```
def lemur_renamer(lemurs)
  lemurs.each { |lemur| lemur.update_name(LemurNames.random) }
end
```

> Names are important, yes. This code is Stylistically better than it was. But structurally it is exactly the same.

Structure and Style

> In novel terms: if you've read Harry Potter, think how different the story would be if Rowling had revealed Snape's back story in the earliest books. Telling it at the end is a structural story telling choice.

> In code terms, structure matters when we want to add or change a feature.
> Code that is structurally different will differ when making changes


Feature: Let people name lemurs with their own sets of lemur names

```
def lemur_renamer(lemurs)
  lemurs.each { |lemur| lemur.update_name(LemurNames.random) }
end
```

So, how do we do that?

```
def lemur_renamer(lemurs)
  lemurs.each do |lemur|
    if lemur.owner.name_list.any?
      lemur.update_name(lemur.owner.name_list.random)
    else
      lemur.update_name(LemurNames.random)
    end
  end
end
```

> This one requires no change to any existing client code. But it introduces a conditional that is likely to grow.

Like this?

```
def lemur_renamer(lemurs, names)
  lemurs.each { |lemur| lemur.update_name(names.random) }
end
```

> This requires us to change any client code to handle the new signature. But it won't grow as we get more name collections.

Like this?

```
def lemur_renamer(lemurs, names = LemurNames)
  lemurs.each { |lemur| lemur.update_name(names.random) }
end
```

> Existing client code can remain unchanged and use the default, new code can pass in their own name collections.

Refactoring
Improving the **design** of existing code


In code, we learn the structure our code should take by

- Wrote a draft
- Learned about a shortcoming of our draft
- Applied that to a change in the structure
- Ended up with a better draft

What's my choice

```
def lemur_renamer(lemurs, names = LemurNames)
  lemurs.each { |lemur| lemur.update_name(names.random) }
end
```

- Red
- Green
- Refactor

- Red
- Green
- Stylistic

- Refactor
- Test
- Implement

This process, I think, is unalterable.

If it weren't, we could write perfect software the first time. 

But it only works if you make the structural change

How do you tell?

- How would I have implemented this feature before the change?
- How would I implement it after?

If it is different, you have made a structural change to your code

If it is *easier*, you have made a good structural change
