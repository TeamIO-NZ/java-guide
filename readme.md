# Ultimate Java Guide. 
## Created by Joe and James

## Contents
* [Basics](#Basics)
    * [Naming](#Naming)
    * [Types](#Types)
    * [Brackets](#Brackets)
    * [Comments](#Comments)
* [Classes](#Classes)
    * [Packages](#Packages)
    * [Imports](#Imports)
    * [Defining a Class](#Defining-a-Class)
    * [Hierarchy (`extends`, `implements`, `super`)](#Hierarchy)
    * [Variables](#Variables)
    * [Constructors](#Constructors)
    * [Methods](#Methods)
* [Application](#Application)
    * [The Main Method](#The-Main-Method)
    * [Exceptions](#Exceptions)
    * [Loose Coupling](#Loose-Coupling)
* [Advanced Java](#Advanced-Java)
    * [Interfaces](#Interfaces)
    * [Annotations](#Annotations)
    * [Inheritance](#Inheritance)
    * [Polymorphism](#Polymorphism) 
    * [Encapsulation](#Encapsulation) 
    * [Abstraction](#Abstraction)
    * [Casting](#Casting)
    * [Dependency Management](#Dependency-Management)
* [Documentation](#Documentation)
    * [Generating Javadocs](#Generating-Javadocs)
    * [Reading UML](#Reading-UML)
        * [Symbols](#Symbols)
        * [Understanding UML](#Understanding-UML)
    * [Version Control (VCS)](#Version-Control-(VCS))
* [Credits](#Credits)

### Basics
Here we cover the basics of Java and try to explain everything as if the reader was completly new to the language.

#### Naming
Java uses `camalCase` for everything but classes, which use `PascalCase`. There are two exceptions to this: the first is static final variables which use `FULL_CAPS` and the other is package names which should be all `lower.case` and preferably one word. Interfaces should be prefixed with a captial i (`I`).
> Note: Spelling should be accurate so other developers can understand your code.


Example Code:
```java
package core.example;

public class PascalCase {
    static final String FULL_CAPS = "underscores between words";
    void camalCase() {
        int alsoCamalCase = 0;
    }
}
```

### Classes


```java
package i;
import t;
public class MyClass extends A implements B, C {
    int val;
    MyClass() {
        this(0)
    }
    MyClass(int i) {
        val = i;
    }
    void method() {}
    int returnMethod() {}

    @Override
    void overriddenMethod() {}
}
```

### Application



### Advanced Java


### Documentation
Documentation is an important aspect of any programming project and Java has a standardised way of creating it.

#### Generating Javadocs
Javadocs are generated by a build system like *Gradle* or *Maven* but the way they're defined is what we're going to focus on. Javadocs use a slightly altered version of the comment specification and can be placed on the line above any defintion.

Javadoc definitions always start with a forward slash folowed by two asterisk as the top line `/**`, then each line after starts with an indented asterisk ` * ` and ending with a asterisk and a forward slash `*/`.

Javadoc uses `@tags` to define special arguments in a Javadoc with some commonly used tags being the following:
* `@param arg Description` - Used to describe a method augment.
* `@returns Description` - Describes what is returned from a method.
* `@author name` - Marks the author of the following code.
* `@see package.Class#field` - Used to link to another piece of code.
* `{@link package.Class#field}` - Used to link to another peice of code inline.
* `@deprecated` - Shows the code as deprecated.

Example:

```java
package example.documentation;

/**
 * Example used to demonstrate defining Javadocs.
 *
 * @author me
 */
public class GeneratingJavadocs {
    
    /**
     * Demo method {@link GeneratingJavadocs}
     * 
     * @deprecated
     * @see GeneratingJavadocs
     * @param arg Demo arg 1
     * @param arg2 Demo arg 2
     * @return Always 0
     */
    @Deprecated
    public int demoMethod(int arg, String arg2) {
        return 0;
    }
}
```

For the full Javadoc documentation click [here](https://www.oracle.com/technetwork/java/javase/documentation/index-137868.html).

#### Reading UML
Reading UML isn't some kind of art. Its a basic set of principals and logic thinking that is easy to understand with a small amount of practice.

##### Symbols
![](https://media.discordapp.net/attachments/631649380536942592/702856640323518474/unknown.png?width=729&height=414)

* `Black Triangle` points at the class that contains an array of this item
* `White Arrow` points at the root class
* `Square with folded corner` is a Comment
* `White Circle next to name` is an Interface. 

* `-` private variable or method
* `+` public variable or method

#### Understanding UML
So where to start? First we identify the root or abstract classes. These are usually the classes with white arrows pointing to them. In the example above, start with Planet and Spacecraft. Outline these classes by putting in their variables and methods. 
```java
public abstract class Planet
{
    // - symbol equals private
    private String name; 
    // + symbol equals public
    public abstract String getName(); 
    public abstract void setName(String name);
    
}
```
In this example we'll see that we have an abstract class as the root with variables and some functions (in this case getters and setters) that all planets will have. From here we can start to flesh out the planets.
```java
public class RockyPlanet extends Planet
/* 
 * Note that this extends the planet class which will mean it has a name and the 
 * getters and setters for name even though they aren't written here
 */
{
    private Set<ILandingCapable> landedSpaceCraft = new HashSet<>() //A set to store our collection of landed spacecraft
    
    public void hostSpaceCraft(LandingCapable landingCapableVehicle){
        
    }
    public void unhost(String uId){
        
    }
    public getOccupiedBays(){
        
    }
}
```
This is a basic version of out first planet class. As you can see we havn't implemented anything yet other than intialising what's on the UML document. For now this is all we will do with this class. From here we move on to doing the basics for all the classes that extend from these root classes. After that only 3 classes remain. 

SolarSystem which is just a class object that contains a set of some kind to put our planets in.

LandingCapable which we can name ILandingCapable to fit with the java naming convention

And our class with the main method in it.

Once this is done we are ready to work. WE can start to fill in what's missing in each class by writing the methods and with that you should be a little bit less confused about how to read a UML diagram.

#### Version Control (VCS)
All code should at all times be utilising some form of version control. The best and most widely uses version control system is Git. Setting up git and github is easy to learn and will make your life and the lives of anyone your working with much easier. Version control will enable things like easy code sharing, being able to revert changes when someone envitably breaks things and being able to review code before its merged into the production app. But the main reason to start using it, is that it will stop you from losing valuable code. 

* For a better tutorial on how to use github go [here](https://product.hubspot.com/blog/git-and-github-tutorial-for-beginners) or go to [Github](https://www.github.com)

### Credits
* us
    * we
        * not them
            * Also Lithial is the best
               * and joe

### TODO
- Check to make sure we follow our own naming conventions.
- Check to make sure our code is actually real code
- Testing as a catagory

