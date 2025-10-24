# Ejercicios Guiados
| Actividad | Evidencia | 
| --- | --- |
| U2 ACT1|[U2ACT1 Ejercicio de Lista Enlazada ](https://github.com/1224100829aalp-cpu/U2GB-Ejercicios-Guiados-2/blob/main/U2ACT1%20Ejercicio%20de%20Lista%20Enlazada.pdf)|
## U2ACT1 Actividad  "Ejercicio de Lista Enlazada Simple con visuAlgo."
#### El archivo pdf con la actividad fue incluido en los archivos de este repositorio.

## U2ACT2 Actividad  "Lista Encantada Humana en Java."
#### Evidencia en Imagenes de participacion en la actividad Lista Humana 

| Imagenes de Evidencia        | Cierre Reflexivo de la Actividad |
| ------------- | ------------- |
| <img src="https://github.com/user-attachments/assets/8ad22b95-21ba-46ff-9250-6e4098ac1b5c" alt="Alt Text" width="200" height="200"> | <img src="https://github.com/user-attachments/assets/bc8b5288-ca39-4852-a312-7a60e712d4f4" alt="Alt Text" width="200" height="200"> |
| <img src="https://github.com/user-attachments/assets/6eceea7e-ab34-4d81-a727-c0c9f51e3524" alt="Alt Text" width="200" height="300"> | 

## U2ACT3 Actividad  " Práctica Manual y Algorítmica Lista."
#### El archivo pdf con la actividad fisica (de cada tipo de lista) fue incluido en los archivos de este repositorio
### Evidencia de Pseudocodigo y Reflexion Final
| Pseudocodigos escritos | Reflexion final |
| ------------- |:-------------:| 
| <img src="https://github.com/user-attachments/assets/722e49ef-5277-4845-b2ee-bb32308f149e" alt="Alt Text" width="300" height="300"> |  <img src="https://github.com/user-attachments/assets/fbedb678-495c-4e76-86e9-b9e791d937a1" alt="Alt Text" width="300" height="400"> |
| <img src="https://github.com/user-attachments/assets/23897172-2d0e-4cfa-99d1-fd5b947d4acd" alt="Alt Text" width="300" height="300"> | 
| <img src="https://github.com/user-attachments/assets/a869cfcb-1d57-4a36-ac78-cdd3ed3dc5c2" alt="Alt Text" width="200" height="200"> |
| <img src="https://github.com/user-attachments/assets/4102cc1b-2678-4b78-a6b3-d76e5db9adb7" alt="Alt Text" width="200" height="200"> |
### Codigo en java
##### Nodo Lista Simple
```javascript
package listas;

/**
 *
 * @author angellunaperez
 * En esta clase de java se declara el nodo
 * para la lista simplemenete enlazada
 */
// Clase Nodo para Lista Simple 
public class Nodo<T> {
    public T dato;
    public Nodo<T> siguiente;

    public Nodo(T dato) {
        this.dato = dato;
        this.siguiente = null;
    }
}
```
##### Usos de la Lista Simple
```javascript
package listas;

/**
 *
 * @author angellunaperez
 *  En esta clase se declara los metodos
 * para la lista simplemente enlazada
 * insertar, eliminar y mostrar
 */

public class ListaSimple<T> {
    private Nodo<T> inicio;
    private int tamanio;

    public ListaSimple() {
        this.inicio = null;
        this.tamanio = 0;
    }

    // --- MÉTODOS DE INSERCION ---
    public void insertarAlInicio(T dato) {
        Nodo<T> nuevoNodo = new Nodo<>(dato);
        
        // El siguiente del nuevo nodo es el inicio actual
        nuevoNodo.siguiente = inicio; 
        
        // Actualizar el inicio de la lista
        inicio = nuevoNodo;
        tamanio++;
    }

    // --- MÉTODOS DE ELIMINACIÓN ---
    public T eliminarAlInicio() {
        if (inicio == null) {
            System.out.println("La lista está vacía.");
            return null; // O lanzar una excepción
        }
        
        T datoEliminado = inicio.dato;
        
        // Mover el inicio al siguiente nodo
        inicio = inicio.siguiente; 
        tamanio--;
        
        return datoEliminado;
    }

}
```
##### Nodo Lista Doble
 ```javascript
package listas;
//@author: ANGEL ALFREDO LUNA PEREZ
//En esta clase se declara el nodo
//para la lista doble.
public class Nodo<T> {
    private T dato;
    private Nodo<T> siguiente;
    private Nodo<T> anterior;

    public Nodo(T dato) {
        this.dato = dato;
        this.siguiente = null; 
        this.anterior = null; 
    }

    public T getDato() {
        return dato;
    }

    public void setDato(T dato) {
        this.dato = dato;
    }

    public Nodo<T> getSiguiente() {
        return siguiente;
    }

    public void setSiguiente(Nodo<T> siguiente) {
        this.siguiente = siguiente;
    }

    public Nodo<T> getAnterior() {
        return anterior;
    }

    public void setAnterior(Nodo<T> anterior) {
        this.anterior = anterior;
    }
}

```
##### Usos de la lista doble 
```javascript

package listas;

/**
 *
 * @author angellunaperez
 * En esta clase se declara los metodos
 * para la lista doblemente enlazada
 * insertar, eliminar y mostrar
 */
    public class ListaDoble<T> {
    private NodoDoble<T> inicio;
    private NodoDoble<T> fin; // Útil para la lista doble
    private int tamaño;

    public ListaDoble() {
        this.inicio = null;
        this.fin = null;
        this.tamaño = 0;
    }

    // --- MÉTODOS DE INSERCIÓN  ---
    public void insertarAlInicio(T dato) {
        NodoDoble<T> nuevoNodo = new NodoDoble<>(dato);
        
        if (inicio == null) { // Si la lista está vacía
            inicio = nuevoNodo;
            fin = nuevoNodo;
        } else {
            nuevoNodo.siguiente = inicio; // El nuevo nodo apunta al inicio actual
            inicio.anterior = nuevoNodo;  // El inicio actual apunta al nuevo nodo como anterior
            inicio = nuevoNodo;           // El nuevo nodo es el nuevo inicio
        }
        tamaño++;
    }

    // --- MÉTODOS DE ELIMINACIÓN  ---
    public boolean eliminarPorValor(T dato) {
        NodoDoble<T> actual = inicio;
        
        while (actual != null && !actual.dato.equals(dato)) {
            actual = actual.siguiente;
        }

        if (actual == null) { // El nodo no se encontró
            return false;
        }

        // Caso 1: El nodo a eliminar es el 'inicio'
        if (actual == inicio) {
            inicio = actual.siguiente;
            if (inicio != null) {
                inicio.anterior = null;
            } else { // Si la lista queda vacía
                fin = null;
            }
        } 
        // Caso 2: El nodo a eliminar es el 'fin'
        else if (actual == fin) {
            fin = actual.anterior;
            fin.siguiente = null;
        } 
        // Caso 3: El nodo a eliminar está en medio
        else {
            actual.anterior.siguiente = actual.siguiente; // El anterior salta el 'actual'
            actual.siguiente.anterior = actual.anterior; // El siguiente salta el 'actual'
        }
        
        tamaño--;
        return true;
    }

}

```
##### Nodo y usos de la lista circular (se reuso el nodo de la simple) 
```javascript

package listas;

/**
 *
 * @author angellunaperez
 * En esta clase se declara los metodos y usos
 * para la lista doblemente enlazada
 * insertar, eliminar y mostrar
 * reutilize la clase Nodo <T> de la Lista Simple
 */

public class ListaCircularSimple<T> {
    private Nodo<T> ultimo; // Puntero al último nodo
    private int tamanio;

    public ListaCircularSimple() {
        this.ultimo = null;
        this.tamanio = 0;
    }

    // --- MÉTODOS DE INSERCION ---
    public void agregarAlFinal(T dato) {
        Nodo<T> nuevoNodo = new Nodo<>(dato);
        
        if (ultimo == null) { // Si la lista esta vacia
            ultimo = nuevoNodo;
            nuevoNodo.siguiente = ultimo; // Se apunta a si mismo
        } else {
            nuevoNodo.siguiente = ultimo.siguiente; // El nuevo nodo apunta al inicio (ultimo.siguiente)
            ultimo.siguiente = nuevoNodo;           // El ultimo nodo actual apunta al nuevo
            ultimo = nuevoNodo;                     // El nuevo nodo es el nuevo último
        }
        tamanio++;
    }

    // --- MÉTODOS DE ELIMINACIÓN---
    public T eliminarAlInicio() {
        if (ultimo == null) {
            System.out.println("La lista está vacía.");
            return null;
        }

        Nodo<T> inicioActual = ultimo.siguiente;
        T datoEliminado = inicioActual.dato;
        
        if (inicioActual == ultimo) { // Si solo hay un nodo
            ultimo = null;
        } else {
            // El 'ultimo' apunta al siguiente del nodo a eliminar
            ultimo.siguiente = inicioActual.siguiente;
        }
        tamanio--;
        return datoEliminado;
    }

}
```
## U2ACT4 Ejercicio de Pila con VisuAlgo
### El archivo pfd con la evidencia de la actividad fue incluido en este repositorio.
### Codigo en java
#### Interfaz de la pila
```javascript
package Stack;

/**
 *
 * @author angellunaperez
 * Una pila (stack) es una colección ordenada de
 *elementos a los que sólo se puede acceder por un
 *único lugar o extremo de la pila. Los elementos de la
 *pila se añaden o quitan (borran) sólo por su parte
 *superior (cima o tope) de la pila.
 */
public interface Pila<T> {
    void push(T elemento);
    T pop ();
    T peek();
    boolean estaVacia();
}
```
#### Metodos de la pila
```javascript
package Stack;

/**
 *
 * @author angellunaperez
 */
public class StackArrays<T> implements Pila <T> {
    private T[] elements;
    private int top;
    
    public StackArrays(){
        elements =   (T[])new Object[30];
    }
    
      public StackArrays(int size ){
        elements = (T[])new Object[size];
    }

@Override
    public void push(T elemento) {
    if (top < elements.length - 1) {
        for (int i = top; i >= 0; i--) {
            elements[i + 1] = elements[i];
        }
        elements[0] = elemento;
        top++;

    } else {
        System.out.println("Esta llena");
    }

    }

    @Override
   public T pop() {
    if (top < 0) { 
        System.out.println("La pila está vacía, no se puede extraer ningún elemento.");
        return null;
    } else {
        T elementoQuitado = elements[top]; 
        top--; 

        return elementoQuitado;
    }


    }


    @Override
    public T peek() {
        if (estaVacia()) {
        System.out.println("Pila Vacía");
        }
        System.out.println("Conociendo el último de la pila");
       return (T) elements[top];

    }

    @Override
    public boolean estaVacia() {
        return top ==0;
    }
  
    

}
```
#### Clase Main
```javascript
package Stack;

/**
 *
 * @author angellunaperez
 */
public class Main {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        StackArrays<String> animales = new StackArrays<String>();
        animales.push("Gato");
        animales.push ("Perro");
        animales.push("Leon");
        
        System.out.println(animales.pop());
        System.out.println(animales.pop());
        System.out.println(animales.pop());
    }
    
}
```

### Reflexion Final
<img src="https://github.com/user-attachments/assets/cfccbfbc-b14a-4aa5-88fd-6f11e9dc9a6b" alt="Alt Text" width="200" height="200"> 

## Actividad Nearpod de pilas 
### El archivo pdf con la evidencia fue adjuntado en este github.

## Actividad Nearpod de Colas
### El archivo pdf con la evidencia de las respuestas fue adjuntado en este github.
### Codigo creado durante la actividad



