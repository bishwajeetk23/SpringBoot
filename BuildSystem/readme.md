# 📌 javac Essentials — Quick Reference

`javac` is the Java Compiler. It compiles `.java` source files into `.class` bytecode files that the JVM can execute.

---

## 1️⃣ Basic Usage
```bash
javac MyClass.java
Produces MyClass.class in the same directory by default.

2️⃣ Compilation Scope
Compiling Main.java also compiles referenced .java files automatically.

Unused/unreferenced files are ignored unless compiled explicitly.

Compile all files in a folder:

bash
Copy
Edit
javac *.java
3️⃣ Packages & Directory Structure
Package name must match folder structure relative to the compilation start point.

Example:

java
Copy
Edit
package my.app.utils;
should be located at:

bash
Copy
Edit
my/app/utils/ClassName.java
If mismatch → compilation error.

4️⃣ Classpath (-cp)
By default, javac searches the current directory.

Extend search path:

bash
Copy
Edit
javac -cp /path/to/classes MyClass.java
Multiple paths:

Linux/Mac: :

Windows: ;

5️⃣ Output Directory (-d)
Specify where .class files should go:

bash
Copy
Edit
javac -d out MyClass.java
This creates the package folder structure inside out/.

6️⃣ Common Flags
-verbose → Show compilation details.

-source <version> → Set source compatibility.

-target <version> → Set bytecode version.

-parameters → Keep method parameter names for reflection.

-Xlint → Enable detailed warnings.

7️⃣ Errors & Warnings
javac stops on the first compilation error.

Use:

bash
Copy
Edit
javac -Xlint:unchecked MyClass.java
for extra warnings.

8️⃣ Relationship to java
javac → Compiles .java → Produces .class

java → Runs .class files.

9️⃣ Tips
Compile from the directory above your package root.

Use javac *.java during development to catch unused classes with errors.

For bigger projects, use Maven or Gradle to handle classpaths and dependencies automatically.

✅ Rule of Thumb:
Package name = folder path (relative to compile starting point)
Mismatch = Compilation error.
