# Notes on MATLAB
or 
# A data science approach for MATLAB

Well, MATLAB is probably the standart programming tool for engineers and scientist. I wrote this note for students at University of Khartoum (5th and 4th year students). I really wish that they help "someone somewhere sometime". Notice that, these notes are by no mean comprehensive! They are only intended for data scientists a.k.a not computer scientists. They are also meant to be as a complemetary materials for my sections.


## What is pogramming?

I do not have any formal definition of what programming is, I might though reference you to a [wikipedia entry](https://en.wikipedia.org/wiki/Programming_language). But this is not how I intended to write this notes. During my studies, I saw that many of my colleagues hate programming, or they are just scared of it. I also saw many students having the same feeling about it. The reason for that is pretty simple. They just do _not_ like it! Thats it. Our brains are incredible at augmenting things, and making us believe in them. My goal of these notes is not to make you love programming (though that would be very cool). I just want to you to be aware of the importance of the programming languages for your career, or research.

## Notes

In this note we are using MATLAB as our programming language--though, I would prefer to use Python. The reason for using MATLAB--as we have mentioned earlier--is that MATLAB is the standard tool in engineering classes. I mean, I see that students are often hate MATLAB, giving them another programming language as an example will not help a lot. MATLAB is also oriented towards science and engineering. Having said that, it should be clear that all the code written here is compatible with MATLAB and also Octave. Some of these code may or may not be compatible with Python's NumPy, so be noticed.

## Open source vs proprietary stuffs

As I mentioned, we will be using MATLAB, but all of our code will be fully compatible with Octave. In fact, I will write the whole codes in Octave, and make sure that they are fully compatible with MATLAB. Open source tools e.g., NumPy has accomplished huge success in the past years. In fact they might have surpassed their companion proprietary software. This tells us that, now, it becomes even more wiser to use them. 

## Low level programming languages vs high level ones

I promised that this won't be %100 geeky post. But I really had to write this one. MATLAB is a high level programming language, and an interpreted one. Unlike in C/C++ or Java, you do not have to compile->run. In MATLAB, you always just run. This has advantage of decreasing the steps the programmer has to do until he gets his programm running, but it also makes the interpreted programming languages are far slower than compiled ones. Again, you do not need to know why this happens, if you are interested, you may read [his](http://stackoverflow.com/questions/3265357/compiled-vs-interpreted-languages) though. The lesson to take away here is, we use interpreted programming languages because they are just faster for the developer than compiled ones. [While interpreted programming languages are known to be much slower than the compiled ones, they are also easier to work with than the compiled ones. So, this is the tradeoff.]

## Even if you have not use any programming language before, you still used programming

I just want to familiarize you with programming. You have used programming at some sense. If you have ever used a calculator, scientific one would be perfect, but non-scientific are also acceptable, then you are exposed to programming! When you are taking a sine for some value, you are under the hood using a programming. Let's take this demonstration of what you are doing

```matlab 

% Assuming you have opened you calculator, you know the `On` button, and you want to compute the sine for some value
% So, you click on `sin` button, and enter that value, and then you close the paranthese.
sin(45)
 1/sqrt(2)

```

From taking the sine _function_ using your calculator we get the following

- There is a language, or a way to interact with you calculator. It's called a _syntax_.
- The notion of the _function_, it is very similar to the mathematics one. A sine in math is a function, that takes as input one value, and returns its value, using some _defined_ rules.
I really ask you to spend some time of analysing what your calculator is doing, and compare it with what would you do. That is really important, programming is not invented for fun, it is used to solve problems, to ease your life!

Let us move to other part. I ask you to tell me how addition is working! I would say something like this


- I want to write a program that computes the addition of two numbers, or may be more.
- First, I need to get the numbers that I would want to add.
- Second, perform the addition operator on them, store the results in some `variable`, so that I can retrieve them later.
- print out the result of this program.
Again, we are really not so obsessed with how this "add" operator is magically implemented in our computer!

```matlab
function result = add_function(a, b)
 result = a + b
 return result
```
Well, this code does exactly that, only it is not valid for any programming language! In analysing this code, we get the following

- We have this _keyword_ "function" that tells our computer about itself. More importantly, it tells the computer that this part of the program is its block! This is really important, because your program might have any number of functions inside it. Your computer needs to know exactly, what goes where.
- We have also that notion of _algorithm_, or steps for solving this problem. We first get the numbers, then add them together, store the value of the addition to some variable.

In your calculator if you do something like

```matlab
    sin(34 + cos(43)
```
you will get an error, a _syntax_ error. Because that thing in your computer and calculator that translates what you write into a machine language encoutered something wrong. In this case it is clear that there is a missing paranthese.
Errors (or bugs) are probably the most common things when you write programs, we are human, after all. 

## About MATLAB

MATLAB is designed around Matrices. In fact, its name actually is an abbreviation for MATrices LABoratory. Every numerical thing in MATLAB is a matrix. Even numbers e.g., 1,2, 3 are just (1 by 1) matrix. In linear algebra, we study how we solve a system of equations using matrices. It turns out that this way is very fast and easy to represent in a computer memory than the other way. 

## Section 1

I could not find a good name for these sections. So, I just named them section{1..n}.

We are talking about computations. The whole story is just about that. While you can easily find the multiplication of two numbers, or divide them etc. and you can also compute the determinant of (3,3) matrix. It becomes very difficult to e.g., compute the determinant of (5,5) matrix. While some would argue that they can solve such problems, the idea is that it takes too much time and effort for something that needs no creativity at all! But again, there these kind of problems when a typical human cannot just solve.  Programming languages are as _important_ as the calculator. You should definitely think of them like that. The time you spend on learning a programming language is often more than that of solving a problem using e.g., your calculator. Your calculator is limited to (3,3) matrix operations, and programming languages are limited by your memory size! While you can handle many of the problems using your calculator, remember that these problems in textbooks are by no means a reflection of what practical problems are. They are just to give an idea of the tools and the techniques of solving such problems. So, you really need to lean programming.

Let us go to this practical example of solving a problem.

### Problems
The square root problem.

There are many algorithms for solving the square root, but we will use a very simple one.

**Our algorithm**. Let _N_ denotes the number that we want to take its square root. The solution is some number between (0, N). Let the lower bound be _lower_, and the higher bound be _upper_, and the solution be _sol_. We need to find a number between (lower, upper). As a good choice, we choose it to be the middle of them (can you guess why?). We can use the brute force solution of trying each number starting from zero to N (remember N is the number we want to find its square root). Using our strategy of divide and conquer, at each step, we will decrease the solution space by a half. If the solution^2 is greater than N, that means the solution is in the lower bound. Else, it is in the upper bound. 

![this figure demonstrates the idea of divide and conquer](drawing.png)
In this figure, we have _L_ that denotes the lower bound, _U_, denotes the upper bounds, and _S_, which is our guess solution. So, if S * S > N, then we let the upper bound equals to S. If the S * S < N, we will let the lower bound equals to S. If else, then we find our square root, that is N = S.
![This figure demonstrates the solution strategy](flowRoot3400.png) 

Let us write our algorithm using a pseudocode.

```
lower = 0
upper = N
guess = (lower + upper) / 2
epsilon = 1e-4
repeat untill abs(guess - N) <= epsilon
    if guess*guess > N % the solution is some where between lower and guess
        upper = guess
    else if guess*guess < N % the solution is some where between guess and upper
        lower = guess
    else
        N = guess
        % We may use break, for now we may not need it so much.
    guess = (lower + upper) / 2
```

Well, give yourself a few moments and study this code. 

In the first three lines of this program, we have initialized our variables: `lower, upper, and guess`. The idea of our algorithm is to divide the solution space at each time by half. If we are dealing with a space of size _m_ in the first pass, then in the second pass will be dealing with a space of _m/2_ by ignoring a half of the the solution space. We will do that untill convergence! The question is, when do we converge? We are limited by our floating point precision [consult this wiki entry](https://en.wikipedia.org/wiki/Floating_point). But simply that means, your computer cannot process an infinite number. They have limitations (32 bit, or 64 bit). In our case, we might not need to do that, but you need to know it anyway. 
For our first guess we set it to be `(lower + upper) / 2`. Then, we need to set some convergence criteria, so that we avoid going too much. In this case, we want our solution to have an accuracy of e-4 i.e., accuracy for the 4th floating point. Untill this step the program should be somewhat easy for you to understand.
In the 5th line, we have introduced a slightly new concept for you, loops.

### Loops in MATLAB
So far we have not actually written any MATLAB code, and that was intended. Let us pick up from where we have lefted in our discussion of square root program. We have stopped at the concept of the loops.
Before we go any further, let us remind ourseleves of what we want to achieve. We want to divide the solution space at each time by a half. To do that, we want to update our solution boundaries e.g., updating `lower` and `upper` bounds, and `guess` accordingly. 