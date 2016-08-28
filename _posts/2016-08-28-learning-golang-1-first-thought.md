---
layout: post
title:  "Learning Golang #1 First Thought"
date:   2016-08-28 13:18:00 +0700
categories: programming language
published: true
---

Golang is one of new emerging programming languages like scala, kotlin, and swift, to name a few. To quote creator's intention with golang:

> Go is an attempt to combine the ease of programming of an interpreted, dynamically typed language with the efficiency and safety of a statically typed, compiled language.

After trying out golang for some times, I generally agreed that it is indeed easy to learn. If you are familiar with some of the popular programming languages now (java, C#, PHP, C, C++), you'll feel right at home, except for some syntastic sugars, but don't worry, golang has some reliable tools to check, lint, and even correct your code (wow, more on that later).

To be honest, when first time seeing the code, I really thought that the syntax is 'beautiful' (in my opinion, others' opinions may differ). Look at this piece of code:

```golang
func GetFibonacciSeriesFast(length int) []int {
	result := make([]int, length)

	for i := 0; i < length; i++ {
		if i == 0 {
			result[i] = 0
		} else if i == 1 {
			result[i] = 1
		} else {
			result[i] = result[i-1] + result[i-2]
		}
	}

	return result
}
```

# Multiple Return Types

Java and C# programmers will notice that the declaration of variable type is inverted, variable first, then type. Next thing is the return type is declared after function declaration (and golang supports multiple return types at once). Ok, this is a good concept. But when not properly used, can be devastating too (e.g. a function returns 10-or-so return types at once won't be easy to maintain).

```golang
func isValidNewUser(request *requests.CreateNewUserRequest) (validNewUser bool,
	err error) {

	validNewUser = true
	exist, err := repositories.IsUserNameExist(request.Name)
	if err != nil {
		return
	}
	if exist {
		validNewUser = false
	}
	return
}
```

# Error Handling

Then, the error handling. This maybe a bit frustrating at first. But while getting around it, I felt that I somehow learned how to handle error properly, which method should throw the error, and which method should handle the error, or taking care of it. The error handling looks something like this:

```golang
exist, err := repositories.IsUserNameExist(request.Name)
if err != nil {
    return
}
```

Yes you have to repeat similiar lines like this often. This is idiomatic in golang, so it's ok. When your function became unreadably long, it's more likely because you are not get used with this method of error handling yet (more so if you are used to use `try catch` blocks to handle errors). But when you get the hang of it, you can write more efficient, yet granular error handling.

# Dependencies/Imports

Golang is an open source project, naturally, many of its libraries (core and external) are also open source. Go uses a simple way to import external dependencies. On your command line (after installed Go, of course, and properly configure the environment), just type:

```bash
go get path/to/dependency
```

Then you can just add import definition in your code:

```golang
import (
	"github.com/gin-gonic/gin"
	"github.com/satriyo796/api-gateway/helper"
	"net/http"
)
```

And just call the function from imported library like this:

```golang
resp, err := http.Get(url)
helper.HandleError(err, c)
```

Simple, and works as expected.

# Documentation

Extensive documentations for core and external libraries are available online. You can look at:

* [Official golang documentation (core)](https://golang.org/doc/)
* [Godoc (public repos)](https://godoc.org/)

The documentation is a good source for learning golang. It's also one reason why golang is easy to learn.
