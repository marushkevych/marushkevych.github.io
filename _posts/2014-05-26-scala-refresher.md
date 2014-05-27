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

There are lots of resources on the net, but for me this book is the best way to refresh my scala: 
[Seven Languages in Seven Weeks](http://pragprog.com/book/btlang/seven-languages-in-seven-weeks)

Here I'll document the most helpful reminders...

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
object Person{
    def staticMethod = println("i'm static")
}

Person.staticMethod()
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
