---
layout: post
permalink: "custom-uiview-from-xib"
title:  "Creating a custom UIView from a Xib in Swift"
date:   2020-02-02 16:21:10 +0100
categories: [Tips 🚀]
---

## Why is it important? 🤔

Creating custom views is an underrated habit that can benefit any codebase for a variety of reasons.

### Reusability

Very often, the same group of design elements will be on multiple screens across an app. It makes sense to group them in a custom `UIView` to reuse the same design and logic at multiple places.

- Enables reusable design and code
- Saves time
- Facilitates changes

### Readability

When a screen has many design elements, the `UIViewController` associated with it can get messy.

- A lot of outlets
- A lot of configuration logic

Grouping those elements in a custom `UIView` move the outlets and the configuration logic to the custom view, making the view controller smaller, easier to read and maintain.

### Testability

Testing every state of a view controller that has a lot of outlets and design logic can be time-consuming and hard to maintain. However, if the view controller is built from a few custom views, those can be tested independently. This improves your tests and make them:

- Easier to maintain
- Smaller and faster to write

## How can I create a custom UIView from a Xib? 🛠

It is relatively easy to create a custom `UIView` from a `Xib` in Swift. There are multiple steps to it though. It all starts with a simple protocol.

### Protocol
First, we need a protocol to give a subclass of `UIView` the ability to attach the content of `Xib` to its content view.

{% highlight swift %}
protocol CustomViewProtocol {

    /// The content of the UIView
    var contentView: UIView { get }

    /// Attach a custom `Nib` to the view's content
    /// - Parameter customViewName: the name of the `Nib` to attachs
    func commonInit(for customViewName: String)
}

extension CustomViewProtocol where Self: UIView {

    func commonInit(for customViewName: String) {
        Bundle.main.loadNibNamed(customViewName, owner: self, options: nil)
        addSubview(contentView)
        contentView.backgroundColor = .clear
        contentView.frame = bounds
        contentView.autoresizingMask = [.flexibleWidth, .flexibleHeight]
        contentView.translatesAutoresizingMaskIntoConstraints = false
    }

}
{% endhighlight %}

### Xib file and UIView subclass

Let’s say our custom view is called `MyCustomView`. The creation process would be the following:
- Create a `UIView` subclass called `MyCustomView`
- Create a `Xib` file called `MyCustomView.xib`

Then, we need `MyCustomView` to conform to `CustomViewProtocol`.

![]({{site.baseUrl}}/assets/custom-view.gif)

After this step, it is **crucial** to make sure the `commonInit(for customViewName: String)` method is called when the custom `UIView` is initialized.

{% highlight swift %}
final class MyCustomView: UIView, CustomViewProtocol {

    @IBOutlet var contentView: UIView!

    required init?(coder: NSCoder) {
        super.init(coder: coder)
        commonInit("MyCustomView")
    }

    override init(frame: CGRect) {
        super.init(frame: frame)
        commonInit("MyCustomView")
    }
}
{% endhighlight %}

That’s it, you have attached the content of a `Xib` to your custom `UIView`.

### Usage
To use your custom view, add a `UIView` to your `UIViewController` in storyboard and set its class to be your custom view. That’s it! 🎉

### Note
If you need to handle certain events happening in your custom view from your view controller I would recommend using the delegate pattern.