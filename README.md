# INTERVIEW QUESTIONS
# -------Kotlin-------
# 1. What is Inline function in kotlin?
Ans: Inline function is a function followed by 'inline' keyword. When we use inline keyword before a function ,the compiler does not allocate the memory.Wherever this function is invoked the piece of code is copied at calling place.
# 2.What is Object Declaration and Expression in Kotlin?
**Object Declaration**<br />
Ans: A way of creating object without class with help of 'object' keyword is called object declaration.Object has similar property as class but difference is that multiple objects can be created of same class while in case of object is not.
e.g-
```fun main() {
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
Ans:There are following key difference:
   1. A **class** is blueprint of objects while an **object** is real-world entity.
   2. A **class** is logical entity while an **object** is physical entity.
   3. A **class** is created using 'class' keyword while 'object' is created either using **new** keyword or using class reference(in kotlin). 
 
# 4.What is singlton class and how to make it in kotlin?
Ans:Singlton class is a class that is defined in such a way that only one instance of the class can be created and used everywhere in project.
**In Java**
```
public class Singlton{

private static Singlton instance=null;
//creating constructor
private Singlton(){

}
//creating instance of singlton class
public static Singlton getInstance(){
if(instance==null){
synchronized(Singlton.class){
if(instance==null){
instance=new Singlton();
}
}
}
return instance;
   }
 }
}
```
**Note:**  **synchronized** keyword ensures there is no any thread interference(i.e sharing multiple thread same data).
<br />
**In Kotlin:**
```
object Singlton{
init{
  println("This is init block")
}
//crating local variable
var name="Vikash kumar"

fun printName(){
println(name)
}
}
```
# 5.Different between class and data class.
Ans: **Class** <br/>
A class is blueprint for an object.It shares common properties and behaviour in form of members and member functions.
```
class Shape{
//creating member 'edge'
  val edge=10
//creating member function 'are'
fun area(){
println(edge*edge)
}

fun main(){
//creating instance or obejct of shape class
val shape=Shape()
println(shape.edge)
shape.area()
}
}
```
**Data class**<br/>
Data class is a simple class which is used to hold data/state and contains standard functionality.
A **data** keyword is used to declare data class.With the help of data class we reduce the boilerplate code.
When we compile the code , the compiler automatically creates ```equals```, ```hashCode```,```toString``` ,```copy``` functions.
```
data class MobileData(
val version:Double?=null,
val modelName:String?=null,
val buildNumber:String?=null)
 
```
# 6.What is enum block in kotlin and why it is used.?
Ans: When we want to store a set of same type of constant values to single variable, **enum** class comes in front.
Each enum constant is an object. it has some inbuilt properties and functions which can be used in programing.
<br/> **Properties:** <br/>
1.**ordinal:** This property stores the ordinal value of the constant, which is usually zero-based index.<br/>
2.**name:** This property store name of the constant.<br/>

**Methods -** <br/>
1.**values:** This method returns a list of all contants defined within the enum class.<br/>
2.**valueOf:** This method returns the enum contant defined in enum class on basis of matching the input string. if the input string is not present in enum class then it returns illegalArgumentException is thrown. Each enum constant is seperated by comma.<br/>
**E.g** <br/>
```
enum class Days{
SUNDAY,
MUNDAY,
TUESDAY,
WEDNESDAY,
THRUSDAY,
FRIDAY,
SATURDAY
}

fun main(){
for(day in Days.values()){
println("${day.ordinal}:${day.values}"
}
println("${day.valueOf("MONDAY)}"
}
```

# Collections in Kotlin
Ans: There are following collections in kotlin for grouping elements:<br/>
 i.Lists<br/>
 ii.Sets<br/>
 iii.Maps<br/>
 **List**<br/>
 There are two functions for grouping items in list<br/>
 a.```listOf()``` function -> This function is used to create read-only(i.e immutable list) type list.<br/>
 ```
fun main(){
readOnlyList()
}
fun readOnlyList(){
    val courseList= listOf<String>("Java","Python","Kotlin","C#","C")
     courseList.add("C++")//this will produce an error because above list can not modify
    println("First element of list is: ${courseList.first()}")
    println("Last element of list is: ${courseList.last()}")
    println("No. of element of list is: ${courseList.size}")
    println("***********************************************************")
}
```        
 b.```mutableListOf()``` function -> This function is used to create dynamic(i.e mutable list) type list<br/>

 ```
