# Even Hemingway Wasn't Hemingway
### Ian Whitney
### @iwhitney
### https://github.com/ianwhitney/hemingway



### Writers keep changing words


### ~~Writers keep changing words~~
### Writers write several drafts


### ~~Writers keep changing words~~
### ~~Writers write several drafts~~
### Writers edit


### ~~Writers keep changing words~~
### ~~Writers write several drafts~~
### ~~Writers edit~~
### Writers Rewrite


# The Best Writing Is Rewriting
### E. B. White


# Writing is Rewriting

Note: Writers even rewrite their own maxim about rewriting. They know the value of rewriting. It clarifies their early drafts and sharpens their message.. Ernest Hemingway was blunt about drafts



# The first draft of anything is shit
### Ernest Hemingway


<img src="images/hemingway.jpg" />

Note:
And here he is doing some of that rewriting. Taking a draft and revising it to something like:


### Simple exchange of values. You give them money. They give you a stuffed dog.<br />
_The Sun Also Rises_

Note:
I'm focusing on Hemingway because his style is known for precision, terseness and clarity. These are all features that I strive for in my code. Hemingway's novels weren't first drafts, they were meticulously re-written. And the approach of writers should be of interest to us, because like them, we are writing stories.


# Story?

Code tells a story.


# Code has drafts

Just like a 'real' writer, you rewrite your code.
As you work with your code, you find ways to improve it.
As you learn more about what your code should do, you refactor it to make it do that.


# Not every change is to the good

As long as we're working with a codebase, we're rewriting it.
But, you can rewrite multiple ways.


Some ways are useful, some not
Some are powerful, some not


I'm going to compare two ways of rewriting code


By the end of the talk, I hope to show you when to use these two approaches


To start, let's look at Hemingway again


<img src="images/hemingway.jpg" />


Note:
What's he doing here?
It's hard to see, but a lot of it is crossed out words replaced with other words.
Let's follow his example and see what this looks like in code.


# First Draft
```ruby
def lemur_renamer(lemurs)
  lemurs.each do |x|
    x.update_name(LemurNames.a_lemur_name)
  end
end
```

Note:
I have an app that lets people manage their lemur collections. Lemurs (or their owners) get bored of names pretty quickly, so they want to be able to rename all of their lemurs at once using randomly picked names. We follow Hemingway's example


# First Draft:
```ruby
def lemur_renamer(lemurs)
  lemurs.each do |x|
    x.update_name(LemurNames.a_lemur_name)
  end
end
```
---
# Rewritten:
```ruby
def lemur_renamer(lemurs)
  lemurs.each { |lemur| lemur.update_name(LemurNames.random) }
end
```

Note:
In this we've changed an opaque variable, x, to a descriptive one, lemur. We've replaced loop with a more idiomatic block. And we changed how we get a random lemur name. This is all to the good. But...


# What _Actually_ Changed?


# First Draft:
```ruby
def lemur_renamer(lemurs)
  lemurs.each do |x|
    x.update_name(LemurNames.a_lemur_name)
  end
end
```
---
# Rewritten:
```ruby
def lemur_renamer(lemurs)
  lemurs.each { |lemur| lemur.update_name(LemurNames.random) }
end
```

Note:
We still loop through a collection of lemurs and give each one a new, randomly selected Lemur Name. Our code is clearer, yes. But it is exactly the same code.


# The Story Remained the Same


# We changed **Style**
# We did not change **Structure**


# Rewriting Approach 1, Stylistic

Stylistic rewriting is great for when you're trying to _clarify_ code. Variable names, idioms, style guides. 

# What it does
- Clarifies your story
- Eases comprehension


# What it doesn't do
- Change the story your code tells


# Changing your story
- ~~Call me Bill~~
- ~~Call me Warren~~
- ~~Call me Al~~
- ~~Call me Roger~~
- **Call me Ishmael**

Note:
I stole this joke from Gary Larsen's 'The Far Side'. I'd show you an image, but copyright, etc. Giving Ishmael a good name is important, but structurally it doesn't affect the story that Melville is telling. In the story our code is telling, our changes were similarly ineffective.



# How many tickets/issues/stories are

> Improve our variable names

# And how many are

> Change the code to do something new/better?

Most of what we do is change the story our code tells.


# Structure is Important


<img src="images/hemingway.jpg" />

Note:
Here's Ernest again. His rewrites also involved large structural changes. He'd do things like start writing about one character, change his mind and then make the book about a different character. Not just change the name, like that Ishmael joke; a previously secondary character would simply become the main character 


# Wait. What?


# Hemingway didn't know the main character of his own book


# Structure is Knowledge

Note:
Hemingway wrote a draft, learned what sort of story he actually wanted to tell, and re-wrote. We write code, learn what story it actually needs to tell, and refactor.


# Our Current Story
```ruby
def lemur_renamer(lemurs)
  lemurs.each { |lemur| lemur.update_name(LemurNames.random) }
end
```

> "Update each lemur with a random name from LemurNames"


# The New Story

> Feature Request: Users can maintain their own set of names that are used when renaming their lemurs.

> Update each lemur with a random name from the user, if present, or from Lemur Names.


# How do we tell this story?


## Option One
```ruby
def lemur_renamer(lemurs)
  names = owner.name_list.any? ? owner.name_list : LemurNames

  lemurs.each { |lemur| lemur.update_name(names.random) }
end
```

Note:
This method's story is now: First I figure out what set of names to use, then I update each lemur with a random name. This is not a very concise story, and it might also surprise clients of this code, since they can't see or control which set of names are used.


## Option Two
```ruby
def lemur_renamer(lemurs, names = LemurNames)
  lemurs.each { |lemur| lemur.update_name(names.random) }
end
```

Note:
This story is more precise. Update each lemur with a random name from the provided names, or from Lemur Names


# We changed **Structure**
# We did not change **Style**


# Structure is Design

<img src="images/refactoringBook.jpg" />


Note:
Almost none of this book is about changing your code's style. It's patterns are almost entirely structural changes. A very simple one, "add parameter", is what we followed in our lemur_renamer code.


# Structure is Knowledge

Note:
Structural change is great for encoding new knowledge into your system. Before we didn't know that more than one set of lemur names was necessary, now our story clearly states than _any_ collection of names can be used.


# Stylistic Changes
- Clarify intent
- Improve readability
- Fast


# Structural Changes
- Changes features
- Adds new knowledge to the application
- Slower


# You can know style in advance
# You can not know structure


# The Magic Process
## We learn the structure our code should take by
1. Write a draft
2. Learn about a shortcoming of our draft
3. Apply structural change
4. Go To 2


# Forever


# This process, I think, is unalterable


# Even Hemingway wasn't Hemingway
