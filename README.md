# INTERVIEW QUESTIONS
# -------Kotlin-------
# 1. What is Inline function in kotlin?
Ans: Inline function is a function followed by 'inline' keyword. When we use inline keyword before a function name ,the compiler does not allocate the memory.Wherever this function is invoked the piece of code is copied at calling place.
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
Set is also used to create list of items but difference is that it drops the duplicate item from the list and its item can not retrive by index like list.In this all items are stored ramdomly(i.e not in a particular order)<br/>
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







