---
layout: post
permalink: "xcode-code-snippets"
title:  "Creating and using code snippets"
date:   2020-03-15 16:57:10 +0100
categories: [Xcode 🛠]
---

## What are code snippets in Xcode? 🤓

A code snippet is some small amount of reusable code. Often overlooked, it is a powerful tool to improve the consistency of a code base and to speed up your development process.

### Consistency 

When working on a codebase, we tend to write the same small portions of code again and again. A good example would be:

{% highlight swift %}

// MARK: - Privates
private extension MyClass {
    // ...
}
{% endhighlight %}

or something like:

{% highlight swift %}

find somehthing

{% endhighlight %}

It's very easy to forget that `MARK:-` or ???. While it doesn't impact the project that much, it's always nicer to work on a code base which is consistent from file to file. 

Using code snippets for those repetitve portions of code eliminates those inconsistencies, improving the readability and consistency of a code base.

### Speed

Using code snippets allows us to generate a significant amount of code in a small amount of time. Especially if you configure them with a completion shortcut, things get real fast! 🚀

**Example with vs without**

## How can we use them? 🛠

There are different ways to use code snippets in Xcode. You can either decide to you use the pre-defined snippets available out of the box in Xcode or create your own. 

### Pre-defined code snippets

You can find your collection of code snippets using `Cmd + Shift + l`. From there you can easily browse, select, edit or delete any code snippet.

// Video

In my opinion, the most useful pre-defined code snippets are: 

- dd
- dd
- dd
- dd

### Create ans share your custom code snippets

The best way to use code snippets is to create your own. Xcode makes it super easy! There are multiple ways to create code snippets.

- first

GIF

- Second

GIF

You can add placeholders with `<#your placeholder#>` in order to make your snippets a bit more customisable. Also, it makes super easy to fill it your code snippet because you can use tab to switch from one placeholder to the other! 🧠

## Conclusion 📚

I personally use code snippets very often. Here are some of my favourites: 

- Test body 

{% highlight swift %}

func test<#testcase#>() {

    // Given
    <#code#>

    // When
    <#code#>

    // Then
    <#code#>
    
}

{% endhighlight %}

- Private extension 

{% highlight swift %}

// MARK: - Privates
private extension <# class name#> {
    <#code#>
}

{% endhighlight %}

- Warning

{% highlight swift %}

#warning("TODO: yourname, <#date#> - <#description#>")

{% endhighlight %}

- Testable
{% highlight swift %}
@testable import <#target#>
{% endhighlight %}