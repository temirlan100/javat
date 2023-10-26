## Which PC and Operating System to choose for Java programming?
- Q: I want to become a programmer. Should I buy MacBook Pro?
- A: Not really, you can use any PC. But it's recommended to have at least 8GB RAM [see here](https://www.jetbrains.com/help/idea/installation-guide.html#requirements)

- Q: Which OS should I have? Should I install Linux?
- A: Linux is a good choice, and it's very popular, BUT all modern OS (Windows, MacOS, Linux) are also compatible with IntelliJ Idea (program where you will be writing your code).

## Linux operating system
Linux is an open source and freely distributed operating system based on the Unix kernel.
The system is popular in the field of servers, embedded systems and many other areas.

## History and Features of the Java Language
Java is an object-oriented programming language that was developed in the early 1990s at Sun Microsystems. The main features are:
- **Platform Independence**: Programs written in Java can be run on any platform using the Java Virtual Machine (JVM).
- **Security**: Java offers a number of security mechanisms, including bytecode verification.
- **Multithreading**: The language contains inbuilt support for multithreading, allowing efficient use of system resources.

## Installing the JDK (Java Development Kit)
The JDK is a Java development kit that includes everything you need to create and run Java applications.
1. Go to [official Oracle website](https://www.oracle.com/java/technologies/downloads/#java21).
2. Select the **JDK Development Kit 21** version for your operating system and follow the installation instructions.

## Installing the IntelliJ IDEA development environment
IntelliJ IDEA is a popular development environment for Java.
1. Go to [official JetBrains website](https://www.jetbrains.com/toolbox-app/) and download ToolBox.
2. Run the ToolBox application.
3. Select "Community Edition" (free version) and download.
3. Install by following the instructions of the installation wizard.

## "Hello World!" - Your first Java programme
After installing everything you need, let's create your first programme:

1. Start IntelliJ IDEA and create a new project.
2. Select "Java" and click "Next".
3. Give your project a name, for example "HelloWorld".
4. In the editor that opens, enter the following code:

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```
Run the program by clicking on the green triangle next to the main method. 
You should see the "Hello, World!" output in the console.
