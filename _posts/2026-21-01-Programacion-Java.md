---
title: Python | Programacion
description: Cosas basicas para aprender a programar python
date: 2026-01-17 10:00:0 +0000
categories: [Programming, Python]
tags: [Python, Programming]
pin: false
mermaid: true
---
# Apuntes de Programación en Python

## Versiones de Python

### ¿Qué es Python?
Python es un **lenguaje de programación interpretado**, de **alto nivel** y **propósito general**, diseñado para ser fácil de leer y escribir.

- **Interpretado**: no necesita compilarse antes de ejecutarse.
- **Alto nivel**: se parece al lenguaje humano.

### Python 2 vs Python 3

- **Python 2**: Usaba principalmente **ASCII** para texto. Ya está **obsoleto**.
- **Python 3**: Usa **Unicode** por defecto, lo que permite manejar tildes, emojis y otros idiomas.

📌 **Siempre usa Python 3**.

---

## PIP – Gestor de paquetes

### ¿Qué es PIP?
PIP es el **gestor de paquetes oficial de Python**. Sirve para instalar, actualizar y eliminar librerías externas.

- Un **paquete** es una librería que añade funcionalidades.
- Ejemplo: pwntools, requests, flask.

### Instalación de pip en Linux

```python
apt install python3-pip
```

### Uso básico

```python
pip3 install pwntools
```

📌 `pip2` corresponde a Python 2 y **ya no se recomienda**.

---

## El intérprete de Python

### ¿Qué es el intérprete?
El intérprete de Python es el **programa que lee y ejecuta código Python línea por línea**.

### ¿Para qué se usa?

- Probar código rápidamente
- Aprender Python de forma interactiva
- Probar librerías

### Ejemplo

```python
python3 -c "print('Hola mundo')"
```

### Conceptos internos importantes

- **Bytecode**: versión intermedia del código Python.
- **PVM (Python Virtual Machine)**: ejecuta el bytecode.

📌 Esto permite que Python sea **portable**.

---

## Shebang y ejecución de scripts

El **shebang** indica qué intérprete usar al ejecutar un script.

```python
#!/usr/bin/env python3
```

📌 Usa `env` para buscar Python según el `PATH` del sistema.

### Ejemplo de búsqueda

```shell
which whoami
/usr/bin/whoami
```

Sin shebang, el script solo se ejecuta con:

```shell
python3 script.py
```

---

## if __name__ == "__main__"

### ¿Qué significa?
Esta línea verifica **cómo se está usando el archivo**.

Python asigna automáticamente el valor:
- `"__main__"` → cuando el archivo se ejecuta directamente
- nombre del archivo → cuando se importa

### ¿Para qué sirve?
Evita que cierto código se ejecute cuando el archivo se importa como módulo.

### Ejemplo

```python
def saludo():
    print("Hola de nuevo")

if __name__ == "__main__":
    saludo()
```

📌 Es clave para crear scripts reutilizables.

---

## Convenciones de Python

### Nombres

- **snake_case** → funciones y variables
- **CamelCase** → clases
- **SCREAMING_SNAKE_CASE** → constantes

```python
VERSION_API = 1
URL_API = "https://yishaq21.github.io"
```

📌 Sigue la guía **PEP 8**.

### Variables protegidas y privadas

```python
_protegido = "Uso interno"
__privado = "No tocar"
```

---

## Variables y tipos de datos

### ¿Qué es una variable?
Una variable es un **nombre que apunta a un valor**. Sirve para guardar información y reutilizarla en el programa.

📌 Python no requiere declarar el tipo, él lo infiere automáticamente.

---

### Strings (Cadenas)

#### ¿Qué es un String?
Un string es una **secuencia de caracteres** usada para representar texto.

- Son **inmutables** (no se pueden modificar carácter por carácter).

```python
cadena = "mi cadena"
print(type(cadena))
```

---

### Números

#### Enteros (int)
Números sin decimales.

```python
port = 80
```

#### Flotantes (float)
Números con decimales.

```python
number = 4.5
```

---

### Type Casting (Conversión de tipos)

#### ¿Qué es Type Casting?
Es el proceso de **convertir un dato de un tipo a otro**.

