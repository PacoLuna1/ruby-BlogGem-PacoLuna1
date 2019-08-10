This document will throw you for all the steps that you need to write your own Ruby gem. Starting with...

### What is a Ruby gem?

If you don't know what a Ruby gem is let me tell you that you have serious problems. But keeping you a few minutes that possibly you were thinking to spend searching in google. 

> A gem is a library that contains a specific piece of functionality as well as any files or assets related to that functionality. 

Inside gems are the following components:

* Code (including tests and supporting utilities)
* Documentation
* gemspec

The next spect you have to learn to create your first Ruby gem.

### What is bundle?

I know. This blog seems more informative and a little borring, but it's not. Gem and bundle are esencial concepts that you will need in the next step to check your possible errors in the magic Google or any searcher you want.

> Bundle is a tool created by Carl Lerche, Yehuda Katz, André Arko and various superb contributors for managing Rubygems dependencies in Ruby libraries.

Now the moment you were waiting all this time...

## How to Create a Ruby Gem?

The first thing you need to do is install **bundle**. I told you that you would need it.
this is the link: https://bundler.io/.
  
If you are in linux just type in your terminal ``` gem install bundler ```

When the instalation finish, with this simple command ``` bundle gem example ``` you will have your first example gem. 
_Notice that "example" can be what ever name you want_.

That command will create a scaffold, where each folder and file have a certain purpose.
* example.gemspec : In this file you can configure or add any dependecy you want.
* Gemfile: Used to manage all gem dependencies for our library.
* Rakefile: Requires bundler and adds the ``build``, ``install`` and ``release`` rake tasks.
* .gitignore: This file ignores the files that you don't want to have in your repository and anything with a .gem or .bundle extension.
* lib/example: In this folder you shouls contain all your code (classes, methods, modules, etc..) for the ruby gem.
* lib/example.rb: Is the main file to define and control all the code that is in de ``lib/example``.
* lib/example/version.rb: Define a constant version for the gem specification that is loaded by example.gemspec.

All this files are esencial to develop your first Ruby gem.

## How to test our gem?

It exists a lot of testers(Rspec, minitest, etc..) in this blog I will explain you how to test with Rspec.

#### Why to test? 

We write test to ensure that our code have the structure and funtionality we want without having any possible error or bug.
Testing our code has to be the first step you should do  when you are developing a gem even more important than writing your main code according to the TDD(Test-Driven Development) process.

#### Steps

To get started with our test. We have to create a folder with the name ``spec``. Then we will specify in our example.gemspec that Rspec is going to be our developmente dependency for test with the next piece of code: ``spec.add_development_dependency "rspec", "~> 3.2"`` to install this and all the default dependencies we have to go to our teminal in our proyect directory and run ``Bundle install``.

To check if our Rspec was correctly installed we will type and run in our terminal ``bundle exec rspec`` it has to print this statement.

`` 0 examples, 0 failures``

It's successfully installed.

## Example of a Ruby gem

To be sure that you understand how to create your first Ruby Gem, I will explain briefly  a little example with our current gem.

Firstly, create a new file in the spec folder with this name ``example_spec.rb`` the word _spec its what we told bundle to execute, when we want to run a test.

When you create your _spec file, you have to write this code.

```
require 'example'
    describe Calculator do
      let (:operation) { Calculator.new }
      it 'Sum results a number' do
        expect(operation.sum(10,12)).to eq(22)
      end
    end
```

Then we are going to run ``bundle exec rspec`` in our terminal.

```
Failure/Error:
  describe Calculator do
    let (:operation) { Calculator.new }
    it 'Sum results a number' do
      expect(operation.sum(10,12)).to eq(22)
    end
  end
NameError:
  uninitialized constant Calculator
```

You will watch a different statement from the first we saw to prove that it was correctly installed, this will told you step by step what is missing in your code, to make this test work.



According with the first error we need a class Calculator

```
class Calculator
end
```
Run again ``bundle exec rspec``

Method error:

```
Failure/Error: calculadora.sum(1,2)
NoMethodError:
  undefined method `sum' for #<Calculator:0x000055b912ec49a8>
```
We have to create a method which its name will be 'sum' with 2 parameters ``sum(number_one,number_two)``
```
class Calculator
  def sum(number_one,number_two)
  end 
end
```
Run the last time ``bundle exec rspec``

Operation error:

```
Failures:
  Calculator Sum results a number
     Failure/Error: expect(operation.sum(10,12)).to eq(22)
       expected: 22
            got: nil
       (compared using ==)
1 example, 1 failure
```

The last step is that both parameters have to sum each other.
 
 ```
 class Calculator
  def sum(numberOne,numberTwo)
      numberOne + numberTwo
  end 
end
```
Finally you know how to create your first Ruby gem.

## Congratulations!!

```1 example, 0 failures```


_______________________________________________________________________________________________________________________

#### Instructions
##### Writting a Ruby Gem

* You must write a document that details the process of writing a Gem using Ruby. 
* The document must be written in a way so others can follow it to create a ruby gem.ruby on rails install
