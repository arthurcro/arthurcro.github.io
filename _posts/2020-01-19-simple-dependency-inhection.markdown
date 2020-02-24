---
layout: post
title:  "Simple dependency injection"
date:   2020-01-19 17:21:10 +0100
categories: Architecture
---
# What is dependency injection? 🤓

Dependency injection is the idea to inject an outside object into another instead of creating it internally. So instead of doing something like this:

{% highlight swift %}
final class ExampleInteractor {
    private let errorHandler = ErrorHandler()
}
{% endhighlight %}

you would do something like this: 

{% highlight swift %}
protocol ExampleInteractorProtocol {}

final class ExampleInteractor: ExampleInteractorProtocol {

    private let errorHandler: ErrorHandlerProtocol

    init(errorHandler: ErrorHandlerProtocol) {
        self.errorHandler = errorHandler
    }
}
{% endhighlight %}

It’s a very simple principle to follow. It encourages the single responsibility principle, it improves the maintainability, reusability, and testability of a codebase.

# What does dependency injection bring to a project? 🤗

When working on a codebase, you want to avoid tight coupling as much as possible. Tight coupling is when some objects are highly dependent on each other. It usually implies that one object has too many responsibilities. Having such a situation complexifies the codebase and makes testing very difficult.

To overcome this situation, we need to split our app into loosely-coupled components. A great way to achieve this is to enforce dependency injection.
By extracting each of the responsibilities of an object to external objects, dependency injection will make sure there are as little as tightly-coupled components as possible.

This will enforce:
- **Readable code**: objects will have fewer responsibilities hence files will be smaller and logic will be simpler. That’ll make your code a lot more readable overall.

- **Reusable code**: each object will have only one responsibility which means you will be able to reuse components more often.

- **Maintainable code**: objects will be smaller and will contain less logic, it will be easier to make changes to existing objects.

- **Testable code**: because dependencies are injected you can easily replace them with mock objects to test the behavior of a class under specific configurations.

# How do we implement it? 🛠

1. The first step is to identify all the responsibilities of an object. This will help you to assess if an object is doing too much and needs to be refactored.

2. The second step is to separate each responsibility in an object. This will make your code more reusable, easy to maintain and a lot more readable.

3. The third step is to inject those single responsibility objects into the refactored object using its initializer.

Following those steps allowed me to refactor and improve old codebases fairly easily.

Dependency injection comes with some downsides for bigger projects though.

- Increases the number of classes
- Increases the amount of boilerplate code
- Time-consuming

To fix those issues I used the following frameworks.
- [Swinject](https://github.com/Swinject/Swinject) is a dependency injection framework that helps your app split into loosely-coupled components.

- [SwinjectStoryboard](https://github.com/Swinject/SwinjectStoryboard) is a Swinject extension for automatic dependency injection via Storyboard.

- [SwinjectAutoRegistration](https://github.com/Swinject/SwinjectAutoregistration) is an extension of Swinject that allows you to automatically register your services and greatly reduce the amount of boilerplate code.

# Results 👨🏻‍🔬
As a result of proper dependency injection, we now have a codebase built with small objects that have a single responsibility and are easy to test.

Introducing unit testing to a project is key to:

- Validate bug fixes and features
- Document complex logic
- Enforce good code quality

Personally, proper dependency injection was a real game-changer. It enabled me to write cleaner code and learn unit testing.

I have been using [SnapshotTesting](https://github.com/pointfreeco/swift-snapshot-testing), [SwiftyMocky](https://github.com/MakeAWishFoundation/SwiftyMocky), and [Nimble](https://github.com/Quick/Nimble) for a while now and it’s a combination that works very well.