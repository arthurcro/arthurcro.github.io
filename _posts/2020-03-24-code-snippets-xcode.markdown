---
layout: post
permalink: "xcode-code-snippets"
title:  "Creating and using code snippets"
date:   2020-03-20 16:57:10 +0100
categories: [Xcode 🛠]
---

## What are code snippets in Xcode? 🤓

A code snippet is a small amount of reusable code. Often overlooked, it is a powerful tool to improve the consistency of a codebase and to speed up your development process.

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

func testMyCode() {

    // Given
    // ...

    // When
    // ...

    // Then
    // ...
}

{% endhighlight %}

It's very easy to forget that `MARK: -`, make a typo or break a convention. While it doesn't impact the project that much, it's always nicer to work on a codebase that is consistent from file to file. 

Using code snippets for those repetitve portions of code eliminates those inconsistencies, improving the readability and consistency of a codebase.

### Speed

Code snippets allows us to generate a significant amount of code in a small amount of time. Especially if you configure them with a completion shortcut, things get real fast! 🚀

**Example with vs without**

## How can we use them? 🛠

There are different ways to use code snippets in Xcode. You can either decide to you use the pre-defined snippets available out of the box in Xcode or create your own. 

### Pre-defined code snippets

You can find your collection of code snippets using `Cmd + Shift + l`. From there you can easily:

- **Browse** your code snippets

![]({{site.baseUrl}}/assets/browse_code_snippets.png)

- **Edit** by control-clicking the code snippets of your choice

![]({{site.baseUrl}}/assets/edit_code_snippets.png)

- **Delete** by pressing `Delete` om the code snippets of your choice

### Create your custom code snippets

The best way to use code snippets is to create your own. Xcode makes it super easy! There are multiple ways to create code snippets. 

- Go to **Editor**
- Select **Create code snippet**

You will be prompted by this window:

![]({{site.baseUrl}}/assets/create_code_snippet.png)


from which you can create your code snippet. I'd strongly recommend adding a **Completion Shortcut** to your code snippets as it makes them even faster to use! 

You can also:

- **Select** a portion of code
- **Control-click**
- Select **Create code snippet**

This will create a new code snippet from the code you selected and open the code snippet library so you can customise it.

It's also good to mention that you can insert placeholder tokens with `<#` and `#>` in your code snippet to make it a bit more customisable. Also, it makes super easy to fill in your code snippet because you can use `Tab` to switch from one placeholder to the other! 🧠

### Share and import code snippets

All your code snippets are in `~/Library/Developer/Xcode/UserData/CodeSnippets/`.

From there you can easily copy them and share then with your team! You can also import a code snippet in that same directory and it will be added to Xcode! 

## Examples 📚

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

- Todo

{% highlight swift %}

#warning("TODO: yourname, <#date#> - <#description#>")

{% endhighlight %}

- Testable
{% highlight swift %}
@testable import <#target#>
{% endhighlight %}