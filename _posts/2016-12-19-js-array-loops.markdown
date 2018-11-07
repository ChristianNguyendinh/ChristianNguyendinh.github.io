---
layout: post
title:  "JS Arrays: map() vs. forEach() vs. for()"
date:   2016-12-19 15:52:06 -0400
categories: uncategorized
---

All are used for iteration over arrays.

<h3>for()</h3>
<ul>
    <li>basic for loop way of iterating through an array.</li>
    <li>+ Faster for than map and forEach for most environments. (map is faster on some others)</li>
    <li>– More code</li>
</ul>
Textbook way:

{% highlight javascript %}
for (let i = 0; i < array.length; i++ ) {
    // do something with array[i]
}
{% endhighlight %}

For ‘in’ way:

For in will loop through the ‘keys’ not through the values.

{% highlight javascript %}
for (let i in [“a”, “b”, “c”]) {
    // each i will represent an INDEX 0, 1, or 2, not the VALUE “a”, “b”, or “c”
}
{% endhighlight %}

Much more useful if you have an object and want the keys.

{% highlight javascript %}
var obj = {name: “johnny”, age: 22}
for (let i in obj) {
    console.log(i + ” = ” + obj[i])
}
// OUTPUT:
// name = johnny
// age = 22
{% endhighlight %}

For ‘of’ way:

For of will loop through the values of an array. Only works on collections with the Symbol.iterator property. So For in works with (raw) objects while For of does not. It also works with strings!

{% highlight javascript %}
for (let i in [“a”, “b”, “c”]) {
    // Each i will represent the actual value, i.e “a”, “b”, or “c”
}
{% endhighlight %}

<h3>forEach()</h3>
Very similar to the ‘For of’ loop.
<ul>
    <li>+ Less code than regular for loop</li>
    <li>– No chaining</li>
    <li>– Slower</li>
</ul>

{% highlight javascript %}
var arr = [“a”, “b”, “c”]
arr.forEach(element => console.log(element))
// Returns undefined
// OUTPUT:
// a
// b
// c
{% endhighlight %}

Chaining does not work

{% highlight javascript %}
// WONT WORK. forEach() does not return an array.
arr.forEach(element => element += “ab”).sort()
{% endhighlight %}

<h3>map()</h3>
Similar to forEach, except it returns an array
<ul>
    <li>+ Faster than forEach</li>
    <li>+ Less code than forEach (3 characters vs 7)</li>
    <li>+ Allows chaining</li>
</ul>

{% highlight javascript %}
var arr = [“a”, “b”, “c”]
arr.map(element => console.log(element))
// Returns an array ([undefined, undefined, undefined] in this case)
// OUTPUT:
// a
// b
// c
{% endhighlight %}

We can use the return value of map()

{% highlight javascript %}
var arr = [“a”, “b”, “c”]
var newArr = arr.map(element => element += “ab”)
// arr = [“a”, “b”, “c”]
// newArr = [“aab”, “bab”, “cab”]
{% endhighlight %}

And we can chain together other methods with map()

{% highlight javascript %}
var arr = [“c”, “b”, “a”]
arrOne = arr.map(element => element = “ab” + element)
// arrOne = [“abc”, “abb”, “aba”]
arrTwo = arr.map(element => element = “ab” + element).sorted()
// arrTwo = [“aba”, “abb”, “abc”]
{% endhighlight %}
