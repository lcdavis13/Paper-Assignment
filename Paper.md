## constexpr ##

**Levi Davis**

**Hope Sanford**

**Malcolm Duren**

### - What is "constexpr"? ###

 C++11 introduced the new keyword `constexpr` with the purpose of simplifying metaprogramming. Similar to writing constant expressions using the keyword const, `constexpr` was also created to evaluate and use expressions during the program compilation time. C++11 took the concept of const and extended it to evaluate function calls, objects, and variables at compilation time as opposed to run time. Although things like this were possible before C++11, `constexpr` is meant to be more coder-friendly than alternatives such as templates, which require much more code. As most optimizations to programming languages, `constexpr` is meant to increase the speed of programming and decrease the amount of code necessary for the purpose of a program.  

### - Explain why it’s useful ###

Most C++ programmers are familiar with the utility of `const` declarations--often times a value needs to be computed only once despite being used multiple times. Although a variable can be used to store this computed value, the compiler will not recognize on its own that the data in this variable is unchanging throughout execution.  This can prevent the compiler from optimizing code where possible.  Worse still, the compiler will not be able to use the value of this variable to allocate static memory, because the size of this memory needs to be known at compile time.  Therefore the prefix `const` can be used to indicate a value that needs to be computed at compile time; allowing the data to be referenced at compile time for use in static memory allocation and compiler optimizations.  Additionally, this decreases runtime by allowing the computation to occur before program execution (though in simple computations the effect might not be noticeable, in more complex computations this could be very useful). However, the const operator has one major shortcoming--it is not compatible with function calls. This makes it difficult and inconvenient to declare constants that rely on the result of computations involving more than one line of code. The use of `constexpr` makes these function-dependent constants possible. A common example of when this would be useful convenience is a `DegreesToRadians` function. If declaring multiple radian constants, one can simply build a function which converts degrees to radians rather than explicitly performing the conversion at each `const` declaration. 




### - How did the community react to this improvisation. ###

Since writers of programming languages are always looking to improve their features and coders are always looking to use the most efficient code, it is important to see how people react to a change. The C++ community received this particular revision both negatively and positively. Most  people seem to like the idea of `constexpr`, but wish it expanded `const` more than it does so far. Most C++ users are  pleased with the speed of their programs that implement using `constexpr` and the amount of code they need to use. However, many users are complaining about the restrictions of `constexpr`. For example, in a StackOverflow post, 
> "NoSenseEtAl” 

points out that for `constexpr`, a function has to have a non-void return type and 
There must exist argument values such that, after argument substitution, the expression in the return statement produces a constant expression." A user that contributes his ideas of revision states that 

> These restrictions on `constexpr` function definitions are still very severe, and the relaxation of the rules has resulted in them becoming harder to teach and to justify. Non-trivial `constexpr` functions tend to be complex and to use a style of coding which is unfamiliar to many, because code must be contorted to fit within the syntactic constraints, even if it already has a pure functional interface." 

He goes on the propose more changes to use `constexpr` to its fullest potential. 




### - What exactly does this add to the C++ Language? ###

`constexpr` grant programmers of C++ a much more controlled way to optimize in terms of compile time computations. A set of computations (think of a function) that can be run at compile time is inherently going to be deterministic and can run independent of the mutable global state of the program. If this is true a programmer can run this code and always know what it will produce prior to run time. `constexpr` also allows the programmer to deliberately indicate what computations have this quality, and give the compiler the green flag to go ahead and make optimizations where possible. One would think that this is an open door to throw the `constexpr` in front of every fit expression and let the compiler sift through it all. However, the current state of this specifier would suggest that it should be used in a very particular manner. For example when describing a `constexpr` function the conditions include the forbidding of declaring any sort of mutable variable within the scope of that function, which proves challenging when you have a computation that requires an iterative process. 

  constexpr int iterate(int n) 
  	 {
     int x = n;    // Does not follow constexpr rules
     while (--n > 1)
	   x *= n;
     return n;
   	 }

