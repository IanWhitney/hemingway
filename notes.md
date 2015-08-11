Even Hemingway Wasn't Hemingway

“The first draft of anything is shit.” - Ernest Hemingway

Ernest Hemingway didn't write first drafts of sparse, clear prose. He wrote terrible first drafts and then rewrote them, over and over, until the design of the prose was right.

For Hemingway, and every good writer, Writing is Rewriting.

As programmers our first drafts are terrible as well. Perhaps we clean up that first draft with some stylistic tweaks that make it look nicer but that don't affect the underlying design. How often do we really dig in to that first draft and tear it apart, redesigning it until it is sparse and clear? Not often enough. And that's to our detriment.

For good developers, Design is Refactoring.

That sounds easy, but all too frequently refactoring doesn't lead to appreciable changes in the code's design. How do you use refactoring to improve code design? And how do you identify when you're just changing the surface style of your code? What's the difference between coding style and design, anyway? I'll answer all of these questions, hopefully, and show you how to take your code from a first draft to a clear, sparse design.

-------
Writers go through drafts
Lots of drafts
They know the value of rewriting, and are aware of the process.
Hemingway quote

Code goes through draft
  where writers can publish, we only deploy a draft
  It's always a draft

But we seem less aware of the need for drafts
  want to lock code in
  reluctant to get in there and re-work

Maybe that's because we're not sure how

Or we think we know, but haven't seen any benefits

Hint: these two are related

Let's look at a refactoring example

deckchair shuffling example

Now, we want to add a new feature, did our refactoring help?

I call this a Stylistic Refactoring. Valuable, yes. But not in terms of design. Let's look at a writer's example:

Call me Ishmael joke

The name of this character is important, yes. But these change do nothing to alter the structure of the story.

The Structure of your application is not its style, but its design. And refactoring is a change to that design.

Refactoring, when done right, moves your code from First Draft to Second, and beyond

Heuristic: Does it change the implementation of a new feature


design change examples

Importantly, you can't know this in advance. Otherwise you'd just write a final draft.

You have to write that first terrible draft, learn the structure and then **improve** the structure

So, why don't we write it like this from the beginning?
We cant
it's a bad idea
https://twitter.com/jeremydmiller/status/568797862441586688
http://martinfowler.com/bliki/Yagni.html
