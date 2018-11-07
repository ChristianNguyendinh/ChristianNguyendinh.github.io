---
layout: post
title:  "HackerRank, JS Day 6: The Connected Cell in a Grid"
date:   2016-12-21 15:52:06 -0400
categories: uncategorized
---

UPDATE: 11/7/18 - i actually redid this again while preparing for this interview season and came up with a cleaner solution... note to self: update this with leetcode solution

<b>Problem</b>

Given a matrix with m rows and n columns with each cell containing a 1 or 0, find the number of cells in the largest ‘region’ of 1s. A region is a group of 1s connected together adjacently (directly left, right, above, below, or diagonally).

<b>Sample Input:</b>

{% highlight text %}
4
4
1 1 0 0
0 1 1 0
0 0 1 0
1 0 0 0
{% endhighlight %}

<b>Sample Output:</b>

{% highlight text %}
5
{% endhighlight %}

First we need to parse the input. We split the input by newlines. Index 0 will be the # of rows and index 1 will be the # of columns. The rest of the indexes will be rows of the actual matrix.

{% highlight javascript %}
function processData(input) {
    var split = input.split(“\n”);
    rows = Number(split[0]);
    cols = Number(split[1]);
}
{% endhighlight %}

I had some difficultly starting off, but I knew recursion would need to be used. So I started by declaring a few global variables, since recursion was going to edit some of these variables and I wanted the changes to actually affect each variable.

{% highlight javascript %}
var alreadySearched = []; // Array of 1s already searched
var biggest = 0; // Size of largest region currently found
var matrix = []; // 2d array representation of the actual matrix
var rows = 0; // Total # of rows in the matrix
var cols = 0; // Total # of columns in the matrix
var total = 0; // Size of current region
{% endhighlight %}

My first few attempts ended up with my call stack growing so large that the program threw an error. This was because after using split() to parse the output, I was using map() for each recursive call to examine an element of the matrix. So, I added the ‘matrix’ variable, and added code at the beginning to assemble a 2d array representation of the matrix.

{% highlight javascript %}
function processData(input) {
    var split = input.split(“\n”);
    rows = Number(split[0]);
    cols = Number(split[1]);

    for (var i = 0; i < rows; i++) {
        var thisRow = split[2 + i].split(” “).map(Number);
        var myRow = [];

        for (var j = 0; j < cols; j++) {
            myRow.push(thisRow[j]);
        }

        matrix.push(myRow);
    }
}
{% endhighlight %}

Now we have to iterate over the entire matrix and find all the 1s. Once we find a one we need to recursively search the elements around it to get the size of the region it is part of. Also, we need to only look at 1s that we have not already examined, just be more efficient. We will used the alreadySearched array for this.

{% highlight javascript %}
for (var i = 0; i < rows; i++) {
    for (var j = 0; j < cols; j++) {
        if (matrix[i][j] == 1 && alreadySearched.indexOf(i + “” + j) == -1) {
            total = 0;
            searchAround(i, j);
            if (total > biggest) {
                biggest = total;
            }
        }
    }
}
{% endhighlight %}

Now for searching “around” the found 1 cell. For each cell we search around, if it is a 1, we add it to the alreadySearched array, and recursively searchAround that cell. This allows us to get the entire size of the region that the calling 1s are a part of. When searching around each 1 cell, we need to to search the cell in row +- 0/1 and/or col +- 0/1. For each cell we search, if its cell value is 1, AND it has not already been examined (i.e in the alreadySearched array), we increment the ‘total’ value by 1. This ‘total’ variable is then used as comparison to the size of the biggest found region so far.

{% highlight javascript %}
function searchAround(i, j) {
    if (matrix[i][j] == 1 && alreadySearched.indexOf(i + “” + j) == -1) {
        alreadySearched.push(i + “” + j);
        total += 1;

        if (i – 1 >= 0)
        searchAround(i – 1, j);
        if (i + 1 < rows)
        searchAround(i + 1, j);
        if (j – 1 >= 0)
        searchAround(i, j – 1);
        if (j + 1 < cols)
        searchAround(i, j + 1);

        if (i – 1 >= 0 && j – 1 >= 0)
        searchAround(i – 1, j – 1);
        if (i + 1 < rows && j – 1 >= 0)
        searchAround(i + 1, j – 1);
        if (i – 1 >= 0 && j + 1 < cols)
        searchAround(i – 1, j + 1);
        if (i + 1 < rows && j + 1 < cols)
        searchAround(i + 1, j + 1);

        return total;

    }
    return 0;
}
{% endhighlight %}

This allows us to assemble the size of each region of 1s, starting from the first 1 we hit. If a 1 cell has been already counted in a previous region, we ignore it. After getting the size of each region, we get the biggest one, and log that to the console. Besides the beginning part where we have to assemble the entire matrix from stdin to a 2d array, I quite happy with my solution.

Solution in full:

![solution-p1](/assets/images/grid-solution-p1.png)

![solution-p2](/assets/images/grid-solution-p2.png)
