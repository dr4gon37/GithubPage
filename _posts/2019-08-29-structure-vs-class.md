---
layout: post
title: "Structure vs class"
subtitle: ""
date: 2019-08-29 23:27:00
comments: true
categories: c++
background: '/img/background/posts/structureClass.jpeg'
---
Hello everyone, <br/>
today post will be the shortest one so far. We will talk about differences between structure and class. <br/>
<!--more-->
This topic isn't hard but beginners programmers in C++ can have some thoughts about it. <br/>

It's a common, good convention to use structure only for data without any methods, constructors or destructor. Just only data. This is the first difference. <br/>
Of coure structure have methods and even constructor or destructor. Structures are avalaible in C++ to keep backward compatibility with C. <br/>

The second difference is that members of a class are private by default, in structure there are public. <br/>

The third difference. The default visibility of structure is public, the class is private. It means also, if you don’t specify anything then the struct will inherit publicly from its base class: <br/>
{% highlight c++ %}
struct T : Base // struct T : public Base
{
   ...
};

class T : Base // class T : private Base
{
   ...
};

{% endhighlight %}

There are no mow differences between structure and class in C++.  <br/>
To prove it, we will look at that code:  <br/>
{% highlight c++ %}
#include <type_traits>
#include <iostream>

int main()
{
    struct Str {};
    
    std::cout << std::is_class<Str>::value; //1 
}
{% endhighlight %}

There you can read more about [type traits][type_traits.h]

[type_traits.h]: https://en.cppreference.com/w/cpp/header/type_traits


{% include disqus_comments.html %}