fun main(){
mutableListItem()
}
fun mutableListItem(){
    val courseList= mutableListOf<String>("Java","Python","Kotlin","C#","C")
    courseList.add("C++")
    println("First element of list is: ${courseList.first()}")
    println("Last element of list is: ${courseList.last()}")
    println("No. of element of list is: ${courseList.size}")
}
```        
**Set**
Set is also used to create list of items but difference is that it drops the duplicate item from the list and its item can not retrive by index like list.<br/>
**Note:** As sets are unordered, you can't access an item at a particular index.
<br/>
i.e<br/>
**immutable set's item**
```
fun main(){
readOnlyList()
}
fun readOnlyList(){
    val courseList= setOf<String>("Java","Python","Kotlin","C#","C","C++")
     courseList.add("C++")//this will produce an error because above list can not modify
    println("First element of list is: ${courseList.first()}")
    println("Last element of list is: ${courseList.last()}")
    println("No. of element of list is: ${courseList.size}")
}
```
**mutable set's item**
```
fun main(){
readOnlyList()
}
fun readOnlyList(){
    val courseList= mutableSetOf<String>("Java","Python","Kotlin","C#","C","C++")
     courseList.add("C++")
    println("First element of list is: ${courseList.first()}")
    println("Last element of list is: ${courseList.last()}")
    println("No. of element of list is: ${courseList.size}")
}
//Output:
```
# 7.Types of constructors in kotlin?
Ans:A constructor is a concise way to initialize class properties.<br/>
It is a special member function that is called when an object is instantiated (created). <br/>
In Kotlin, there are two types of constructors:

Primary constructor - concise way to initialize a class
Secondary constructor - allows you to put additional initialization logic. 

Primary Constructor<br/>
The primary constructor is part of the class header. Here's an example:<br/>
```
fun main(args: Array<String>) {

    val person1 = Person("Joe", 25)

    println("First Name = ${person1.firstName}")
    println("Age = ${person1.age}")
}

class Person(val firstName: String, var age: Int) {

}
```
<br/>
There are other ways of using primary constructors.<br/>
Primary Constructor and Initializer Blocks<br/>

To put the initilization code (not only code to initialize properties), initializer block is used. It is prefixed with init keyword. Let's modify the above example with initializer block:
<br/>
```
fun main(args: Array<String>) {
    val person1 = Person("joe", 25)
}

class Person(fName: String, personAge: Int) {
    val firstName: String
    var age: Int

    // initializer block
    init {
        firstName = fName.capitalize()
        age = personAge

        println("First Name = $firstName")
        println("Age = $age")
    }
}
```
<br/>
# Kotlin Secondary Constructor
In Kotlin, a class can also contain one or more secondary constructors. They are created using ``` constructor ``` keyword.
<br/>

```
class Log {
    constructor(data: String) {
        // code
    }
    constructor(data: String, numberOfData: Int) {
        // code
    }
}

class AuthLog: Log {
    constructor(data: String): super(data) {
        // code
    }
    constructor(data: String, numberOfData: Int): super(data, numberOfData) {
        // code
    }
}

