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

> Writers know the value of rewriting. They know that the final work is built on piles and piles of discarded drafts. Ernest Hemingway was blunt about drafts:

The first draft of anything is shit
  - Ernest Hemingway

https://vramon1958.files.wordpress.com/2015/01/hemingway.jpg

> Hemingway's style is know for its precision, terseness and clarity. These are all features that I strive for in my code. Hemingway knew that this style came through rewriting.

Writers Have It Good
  After publication, it's done

Code is always a draft

> Unless you are burning your program into some unalterable hardware, it can change. Most of us work in situations where the code changes constantly. It is never done

This is to our benefit, if we allow it

> Like writers, we can improve our code through each draft. Every time we improve the code, we show our growing knowledge of the code's purpose and our vision for what it should do. And, unlike writers, we don't have to stop.

How do we take advantage of this?

Refactoring is our Rewriting

But only when we truly refactor

Let's look at a common type of refactoring

Before:

```
def lemur_renamer(lemurs)
  lemurs.each do |x|
    x.update_name(LemurNames.a_lemur_name)
  end
end
```

After:

```
def lemur_renamer(lemurs)
  lemurs.each { |lemur| lemur.update_name(LemurNames.random) }
end
```

> In this we've changed an opaque variable, x, to a descriptive one, lemur. We've replaced loop with a more idiomatic block. And we changed how we get a random lemur name. This is all to the good. Then we get a new feature request

Allow people to name Lemurs with our collection of Snake names.

Did our changes make implementing this feature easier?

Did our changes make implementing *any* feature easier?

What would a similar change look like in a novel?

Call me Ishmael joke

> I stole this joke from Gary Larsen's 'The Far Side'. I'd show you an image, but copyright, etc.

Stylistic Refactoring

> I call this a Stylistic Refactoring. Valuable, yes. But it doesn't change your code's structure, its design

Names are important

_Refactoring: Improving the *Design* of Existing Code_

> Emphasis mine. Design, in this case, means the structure of your code.

Going back to a writing example:

Austen

> This is illegible, I realize. It's a Jane Austen manuscript, and you can see that the changes here are wholesale deletions, reorganizations. This goes beyond style and into structure. 

Refactoring is changing of your code's structure

And it is through Refactoring that your code will move from First Draft, to Second and Beyond

How can you tell when you are actually Refactoring?

Does it change the implementation of a new feature?

> Let's go back to our previous example. We left the code like this:

```
def lemur_renamer(lemurs)
  lemurs.each { |lemur| lemur.update_name(LemurNames.random) }
end
```

> And we want to let people name lemurs with a their chosen name. We can do that without altering the signature of this method, sure:

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

> Users of this method don't care about this change, so structurally this method hasn't really changed. But its implementation is certainly worse. Let's try that again, but this time tackle the code's structure

```
def lemur_renamer(lemurs, names = LemurNames)
  lemurs.each { |lemur| lemur.update_name(names.random) }
end
```

> Existing clients of this code probably aren't affected by this at all, but now it's simple for us to pass in any collection of names.

We:

- Wrote a draft
- Learned about a shortcoming of our draft
- Applied that to a change in the structure
- Ended up with a better draft

This process, I think, is unalterable.

If it weren't, we could write perfect software the first time. 

As likely as a classic novel with your first draft

But it only works if you make the structural change

Otherwise you're just renaming characters in an increasingly convoluted novel

You have to write that first terrible draft, learn the structure and then **improve** the structure

https://twitter.com/jeremydmiller/status/568797862441586688
http://martinfowler.com/bliki/Yagni.html
