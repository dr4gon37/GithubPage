---
layout: post
title: "Memory alignment in structure"
subtitle: ""
date: 2019-08-28 19:43:00
comments: true
background: '/img/background/posts/ram.jpeg'
---
Hello, <br />
today we discuss topic, which many of you don't know. <br />
This is more interesting fact than useful knowledge unless you work with packets.  <br />
<!--more-->
<br />
Reading below code: 
{% highlight c++ %}
#include <iostream>
int main()
{
    struct A
    {
        int a;
        char b[3];
        long c;
        char d;
    };
    struct B
    {
        long c;
        int a;
        char b[3];
        char d;
    };
    std::cout << "The size of A is " << sizeof(A) << std::endl;
    std::cout << "The size of B is " << sizeof(B) << std::endl;
    
    return EXIT_SUCCESS;
}
{% endhighlight %}
it is obvious that those two structs have the same size. But this is not the truth. <br />
Size A is 24 bits, size B is 16 bits, word size = 1 byte. <br />
<b>Why?</b> And what is word in this case?  <br />

First of all we have to clear the definitions: <br />
&middot; Data alignment - data are putting in the memory of the computer at address equal multiple of word size. <br />
&middot; Data structure padding - to align the data, sometimes compiler can add extra bites to make memory continuous.  <br />
&middot; Word -  the amount of data that a machine can process at one time. Word size could be 4 bits or 64 bits. It is up to processor. <br />

It's better for computer to read, for example, 4 bits at the same time than bit by bit. <br />


Word size: 1 byte <br/> <br/>
This is <b>struct A</b> in the memory:  <br />
![Structure A](/img/memoryAlignment/structureA.jpg) <br />
As you can see the compiler add some padding to increase the performance of the program. <br /><br />
When we take <b>struct B</b> we get: 
![Structure B](/img/memoryAlignment/structureB.jpg) <br />

Should we take care of it and change our structures even if they have 100 lines?  <br />
No, because we already know that our compiler can add extra informations to the memory block of size to get better performance (as I mentioned - it's better for computer to read word size data than bit by bit).   <br /> <br />
But what about network packets?  <br />
We send extra useless informations, packets are bigger, how to change the very big structure in easy way? <br />
There is a simple solution (or maybe two to be more precise): <br />
{% highlight c++ %}
#pragma pack(1)
{% endhighlight %}
or
{% highlight c++ %}
__attribute__ ((packed))
{% endhighlight %}
It depens of compiler you have. If you use gcc the second option will the good one. This works the same way as pragma but it is only available on gcc compiler. <br />

You can get the size of the word using this code:
{% highlight c++ %}
#include <iostream>
int main()
{
    std::cout << sizeof(size_t) << std::endl; // 32 bits machine - 4 bits 
                                              // 64 bits machine - 8 bits
    return EXIT_SUCCESS;
}
{% endhighlight %}

Assuming all the informations: <br /> 
You care about memory alignment only if you deal with the Internet packets and other stuffs like that :) <br />
In other case it doesn't matter, let your compiler do his job. <br />


Thanks for your attention. I hope you enjoy the post :) <br />


{% include disqus_comments.html %}