```
Here, constructors of the derived class AuthLog calls the corresponding constructor of the base class Log. For that, super() is used.
# 8. Can we create constructor in abstract class?
Ans: Yes! an abstract calss can also have constructor like regular class.
```
//creating abstract class
abstract class Person(name:String,age:Int){
abstract fun personalDetail()
abstract fun qualification()
}
//implementation of abstract class in employee class
class Employee(val name:String,val age:Int :Person(name,age){
@override
personalDetail(){
 println("Name of employee is:$name")
}

@override
qualification(){
//do something here
}
}
```
# 9. Difference between interface and abstract class.
**Abstract class** <br/>
Ans: if you want a single class that can have both optional and required method to override in a class, you can use Abstract class.
```
fun main() {
    val rect = Rectangle(2,3)
    println("Area: ${rect.computeArea()}")
    println("Perimeter: ${rect.computePerimeter()}")
    rect.defaultColor()
}
abstract class Shape{
    lateinit var color: String

    private val shapeColor: String
        get() = color

    init {
        color = "pink"
    }
    fun defaultColor(){
        println("The shape's default color is $shapeColor.")
    }
    abstract fun side(): Int
    abstract fun computeArea(): Double
    abstract fun computePerimeter(): Double
}
class Rectangle(var l: Int, var w: Int): Shape(){
    override fun side(): Int = 4
    override fun computeArea(): Double = (w*l).toDouble()
    override fun computePerimeter(): Double = (2*(l+w)).toDouble()
}
```
**Interface** <br/>
An Interface is used when you want to achieve 100% abstraction. Because an interface does not accept the construtor,body of functions instead of declaration only, it can not itantiated. The core diff. between abstract and interface class is that an abstract class can have constructors,abstract function as well as no-abstract functions while interface have not.

# 10.What is root class of exception? and diff. between checked and unchecked exception?
Ans:
![png;base64669bf411b9dbea2c](https://github.com/22vikash1995/InterviewPrep/assets/69666373/9e48209c-670a-4649-908b-a073c8bb288a)
``` Throwable ``` is the root class of exceptions.An exception is an unwanted event that disrupts the normal flow of the program. It is an object which is thrown at runtime.**Exception handling** is a technique, using which we can handle errors and prevent run time crashes that can stop our program.<br/>
**There are two types of Exceptions** <br/>
**1.Checked Exception:** - This type of exception is checked at compile time and typically set on methods. For example IOException, FileNotFoundException etc.
**2.UnChecked Exception** – Exceptions that are generally due to logical errors and checked at the run time, for example NullPointerException, ArrayIndexOutOfBoundException etc.<br/>
**Kotlin Exceptions –** <br/>
In Kotlin, we have only unchecked exceptions and can be caught only at run time. All the exception classes are descendants of Throwable class.
We generally use the throw-expression, to throw an exception object –<br/>
``` throw Exception("Throw me") ```.
<br/>
**Kotlin try-catch block –** <br/>
In Kotlin, we use try-catch block for exception handling in the program.<br/>
```
import kotlin.ArithmeticException
fun main(args : Array<String>){
	try{
		var num = 10 / 0
	}
	catch(e: ArithmeticException){
		// caught and handles it
		println("Divide by zero not allowed")
	}
}
```
**Kotlin finally block –** <br/>
In Kotlin, finally block is always executes irrespective of whether an exception is handled or not by the catch block. So it is used to execute important code statement.<br/>
```
fun main(args : Array<String>){
	try{
		var ar = arrayOf(1,2,3,4,5)
		var int = ar[6]
		println(int)
	}
finally {
		println("This block always executes")
	}
}
```
**Kotlin throw keyword –** <br/>
In Kotlin, we use throw keyword to throw an explicit exception. It can also be used to throw a custom exception.<br/>
```
fun main(args: Array<String>) {
	test("abcd")
	println("executes after the validation")
}
fun test(password: String) {
	// calculate length of the entered password and compare
	if (password.length < 6)
		throw ArithmeticException("Password is too short")
	else
		println("Strong password")
}
```

# 11. How can we create custom exception?
# 12. What is OOP?
# 13. What is sealed class why it is used?
# 14.What is Coroutine in kotlin?
Ans: A Coroutine is a framework developed by jetbrain. It is conceptually similar to thread which allow to run a piece of code concurrently with rest of the code. It is not bound to any other thread .It may suspend its execution in one thread and resume another one. 
```
fun main() = runBlocking { // this: CoroutineScope
    launch { // launch a new coroutine and continue
        delay(1000L) // non-blocking delay for 1 second (default time unit is ms)
        println("World!") // print after delay
    }
    println("Hello") // main coroutine continues while a previous one is delayed
}
```
**launch**: it is a coroutine builder that creates new coroutine within coroutinescope.<br/>
**runBlocking**: It is also a coroutine builder but it creates coroutiine scope where coroutine builder (i.e launch) creates coroutines. Outside of coroutiine scope we can not use any coroutine builder like launch. 
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
# Explain all states of fragment
Ans:<br/>
**Case:1 When Fragment launched** <br/>
```
onAttach()
onCreate()
onActivityCreated()
onStart()
onResume()
```
**Case:2 While navigating from FragmentA to FragmentB** <br/>
```
//in fragA
onPause()
onStop()
onDestroyView()//after few milli second

//in FragB
onAttach()
onCreate()
onActivityCreated()
onStart()
onResume()
```
**Case:3 When come back from other applicatcation** 
```
onStart()
onResume()
```
**Case:4 When come back from FragB to FragA**
<br/>
**for FragB**
```
onPause()
onStop()
onDestroyView()
onDestroy()
onDetach()
```
**for FragA**
```
onActivityCreated()
onStart()
onResume()
```
**Case:4 When press back button** <br/>
```onPause()
onStop()
onDestroyView()
onDestroy()
onDetach()
```




