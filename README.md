# INTERVIEW QUESTIONS
# -------Kotlin-------
# 1. What is Inline function in kotlin?
Ans: Inline function is a function followed by 'inline' keyword. When we use inline keyword before a function name ,the compiler does not allocate the memory.Wherever this function is invoked the piece of code is copied at calling place.
# 2.What is Object Declaration and Expression in Kotlin?
**Object Declaration**<br />
Ans: A way of creating object without class with help of 'object' keyword is called object declaration.Object has similar property as class but difference is that multiple objects can be created of same class while in case of object is not.
e.g-
```
fun main() {
    println(shape.str)
    println("Square is: ${square.area(10)}")
}
//creating first object having name 'shape'
object shape {
    val str = "This is shape object"
}
//creating second object having name 'square'
object square {
    fun area(edge: Int): Int {
        return edge * edge
    }
}
```
**Object Expression**:<br />
A way of creating an object without giving any name ,is called obeject expression .object expression can include function also i.e
```
fun main() {
    println(message)
    println("Square is: ${square.area(10)}")
    //creating second object expression
    var obj_express = object {
        val x = 10
        fun area() {
            println("Result is: ${x * x}")
        }
    }
    println(obj_express.area())
}

//creating first object expression
val message = object {
    val str = "This is shape object"
}

//declaring second object
object square {
    fun area(edge: Int): Int {
        return edge * edge
    }
}
```
# 3.Difference between 'object and class'.
# 4.What is singlton class and how to make it in kotlin?
# 5.Different between class and data class.
# 6.What is enum block in kotlin and why it is used.?
# 7.Types of constructors in kotlin?
# 8. Can we create constructor in abstract class?
# 9. Difference between interface and abstract class.
# 10.What is root class of exception? and diff. between checked and unchecked exception?
# 11. How can we create custom exception?
# 12. What is OOP?
# 13. What is sealed class why it is used?
# 14.What is Coroutine in kotlin?
# 15.What are dispachers.Explain?

# -------Android---------
# 1.Explain all states of activity?
# 2.What is android architecture?
# 3.What are the permission levels in android?
# 4.What are the lunch mode and why it is used?
# 5.Explain room database? How this is deffrent from sqlite db?
# 6.How to merge two table data in room?
# 7.State of activity when it coverred by popUp?
# 8.Explain Push Notification?
# 9.What is deep linking in android?
# 10.How Make base url dynamic?
# 11.How to save data after changing the configuration of app?
# 13.What are android components?
# 14.What is jetpack components?
# 15.Why developer used MVVM architecture?
# 16.Difference between intent and intent-filter?
# 17.How communicate between fragments?







