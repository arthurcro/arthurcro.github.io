---
layout: post
permalink: "readable-code"
title: "Write readable code"
date: 2020-03-31 17:57:15 +0100
categories: [Tips 🚀]
---

## What makes your code readable? 🤷‍♂️

Readable code is code that you find easy to read and that is easy for others to review.

You should be able to easily go through code that you wrote a few days ago. It should be easy to understand it and you should be able to make changes confidently without risking to break anything.

Other people should be able to get into your codebase easily, they should be able to review it, understand it and make changes without risking breaking anything.

## Why should we care? 🤗

Making sure you produce readable code is important for different reasons. Unreadable code is a major factor in technical debt. Unreadable code slows down a team and a project's progress. Making sure a team produces readable code reduces the technical debt and allows for:

- **Faster bug fixes**: it's easier to understand a piece of code hence bugs related to existing logic are fixed faster.
- **Faster development**: new developers can get up to speed with a codebase faster, they can contribute to the project sooner and more efficiently.
- **Better review**: people can review your code and the implementation of a feature more carefully when they don't have to decrypt your code. This leads to a better review process and a safer and healthier codebase.

## How to write readable code? 🛠

There are many very simple ways to improve the readability of the code your produce. Here are the guidelines I follow.

### Short and concise

Keep your code short and concise. Keep things simple and make sure you follow the single responsaiblity principle.

### Naming

Naming your entities properly is a huge factor in the readability of your code. I personally always try to follow [Swift API design guidelines](https://swift.org/documentation/api-design-guidelines/). It provides you with a set of rules and conventions to follow. 

The main guidelines are: 

- **Promote clear usage**: include all the words needed to avoid ambiguity, omit the needless word and name entities according to their role rather than their type.
- **Strive for fluent language**
- **Use terminology well**: avoid obscure terms, stick to established meaning and avoid abbreviations.

### Structure

You should organize your code inside your `.swift` files logically and consistently.

Use `// MARK: -` and extensions to organise your code.

{% highlight swift %}

// MARK: - Pivates
private extension CustomViewComtroller {
    // ...
}

// MARK: - UICollectionViewDelegate
extension CustomViewComtroller: UICollectionViewDelegate {
    // ...
}

// MARK: - Actions
@objc extension CustomViewComtroller {
    // ...
}
{% endhighlight %}

It makes it easier to find a specific piece of code in a file. You can navigate to the different landmarks like `//MARK: -` by clicking on the jump bar (the bar above the source code editor):

![]({{site.baseUrl}}/assets/jump_bar.png)

or by using the minimap introduced in Xcode 11.

![]({{site.baseUrl}}/assets/minimap.png)


### Formatting

You should format your Swift code consistently and according to a defined set of rules. 

To enforce those rules, there are many options. I use [Swiflint](https://github.com/realm/SwiftLint) because it's super straightforward. You can configure it with any Swift style guide you want. There are many well-known style guides out there, you should discuss with your team which one you think is best.

- [Airbnb](https://github.com/airbnb/swift)
- [Raywenderlich](https://github.com/raywenderlich/swift-style-guide)
- [Google](https://google.github.io/swift/)
- [LinkedIn](https://github.com/linkedin/swift-style-guide)


Xcode can also help you format your code properly. 

- `Ctrl + I` on selected code will format your code and fix any indentation issues.

- *Preferences* -> *Text Editing* -> *Tab Key* -> **Indents always** will allow you to properly any selected code using the `Tab` key.

- *Preferences* -> *Text Editing* -> **Page guide at column: 120** add am indicator in your editor so you can easily see if you have more than 120 characters on one line.