<div align="center">

# 🔍 Java Annotations & Reflection

![Java](https://img.shields.io/badge/Java-11-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-C71A36?style=for-the-badge&logo=apache-maven&logoColor=white)
![JUnit](https://img.shields.io/badge/JUnit-4.13.2-25A162?style=for-the-badge&logo=junit5&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)

**Hands-on implementation of custom Java annotations and runtime reflection**  
Built as part of Module 5 coursework using Apache Maven.

</div>

---

## 📌 About

This project demonstrates two powerful advanced Java features:

- **Custom Annotations** — defining your own annotation types with `@interface`, controlling retention policy and target element
- **Java Reflection API** — inspecting classes, methods, and parameters at runtime to read annotation metadata dynamically

---

## 🗂️ Project Structure

```
Java-Annotations-and-Reflection/
├── pom.xml                          # Maven build config (Java 11, JUnit 4.13.2)
└── src/
    ├── main/java/
    │   └── mod5/annotations/
    │       ├── Para.java            # Custom @Para annotation definition
    │       ├── AnnotatedExample.java # Usage of @Para on method parameters
    │       └── ReflectTest.java     # Runtime reflection to read @Para metadata
    └── test/java/
        └── org/example/
            └── AppTest.java         # Unit tests
```

---

## 🧠 Concepts Covered

| Concept | Details |
|---------|---------|
| **Custom Annotation** | `@interface Para` with `description` element |
| **Retention Policy** | `@Retention(RetentionPolicy.RUNTIME)` — annotation available at runtime |
| **Target** | `@Target(ElementType.PARAMETER)` — applies to method parameters |
| **Reflection API** | `Method`, `Parameter`, `getAnnotation()` to inspect metadata at runtime |
| **Maven Build** | Standard Maven project layout with `pom.xml` |

---

## 🔬 Key Files Explained

### `Para.java` — Custom Annotation
```java
@Target(ElementType.PARAMETER)
@Retention(RetentionPolicy.RUNTIME)
public @interface Para {
    String description();
}
```
Defines a custom annotation that can be applied to method parameters and is retained at runtime for reflection.

### `ReflectTest.java` — Reading Annotations via Reflection
```java
Method method = ReflectTest.class.getMethod("greet", String.class);
Parameter[] parameters = method.getParameters();
Para para = parameter.getAnnotation(Para.class);
System.out.println(para.description());
```
Uses the Reflection API to inspect a method's parameters and read the `@Para` annotation value at runtime.

---

## 🚀 How to Run

**Prerequisites:** Java 11+, Apache Maven 3.6+

```bash
# Clone the repository
git clone https://github.com/chopragauri/Java-Annotations-and-Reflection.git
cd Java-Annotations-and-Reflection

# Build the project
mvn compile

# Run ReflectTest
mvn exec:java -Dexec.mainClass="mod5.annotations.ReflectTest"

# Run tests
mvn test
```

---

## 👩‍💻 Author

**Gauri Chopra**  
[![GitHub](https://img.shields.io/badge/GitHub-chopragauri-181717?style=flat&logo=github)](https://github.com/chopragauri)
