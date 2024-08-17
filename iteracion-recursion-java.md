# Iteración es el proceso de repetir una secuencia de instrucciones hasta que se cumpla una condición.
=> for, while, do while

## Contextos comunes:
Recorrer colecciones: Listas, conjuntos, mapas.
Procesar datos de archivos: Leer líneas de un archivo, procesar registros.
Realizar cálculos repetitivos: Sumas, promedios, búsqueda de elementos.

Ejemplo clásico de iteración usando un bucle for:

```java
public class IterationExample {
    public static void main(String[] args) {
        int[] numbers = {1, 2, 3, 4, 5};
        int sum = 0;
        
        for (int number : numbers) {
            sum += number;
        }
        
        System.out.println("La suma es: " + sum);
    }
}
```

```java
List<String> nombres = Arrays.asList("Ana", "Pedro", "María");
for (String nombre : nombres) {
    System.out.println(nombre);
}
```


```java
public class StreamIterationExample {
    public static void main(String[] args) {
        int[] numbers = {1, 2, 3, 4, 5};
        
        int sum = Arrays.stream(numbers)
                        .sum();
        
        System.out.println("La suma es: " + sum);
    }
}
```

```java
List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5);
int suma = numeros.stream()
                 .map(n -> n * 2)
                 .reduce(0, Integer::sum);
```


# Recursión es una técnica donde una función se llama a sí misma para resolver un problema. 
Es útil cuando un problema puede dividirse en subproblemas más pequeños de la misma naturaleza. Sin embargo, es importante manejar los casos base para evitar bucles infinitos y desbordamientos de pila. 

Ejemplo clásico de recursión: cálculo del factorial de un número:

Definicion de factorial (google[factorial.mx]): La función factorial es una fórmula matemática representada por el signo de exclamación “!”. En la fórmula Factorial se deben multiplicar todos los números enteros y positivos que hay entre el número que aparece en la fórmula y el número 1.

```java
public class RecursionExample {
    public static void main(String[] args) {
        int number = 5;
        int factorial = factorial(number)
        
        System.out.println("El factorial de " + number + " es: " + factorial);
    }

    public static int factorial(int n) {
        if (n == 0) {
            return 1; // Caso base
        }
        return n * factorial(n - 1); // Llamada recursiva
    }
}
```

# EJERCICIOS PARA PRACTICAR:
Enunciado: Dado un arreglo de números enteros, implementa dos métodos en Java que calculen la suma de sus elementos:


## Usando Iteración: 
- Utiliza un bucle (for, while, o do-while) para iterar sobre los elementos del arreglo y calcular su suma.
```java
int[] numeros = {1, 2, 4, 5, 6, 11, 22, 14}
int resultado = 0;

for (int n : numeros){
    resultado +=n;
}

return resultado;
```

- Dado un arreglo de números enteros, encontrar el número más grande.
```java
int[] numeros = {1, 2, 4, 5, 6, 11, 22, 14, 0, 100}
int resultado = 0;

for (int n: numeros){
    if (n > resultado){
        resultado = n;
    }
}

return resultado;
```

- Implementar una función que calcule la suma de los elementos de una lista enlazada.
```java
class Nodo{
    int valor;
    Nodo enlace;

    Nodo(int valor){
        valor = valor;
        enlace = null;
    }
}

class ListaEnlazada{
    Nodo primerNodo;

    public void insertar(int valor){
        Nodo nuevoNodo = new Nodo(valor);

        if (primerNodo == null){
            primerNodo == nuevoNodo
        }
        else{
            Nodo add = primerNodo;
            while (add.enlace != null){
                add = add.enlace;
            }
            add.enlace = nuevoNodo;
        }
    }

    public int sumar(){
        int suma = 0;

        Nodo nodo = primerNodo;
        while (nodo != null){
            suma += nodo.valor;
            nodo = nodo.enlace
        }
        
        return suma;
    }
}

public class Main{
    public static void main(String[] args){
        ListaEnlazada lista = new ListaEnlazada();

        lista.insertar(3);
        lista.insertar(10);
        lista.insertar(20);

        int suma = lista.sumar();

        return suma;
    }
}
```

- Leer un archivo de texto y contar la cantidad de palabras que comienzan con una vocal.
```java
String texto = "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
String[] textoSplit = texto.split(" ");
int palabrasQueEmpiezanConVocal = 0;


for (String palabra : textoSplit){
    String primeraLetra = palabra.substring(0,1).toLowerCase();

    if (primeraLetra.equals("a") || 
        primeraLetra.equals("e") || 
        primeraLetra.equals("i") || 
        primeraLetra.equals("o") || 
        primeraLetra.equals("u") ){
            palabrasQueEmpiezanConVocal++;
    }
}

return palabrasQueEmpiezanConVocal
```


## Usando Recursión: 
- Implementa una función recursiva que recorra el arreglo y retorne la suma de sus elementos.
```java
int[] arreglo = {20, 40, 60, 80, 100, 120, 140, 160};

public int sumRecursiva(int[] arreglo, int indice){
    if (indice >= arreglo.length){
        return 0;
    }

    return arreglo[indice] + sumRecursiva(arreglo, indice + 1);
}

int resultado = sumRecursiva(arreglo, 0);

return resultado;
```


- Calcular el enésimo número de Fibonacci.

*En matemática, la sucesión de Fibonacci se trata de una serie infinita de números naturales que empieza con un 0 y un 1 y continúa añadiendo números que son la suma de los dos anteriores: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34*
 
```java
public int fibonacci(int numero){
    if (numero <= 0){
        return 0;
    }
    else if (numero == 1){
        return 1;
    }
    else{
        return (fibonacci(numero-1) + fibonacci(numero-2));
    }
}

return fibonacci(10);
```

- Implementar la búsqueda binaria para encontrar un elemento en un arreglo ordenado.
```java
public int busqueda(int[] arreglo, int buscar, int inicio, int fin){
    if (inicio > fin){
        return -1;
    }
    else{
        int medio = (inicio + fin) / 2 

        if (arreglo[medio] == buscar){
            return medio;
        }
        else if (arreglo[medio] < objetivo){
            return buscar(arreglo, objetivo, medio+1, fin);
        }
        else{
            return buscar(arreglo, objetivo, inicio, medio-1);
        }
    }
}
int[] arreglo = {1, 3, 5, 7, 9, 11, 13, 15, 17, 19};
int buscar = 17;
int resultado = busqueda(arreglo, buscar, 0, arreglo.length-1)
```

- Generar todas las posibles permutaciones de una cadena de caracteres.
Definición: [An Internal Link](/permutacion.md)




# Enunciado desafiante:
- Implementar un algoritmo que, dada una matriz de enteros, encuentre el camino más largo desde la esquina superior izquierda hasta la esquina inferior derecha, moviéndose solo hacia abajo o hacia la derecha. Cada celda de la matriz representa un peso, y el objetivo es maximizar la suma de los pesos del camino.