---
layout: post
title:  "Simple Fibonacci Series with Recursion in C#"
date:   2016-03-12 11:32:40 +0700
categories: programming
---

Fibonacci series are a series of integers having following pattern:

```
0, 1, 1, 2, 3, 5, 8, 13 ,21, 34, 55, and so on...
```

The pattern is F<sub>n</sub> = F<sub>n-1</sub> + F<sub>n-2</sub>
With F<sub>0</sub> = 0 and F<sub>1</sub> = 1

A simple implementation if this logic in csharp is as follows (with recursion):

{% highlight csharp %}

public static int GetItemValue(int itemIdx)
{
    if (itemIdx == 0) return 0;
    if (itemIdx == 1) return 1;
    return GetItemValue(itemIdx - 2) + GetItemValue(itemIdx - 1);
}

{% endhighlight %}

Then one more function is made to create a series with defined length.

{% highlight csharp %}
public static int[] GetSeries(int startIndex, int endIndex)
{
    int[] result = new int[endIndex - startIndex];
    int resultIdx = 0;
    for (int i = startIndex; i < endIndex; i++)
    {
        result[resultIdx] = GetItemValue(i);
        resultIdx++;
    }
    return result;
}
{% endhighlight %}

Of course, the performance of recursive code is a bit slow :D. These codes are for experimental only.

That's it, thanks for reading! Source code can be found [here](https://github.com/satriyo796/mono-algorithms/).

_Translated from my old [blog post](https://electrosphere.wordpress.com/2011/03/03/simple-recursion-fibonacci-series/)._
