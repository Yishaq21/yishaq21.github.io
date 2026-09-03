---
title: Java | Programacion
description: Cosas basicas para aprender a programar en Java y cosas de POO
date: 2026-01-21 10:00:0 +0000
categories: [Programming, Java, POO]
tags: [Java, Programming, POO]
pin: false
mermaid: true
---
## Versiones de Java

### ¿Qué es Java?
Java es un **lenguaje de programación compilado**, de **alto nivel** y **propósito general**, orientado a objetos.

- **Compilado**: el código se transforma a *bytecode* antes de ejecutarse.
- **Portátil**: funciona bajo el principio *"Write Once, Run Anywhere"*.

---

## JVM, JDK y JRE

### JVM (Java Virtual Machine)
Es la **máquina virtual** que ejecuta el bytecode de Java.

### JDK (Java Development Kit)
Conjunto de herramientas para **desarrollar** en Java (incluye compilador).

### JRE (Java Runtime Environment)
Entorno necesario para **ejecutar** programas Java.

📌 Para programar necesitas el **JDK**.

---

## Compilación y ejecución

```java
javac Main.java
java Main
```

- `javac` → compila el código
- `java` → ejecuta el programa

---

## Clase principal y método main

### ¿Qué es `main`?
Es el **punto de entrada** de todo programa en Java.

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hola mundo");
    }
}
```

📌 Sin `main`, el programa no puede iniciar.

---

## Convenciones en Java

- **camelCase** → variables y métodos
- **PascalCase** → clases
- **MAYUSCULAS_CON_GUIONES** → constantes

```java
public static final int VERSION_API = 1;
```

---

## Variables y tipos de datos

### ¿Qué es una variable?
Una variable es un **espacio en memoria** que almacena un valor.

En Java **sí se debe declarar el tipo**.

```java
int port = 80;
String texto = "Hola";
```

---

### Tipos de datos básicos

- `int` → enteros
- `double` → decimales
- `boolean` → verdadero / falso
- `char` → carácter
- `String` → texto

---

### Type Casting (Conversión de tipos)

#### ¿Qué es Type Casting?
Es convertir un tipo de dato en otro.

```java
int numero = 5;
double decimal = (double) numero;
```

```java
String texto = String.valueOf(numero);
```

---

## Listas (ArrayList)

### ¿Qué es una lista?
Es una estructura que permite almacenar **múltiples valores** dinámicamente.

```java
import java.util.ArrayList;

ArrayList<Integer> puertos = new ArrayList<>();
puertos.add(22);
puertos.add(80);
```

### Recorrer una lista

```java
for (int puerto : puertos) {
    System.out.println(puerto);
}
```

---

## Operadores básicos

### Operadores aritméticos

- `+` suma
- `-` resta
- `*` multiplicación
- `/` división
- `%` módulo

```java
int resultado = 10 * 5;
```

---

## Formateo de Strings

### ¿Qué es formatear?
Insertar variables dentro de texto.

```java
String nombre = "Isaac";
int edad = 27;

System.out.println(String.format("Hola soy %s y tengo %d años", nombre, edad));
```

---

## Control de flujo

### If / Else

```java
if (edad >= 18) {
    System.out.println("Adulto");
} else {
    System.out.println("Menor");
}
```

### For

```java
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}
```

### While

```java
int i = 0;
while (i < 5) {
    i++;
}
```

---

## Funciones (Métodos)

### ¿Qué es un método?
Un método es un **bloque de código reutilizable** que pertenece a una clase.

```java
public static int suma(int a, int b) {
    return a + b;
}
```

---

## Ámbito (Scope)

### ¿Qué es el ámbito?
Define **dónde existe una variable** y dónde puede usarse.

### Variable local

```java
public static void metodo() {
    int x = 10;
}
```

### Variable global (atributo de clase)

```java
static int contador = 0;
```

---

## Funciones lambda (Java)

### ¿Qué es una lambda?
Es una **función anónima** usada principalmente con interfaces funcionales.

```java
(x) -> x * 2
```

Ejemplo con listas:

```java
puertos.forEach(p -> System.out.println(p));
```

---

## Manejo de errores y excepciones

### ¿Qué es una excepción?
Es un error que puede ser **controlado**.

```java
try {
    int x = 5 / 0;
} catch (ArithmeticException e) {
    System.out.println("No se puede dividir entre 0");
} finally {
    System.out.println("Siempre se ejecuta");
}
```

### Lanzar excepciones

```java
if (x < 0) {
    throw new IllegalArgumentException("Número negativo");
}
```
