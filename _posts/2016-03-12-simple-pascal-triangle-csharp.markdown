---
layout: post
title:  "Simple Pascal Triangle with Recursion in C#"
date:   2016-03-12 22:20:40 +0700
categories: programming
---

> In mathematics, Pascal's triangle is a triangular array of the binomial coefficients. In the Western world, it is named after French mathematician Blaise Pascal, although other mathematicians studied it centuries before him in India,[1] Persia (Iran), China, Germany, and Italy.[2]

Source [Wikipedia](https://en.wikipedia.org/wiki/Pascal%27s_triangle)

Visual:
<a href="http://electrosphere.files.wordpress.com/2011/03/250px-pascals_triangle_5-svg.png"><img class="size-full wp-image-63 " title="250px-Pascal's_triangle_5.svg" src="http://electrosphere.files.wordpress.com/2011/03/250px-pascals_triangle_5-svg.png" alt="" width="250" height="180" /></a>

<!--more-->

Pascal triangle can be defined as follows:

{% highlight tex %}
f(x, 0) = 1

f(x, x) = 1

f(x, y) = f(x-1, y-1) + f(x-1, y)
{% endhighlight %}


With _x_ as row number and _y_ as column number (relative to first element of the row).

Therefore, the C# implementation of for getting the value of one single element (knowing the row and the column) will be:

{% highlight csharp %}
public static int ComputeItem(int row, int column)
{
    if(column == 0) return 1;
    if(column == row) return 1;
    return ComputeItem(row-1, column-1) + ComputeItem(row-1, column);
}
{% endhighlight %}

To get element values for specific line, can be done like this:


{% highlight csharp %}

public static int[] GenerateLine (int row)
{
    int[] result = new int[row+1];
    for(int column = 0; column <= row; column++)
    {
        result[column] = ComputeElementValue(row,column);
    }
    return result;
}

{% endhighlight %}

Then, if we want to create the complete triangle, just loop through the desired lines:

{% highlight csharp %}

public static int[][] GenerateTriangleArray(int rowStart, int rowEnd)
{
    int[][] result = new int[rowEnd-rowStart][];
    for(int i=rowStart;i<rowEnd;i++)
    {
        result[i] = GenerateLine (i);
    }
    return result;
}

{% endhighlight %}

Performance wise, these codes are not efficient enough that recursion is used. And the recursion is quite a lot. For performance concerns, it is recomended to use loop only. But again, the code must be optimized for the requirements. Therefore, the code will tailored for specific needs. This codes are or education and experimental only.

Happy Coding!

Source code can be found [here](https://github.com/satriyo796/mono-algorithms/).

_Translated from my old [blog post](https://electrosphere.wordpress.com/2011/03/04/another-recursion-pascals-triangle/)_
