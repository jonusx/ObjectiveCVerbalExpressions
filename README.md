ObjectiveCVerbalExpressions
=====================
[![Build Status](https://travis-ci.org/kishikawakatsumi/ObjectiveCVerbalExpressions.png?branch=master)](https://travis-ci.org/kishikawakatsumi/ObjectiveCVerbalExpressions)
[![Coverage Status](https://coveralls.io/repos/kishikawakatsumi/ObjectiveCVerbalExpressions/badge.png?branch=master)](https://coveralls.io/r/kishikawakatsumi/ObjectiveCVerbalExpressions?branch=master)

## Objective-C Regular Expressions made easy
ObjectiveCVerbalExpressions is a Objective-C library that helps to construct difficult regular expressions - ported from the awesome JavaScript [VerbalExpressions](https://github.com/jehna/VerbalExpressions).

## Examples

Here's a couple of simple examples to give an idea of how VerbalExpressions works:

### Testing if we have a valid URL

```objc
// Create an example of how to test for correctly formed URLs
OCVerbalExpression *expressions = [[OCVerbalExpression alloc] init];
[expressions startOfLine:YES];
[expressions then:@"http"];
[expressions maybe:@"s"];
[expressions then:@"://"];
[expressions maybe:@"www"];
[expressions anythingBut:@" "];
[expressions endOfLine:YES];

// Create an example URL
NSString *testMe = @"https://www.google.com";

// Use test: method
if ([expressions test:testMe]) {
    NSLog(@"%@", @"We have a correct URL"); // This output will fire
} else {
    NSLog(@"%@", @"The URL is incorrect");
}

NSLog(@"%@", tester); // Ouputs the actual expression used: "^(http)(s)?(:�_/�_/)(www)?([^ ]*)$"
```

### Replacing strings

```objc
NSString *replaceMe = @"Replace bird with a duck";

// Create an expression that seeks for word "bird"
OCVerbalExpression *expressions1 = [[OCVerbalExpression alloc] init];
[expressions1 find:@"bird"];

// Execute the expression like a normal RegExp object
NSString *result = [expressions1 replaceWithSource:replaceMe value:@"duck"];

NSLog(@"%@", result); // Outputs "Replace duck with a duck"
```

### Shorthand for string replace:

```objc
NSString *result2 = [[[OCVerbalExpression new] find:@"red"] replaceWithSource:@"We have a red house" value:@"blue"];

NSLog(@"%@", result2); // Outputs "We have a blue house"
```

## API documentation

I haven't added much documentation to this repo yet, but you can find the documentation for the original JavaScript repo on their [wiki](https://github.com/jehna/VerbalExpressions/wiki).  Most of the methods have been ported as of v0.1.0 of the JavaScript repo.  Just be sure to use the syntax explained above rather than the dot notation :)

## Contributions
Clone the repo and fork!
Pull requests are warmly welcomed!

## Issues
 - I haven't yet ported the `stopAtFirst` method.

## Thanks!
Thank you to @jehna for coming up with the awesome original idea!
