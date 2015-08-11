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

Writer's Have It Good
  They get to publish their work
  At some point, it's done

Code is always a draft

> Unless you are burning your program into some unalterable hardware, it can change. Most of us work in situations where the code changes constantly. It is never done

We need to respect drafts

> Like writers, we should acknowledge the value drafts serve. Each one shows our growing knowledge of the code and our vision for where it should be.

We need to understand how to improve our drafts
  Refactoring

> I see a lot of programmers try to *get things right* right away, because they have an aversion to improving their code through drafts.

Maybe because:
  We aren't sure how
  Or we haven't seen any benefits 

Hint: these two are related

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

How did our changes make this feature easier?

Did our changes make *any* feature easier?

I call this a Stylistic Refactoring. Valuable, yes. But not in terms of design. Let's look at a writer's example:

Call me Ishmael joke

> I stole this joke from Gary Larsen's 'The Far Side'. I'd show you an image, but copyright, etc.

Names are important

But, improving your draft code means improving its structure

Refactoring: Improving the *Design* of Existing Code

Refactoring, when done right, moves your code from First Draft to Second, and beyond

Heuristic: Does it change the implementation of a new feature

Before

```
def lemur_renamer(lemurs)
  lemurs.each do |lemur|
    if using_snake_name?
      lemur.update_name(SnakeNames.random)
    else
      lemur.update_name(LemurNames.random)
    end
  end
end
```

After

```
def lemur_renamer(lemurs, names = LemurNames)
  lemurs.each { |lemur| lemur.update_name(names.random) }
end
```

Importantly, you can't know this in advance. Otherwise you'd just write a final draft.

You have to write that first terrible draft, learn the structure and then **improve** the structure

So, why don't we write it like this from the beginning?
We can't
it's a bad idea
https://twitter.com/jeremydmiller/status/568797862441586688
http://martinfowler.com/bliki/Yagni.html
