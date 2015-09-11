---
layout: post
title: Week 2! Blocks, procs and lambdas.
---


Blocks are chunks of code, associated with methods, and are a fundamental part of the Ruby language. The block is given either between braces {} or between a do-end statements after the method name. It describes how you want ruby to execute the method on the object or elements of the object upon which it was called.

```
[1,2,3].each { |x| puts x*2 }   # block between the curly braces

[1,2,3].each do |x|
puts x*2                    # block between do and end statement
end

# both of the above return
# 2
# 4
# 6
```

The big difference between blocks and procs is that procs are objects and blocks are not. So a proc is like a block that can be stored, used and passed around just like any other objects. Procs can also be passed into methods as arguments, meaning you can pass multiple procs to methods but blocks can only appear once in the method call.

```
p = Proc.new { |x| puts x*2 }       # When entering procs as arguments in methods 
[1,2,3].each(&p)                    # they are preceeded with an '&' telling ruby
                                    # to turn the proc into a block
# again, returns
# 2
# 4
# 6
```

Lambdas are in fact also objects of the Proc class, they are just a different 'style' of proc. The three fundamental differences are:

* Lambdas require explicit creation - Wherever Ruby implicitly creates proc objects they are regular procs and not lambdas. Lambdas must be created using the 'lamba' keyword or -> syntax (see examples below).

* Lambdas and Procs treat the return keyword differently - Return inside a lambda triggers an exit from the body of the lambda, however return inside a proc triggers a return from the method in which it is being executed.

* Lambdas can only be called with the correct number of arguments - A regualr proc will run no matter how many arguments are given (it just ignores additional arguments given or runs with zero arguments). A lambda, however, will raise an error.

```
proc = Proc.new { puts "Hello world" }
lam1 = lambda { puts "Hello World" }
lam2 = -> { puts "Hello World" }

proc.class # returns Proc
lam1.class  # returns Proc
lam2.class # returns Proc
```

