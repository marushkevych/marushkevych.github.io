---
layout: post
title:  Scala refresher
tagline:  
date:   2014-05-26 10:00:00
categories: scala
---

Scala is one of those languages (for me at least) that need constant use in order to stay in my head. 
I completed "Functional programming in Scala" course more then year ago, doing pretty advance stuff in Scala, 
but now going back to it I found lots of gaps in my Scala part of the brain.

There are lots of resources on the net, but for me this book is the best way to refresh my Scala: 
[Seven Languages in Seven Weeks](http://pragprog.com/book/btlang/seven-languages-in-seven-weeks)

Official Scala [cheatsheet](http://docs.scala-lang.org/cheatsheets/) is very complete and concise.

Here I'll document the most helpful reminders...

## Pattern Matching Anonymous Functions

```scala
val b = List(1, 2)
b map {
    case 1 => "one"
    case 2 => "two"
}
```

## Anonymous Functions as blocks

```scla

def myMethod(value:File,x: (a:File) => Unit) = {
   // Some processing here
   x(value)
}

myMethod(new File("c:/"), x => { 
  if (x.toString.endsWith(".txt")) {
    println(x) 
  }
})

// An alternative is way to define myMethod as a curried function
def myMethod(value: File)(x: File => Unit) = x(value)

myMethod(new File("c:/")) { x => 
  if (x.toString.endsWith(".txt")) {
    println(x) 
  }
}

```

## ranges
    
```scala
scala> val inclusiveRange = 0 to 10
scala> val range = 0 until 10
```

for loop using range: `for(i <- 0 until args.length)`

## tuples

```scala
val person = ("Elvis", "Presley")
person._1
person._2

val (first, last) =  ("Elvis", "Presley")
```

## classes

```scala
class Person(firstName: String, lastName: String)
val gump = new Person("Forrest", "Gump")

// Constructors
class Person(firstName: String) {
    println("Outer constructor")
    def this(firstName: String, lastName: String) {
        this(firstName)
        println("Inner constructor") 
    }
    def talk() = println("Hi") 
}

// static elements - use singleton objects
object Person {
    def staticMethod = println("i'm static")
}

Person.staticMethod()
```

## companion object factory

```scala
class Person(firstName: String, lastName: String)

object Person {
    def apply(fullName: String){
        new Person(parseFirstName(fullName), parseLastName(fullName)
    }
}

val person = Person("Elvis Presley");

```

## Inheritance

```scala
class Person(val name: String) {
    def talk(message: String) = println(name + " says " + message) 
    def id(): String = name
}

class Employee(override val name: String, val number: Int) extends Person(name) {
    override def talk(message: String) {
        println(name + " with number " + number + " says " + message)
    }
    override def id():String = number.toString 
}
```

## traits

```scala
class Person(val name:String)
trait Nice {
    def greet() = println("Howdily doodily.")
}
class Character(override val name:String) extends Person(name) with Nice
val flanders = new Character("Ned") 
flanders.greet

// or extend trait directly:
class Person(val name: String) extends Nice
```

