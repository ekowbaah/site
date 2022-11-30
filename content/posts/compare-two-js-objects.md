+++
author = "Ekow Baah-Nyarkoh"
title = "How to compare 2 objects in JavaScript  🥷"
date = "2022-03-26"
description = "Best way to compare two javascript objects"
tags = [
    "javascript",
    "objects"
]
+++

How do you compare two objects in javascript? The first thing that comes to mind is to use the classic comparison operators but does it work? This article will look at ways of comparing two javascript objects with and without using any third-party libraries. We will also look at the benefits and tradeoffs of each.

## Why direct comparison operators won't work.

In JavaScript, values are either primitives or objects. Primitive types (such as string and number) are immutable. So, for example, the number 16 will always be the number 16; the string "Robert" will always be the string "Robert". Objects, on the other hand, are mutable.

**_Note that immutability does not mean the content of the variables can't change. 🔑_**

```js
const age1 = 16;
const age2 = 16;

age1 === age2; //true

const name1 = "Robert";
const name2 = "Robert";

name1 === name2; //true

const obj1 = { name: "Robert", age: "16" };
const obj2 = { name: "Robert", age: "16" };
const obj3 = obj1;

obj1 === obj2; //false

obj1 === obj3; //true
```

In the code above, we can see that we get the expected results when we use two primitives with comparison operators, but that is not the case when we compare with objects. First, note that the properties of obj1 and obj2 are the same; however, they are two distinct objects (in contrast to primitives: two variables that both have the number 16 refer to the same primitive)—on the other hand, comparing obj1 to obj3 yields, the same results as comparing primitives because this has to do with the object's location in memory. <a href="https://dev.to/carlosrafael22/back-to-the-basics-primitive-and-object-types-in-javascript-18c2" target="_blank">You can read more about primitives and objects here.</a>

## 1. Using JSON.stringify

```js
const obj1 = { clothing: "🧥" };
const obj2 = { clothing: "🧥" };

JSON.stringify(obj1) === JSON.stringify(obj2); //true
```

What is happening here? We convert our object into a JSON string and then compare it using the comparison operators. Doing that works because we compare two primitives (strings). It is also applicable to nested objects. We can see this from the code below.

```js

const person1 = {
age: 23,
features: {
 eyes: '👀',
 nose:'👃'
 feet: {
   size: 32
 }
}
};

const person2 = {
age: 23,
features: {
 eyes: '👀',
 nose:'👃'
 feet: {
   size: 32
 }
}
};

JSON.stringify(person1) === JSON.stringify(person2); //true


```

Now to the downsides of using this approach. For this to work, order matters. What does this mean? We need to have the keys and values in both objects in the same order to get the desired results. Since we compare the objects to strings if the order differs, we will have two completely different strings, hence the unexpected result. I recommend using this approach when you have to compare small objects you have complete control over, not massive objects of 1000 key-value pairs.

<!--more-->

## 2. Using Object.enteries

```js
Object.entries(person1).toString() === Object.entries(person2).toString(); // true
```

We can also compare two objects using ES6's Object.entries method, which returns an array of a given object's own string-keyed property `[key, value]` pairs. We then convert the arrays to strings using the toString method and compare the two strings just as we did in the first approach. For this approach, order matters as well since we compare strings.

However, this approach won't produce the desired results in the case of nested loops since Object. enteries only return the values of the first level of the object.
Use this approach if you want to compare small flat objects.

## 3. Using Lodash's isEqual

```js
_.isEqual(person1, person2); // true
```

We can also compare two javascript objects using <a href="https://lodash.com/docs/4.17.15#isEqual/" target="_blank">Lodash - a third-party javascript utility library.</a> The Lodash **\_.isEqual()** method performs a deep comparison between two values to determine if they are equivalent.

This method supports comparison for other kinds of objects as well. It returns a **boolean value** (Returns true if the two values are equal, else false).

This approach offers a bit of an advantage to those above. It works fine for deep nested and flat objects and does not require the objects to have the same order covering a lot of odd edge cases.

Lodash is significantly faster. Because lodash will stop as soon as it reaches the first difference, stringify will continue unnecessarily until the end.

## Conslusion

I recommend using lodash's isEqual method since it's faster than the other approaches and will give you the desired results since it makes a deep comparison. It might not be very pleasant to import the whole library to use one method, but maybe it's worth it, just maybe 😉.

## Resources

- <a href="https://lodash.com/docs/4.17.15#isEqual/" target="_blank">Lodash: isEqual</a>
- <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify" target="_blank">JSON stringify</a>
- <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/entries" target="_blank">Object.entries</a>
- <a href="https://stackoverflow.com/questions/201183/how-to-determine-equality-for-two-javascript-objects" target="_blank">How to determine equality for two javascript objects</a>
- <a href="https://betterprogramming.pub/intermediate-javascript-whats-the-difference-between-primitive-values-and-object-references-e863d70677b" target="_blank">What’s the Difference Between Primitive Values and Object References in JavaScript?</a>