Needless to say  if `constexpr` is trying to revolutionize the way we program in C++ its limitations are hindering it from doing so. In spite of these shortcomings, `constexpr` does provide the language with syntax that is easier to read, easier to write, and code that is faster. With any programming language this is always a good thing.



### - Relation to topics learned in class ###

Functions that are declared with `constexpr` are required to have no side effects, as they are required to be executable at compile time, when no memory has yet been established.  In this sense, they are functional, avoiding the use of states and mutable data--this way the compiler knows that calling the function with a specific set of parameters will always return the same result, regardless of when it is called.  Given this guarantee, the compiler is free to make optimizations in places that it couldn't have before--one of the prominent benefits of functional programming. Declarations using `constexpr` also benefit from other advantages of functional programming, such as enhanced readability. C++’s `constexpr` also bears resemblance to functional programming in its emphasis on recursion for finding the solutions of complicated calculations as opposed to iteration--the current limitations of `constexpr` prevent data from being saved in mutable variables (and therefore the programmer is barred from using iteration).  This effectively creates a small facet of the otherwise empirical C++ that is entirely functional.  




### - Conclusion ###


`constexpr` is an excellent example an amendment to C++ that is more or less in the grey area between being generally useful and overlooked in the community. In the prior regard, it proves useful for very particular situations, and in the latter its own restrictions bar some uses for it that would prove beneficial to most people. It addresses the very verbose and ugly looking code that template metaprogramming uses, and it is something that the user must use to their discretion if they want to get the full effect, as `constexpr` tells the compiler something can be optimized but not necessarily something has to optimized. Many suggested improvements to `constexpr` come from the same idea in other languages, but for the now the status quo is maintained and it is up the C++ community to use what we have to its fullest potential. 



##Collaboration##
- Our collaboration was using GoogleDocs, as we couldn't get git to work in time
for turn in. [Googledocs](https://docs.google.com/document/d/1VRJY603obCnV3rj6AcUz7KYbllAneMpU6NDkLFUHIMQ/edit#heading=h.6uymmw4m3v8c "constexpr in C++")




### Good Sources ###

- [http://en.wikipedia.org/wiki/C%2B%2B11#constexpr_.E2.80.93_Generalized_constant_expressions](https://docs.google.com/document/d/1VRJY603obCnV3rj6AcUz7KYbllAneMpU6NDkLFUHIMQ/edit#heading=h.6uymmw4m3v8c)

- [http://cpptruths.blogspot.com/2011/07/want-speed-use-constexpr-meta.html](http://cpptruths.blogspot.com/2011/07/want-speed-use-constexpr-meta.html)
[http://stackoverflow.com/questions/4748083/when-should-you-use-constexpr-capability-in-c11](http://stackoverflow.com/questions/4748083/when-should-you-use-constexpr-capability-in-c11)
- [http://www.cprogramming.com/c++11/c++11-compile-time-processing-with-constexpr.html](http://www.cprogramming.com/c++11/c++11-compile-time-processing-with-constexpr.html)
- [http://blog.smartbear.com/software-quality/bid/248591/Using-constexpr-to-Improve-Security-Performance-and-Encapsulation-in-C](http://blog.smartbear.com/software-quality/bid/248591/Using-constexpr-to-Improve-Security-Performance-and-Encapsulation-in-C)
- [http://www.informit.com/guides/content.aspx?g=cplusplus&seqNum=315](http://www.informit.com/guides/content.aspx?g=cplusplus&seqNum=315)
- [http://stackoverflow.com/questions/8308812/why-is-c11-constexpr-so-restrictive](http://stackoverflow.com/questions/8308812/why-is-c11-constexpr-so-restrictive)
- [https://groups.google.com/forum/?fromgroups=#!topic/comp.std.c++/BPR0KgrHcRU](ttps://groups.google.com/forum/?fromgroups=#!topic/comp.std.c++/BPR0KgrHcRU)
- [http://akrzemi1.wordpress.com/2012/12/13/constexpr-unions/](http://akrzemi1.wordpress.com/2012/12/13/constexpr-unions/)
- [http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3597.html](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3597.html) 
- [http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2235.pdf](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2007/n2235.pdf) 
