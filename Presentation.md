Constant Expression
=====================

###C++  `constexpr`###

**Hope Sanford**

**Levi Davis**

**Malcolm Duren**



---
### Introduction ###

##### What is the goal of using `constexpr`? #####


 - Increases C99 compatibility. 

 - Improves support for: 
 	
 	- Generic programming 
 	- Systems programming 
	- Library building

 - Builds on `const`

 ---

### Introduction cont...  ###

##### What is the goal of using `constexpr` #####

 - Compilation time vs. Run time

 - Coder friendly syntax

 - Speed of programming


---

### Introduction cont...  ###

##### Simple Example #####
	
	int get_five() {return 5;}
 	int some_value[get_five() + 7]; // Create an array of 12 integers. Ill-formed C++

vs.

	constexpr int get_five() {return 5;}
 	int some_value[get_five() + 7]; // Create an array of 12 integers. Legal C++11


---
### Why is this useful? ###

##### Static Memory Allocation #####

 - Static arrays cannot be allocated with non-const sizes
 	- Using a function was previously impossible


	constexpr int cubed(int n) { return n*n*n; }
	
	int static_array [ cubed(25) ];


---
### Why is this useful? ###

##### Programmer Convenience #####

 - constants can be computed using functions.

	- Useful for repetitive `const` declarations.
	- Decrease code 

---
### Why is this useful? ###

##### Programmer Convenience - An example #####

	constexpr double degToRad (double deg) { return deg*M_PI/180; }
	const double Angle1 = degToRad(165);
	const double Angle2 = degToRad(230);
	const double Angle3 = degToRad(47);

vs

	const double Angle1 = 165*M_PI/180;
	const double Angle2 = 230*M_PI/180;
	const double Angle3 = 47*M_PI/180;


---
### Why is this useful? ###

##### Runtime Efficiency #####

 - Heavy computations can be done at compile time vs run time.
	
	- Recursive functions
		


---
### Why is this useful? ###

##### Runtime Efficiency - Some code #####

	constexpr int fibonacci(int n)
	{
		return (n == 0 || n == 1) ? (1) : (fibonacci(n - 1) + fibonacci(n - 2));
	}
	
	const int Fib10 = fibonacci(100);
	const int Fib20 = fibonacci(200);
	const int Fib30 = fibonacci(300);


---
### How does this improve the C++ language? ###

 - Nature of running at compile time...
	- Deterministic
	- Runs independent of mutable program
		- Sound familiar?
	
---

### Technicalities ###

 - Compiler sets rules for `constexpr`
	
 	1. Can't declare any mutable variables within a `constexpr` function.
 	
	2. Return must be `LiteralType`
		
		> 3 + 5

		> 
			
	
	3. Must return ONE value
	

	What if you **need** an iterative process?
 		

		constexpr int iterate(int n) 
  	 	  {
     	  int x = n;    // Does not follow constexpr rules
     	  while (--n > 1)
	 	   x *= n;
          return n;
   	 	  }


---

### Reaction ###

##### How did the community receice this revision? #####
	 
	 
**Postitive Reactions**

 - General idea
 
 - Speed

 - Amount of code

---

### Reaction ###

##### How did the community receice this revision? #####

**Negative Reactions**

 - return type

 - Incompatible with most algorithms from standard library.

 - Syntax restrictions
 	- `if` statement vs ternary if `? :`



### Reaction ###

##### How did the community receice this revision? #####

**Negative Reactions cont...**'


 - Difficulty working around the restrictions

 - "Harder to justify and teach the use of `constexpr`".

 - Speed is not improved in some situations.

---


### Conclusion ###
ackvnldjksn
##### 