Se usa cuando necesitamos que un valor tenga un tipo específico.

```python
number = float(4)
text = str(123)
```

---

## Listas

### ¿Qué es una lista?
Una lista es una **estructura de datos** que permite almacenar **múltiples valores** en una sola variable.

- Son **ordenadas**
- Son **mutables** (se pueden modificar)
- Permiten valores repetidos

### Ejemplo básico

```python
my_ports = [22, 80, 443]
```

### Recorrer una lista

```python
for port in my_ports:
    print(port)
```

### Operaciones comunes

```python
my_ports.append(8080)
my_ports.extend([8443, 9000])
my_ports.sort()
my_ports.pop()
```

📌 `set(lista)` elimina duplicados.

---

## Operadores básicos

### ¿Qué son los operadores?
Los operadores permiten **realizar operaciones** entre valores.

### Operadores aritméticos

- `+` Suma o concatenación
- `-` Resta
- `*` Multiplicación o repetición
- `/` División
- `**` Potencia

```python
result = 124 * 58
print(round(result, 2))
```

---

## Formateo de Strings

### ¿Qué es formatear un string?
Formatear significa **insertar variables dentro de texto** de forma controlada.

### f-strings (recomendado)

```python
name = "Isaac"
edad = 27
print(f"Hola soy {name} y tengo {edad} años")
```

### format()

```python
print("Hola soy {}".format(name))
```

### % (forma antigua)

```python
print("Hola soy %s" % name)
```

---

## Control de flujo

### For

```python
for i in range(5):
    print(i)
```

### While

```python
i = 0
while i < 5:
    print(i)
    i += 1
```

### Condicionales

```python
if edad >= 18:
    print("Adulto")
else:
    print("Menor")
```

---

## Funciones

`¿Qué es una función?`

Una función es un bloque de código reutilizable que se usa para realizar una tarea específica.
En palabras simples:
    Una función es una forma de guardar instrucciones para poder usarlas cuantas veces quieras.

¿Para qué sirven las funciones?

Las funciones sirven para:

- Evitar repetir código
- Organizar mejor el programa
- Hacer el código más legible
- Facilitar mantenimiento y pruebas

En Python, las funciones se definen con la palabra clave `def`.

```python
def suma(x, y):
    return x + y
```

### Ámbito
¿Qué es el ámbito?

El ámbito (scope) es el lugar del programa donde una variable existe y puede usarse.
Dicho simple:
    El ámbito define desde dónde una variable puede ser vista y utilizada.

#### Tipos de ámbito en Python
- Variables global

**¿Qué es una variable global?**

Una variable global es aquella que se define fuera de funciones.
Puede usarse en todo el archivo
Existe durante toda la ejecución del programa

Ejemplo
```python
mensaje = "Soy global"

def mostrar():
    print(mensaje)

mostrar()
```
La función puede leer la variable global sin problema.

- Variables globales

**¿Qué es una variable globla?**

Una variable local se define dentro de una función.
Solo existe dentro de esa función
Fuera de ella no se puede usar

Ejemplo
```python
def mi_funcion():
    texto = "Soy local"
    print(texto)

mi_funcion()
print(texto)  # ❌ Error
```
texto no existe fuera de la función.

---

## Funciones lambda
¿Qué es una función lambda?

Una función lambda es una función pequeña y sin nombre que se escribe en una sola línea.

Se usa cuando:
- La función es muy simple
- No vale la pena crear una función completa con def
- Se necesita una función rápida y temporal

```python
cuadrado = lambda x: x**2
```

```python
cuadrados = list(map(lambda x: x**2, [1, 2, 3]))
```

---

## Manejo de errores y excepciones

### ¿Qué es un error?
Un error ocurre cuando Python **no puede ejecutar una instrucción**.

### ¿Qué es una excepción?
Una excepción es un **error controlable** que puede manejarse para evitar que el programa se caiga.

### Ejemplo básico

```python
try:
    num = 5 / 0
except ZeroDivisionError:
    print("No se puede dividir entre 0")
finally:
    print("Siempre se ejecuta")
```

### raise

Se usa para **forzar un error manualmente**.

```python
x = -5
if x < 0:
    raise Exception("No se permiten números negativos")
```



