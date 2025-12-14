# taller-final-pila-enlazada
Implementación de una pila utilizando lista enlazada simple en lenguaje C. Taller final de la materia Estructura de Datos, incluye operaciones básicas como push, pop y recorrido de la pila mediante menú interactivo.

#include <stdio.h>
#include <stdlib.h>

#define MAX 100   // tamaño máximo de la pila

// Estructura de la pila
typedef struct {
    int elementos[MAX];
    int tope;
} Pila;

// Función para inicializar la pila
void inicializar(Pila *p) {
    p->tope = -1;
}

// Verificar si la pila está llena
int estaLlena(Pila *p) {
    return p->tope == MAX - 1;
}

// Verificar si la pila está vacía
int estaVacia(Pila *p) {
    return p->tope == -1;
}

// Insertar elemento (PUSH)
void push(Pila *p, int dato) {
    if (estaLlena(p)) {
        printf("Error: La pila esta llena.\n");
        return;
    }
    p->tope++;
    p->elementos[p->tope] = dato;
    printf("Insertado: %d\n", dato);
}

// Eliminar elemento (POP)
int pop(Pila *p) {
    if (estaVacia(p)) {
        printf("Error: La pila esta vacia.\n");
        return -1;
    }
    int dato = p->elementos[p->tope];
    p->tope--;
    printf("Eliminado: %d\n", dato);
    return dato;
}

// Mostrar pila
void mostrar(Pila *p) {
    if (estaVacia(p)) {
        printf("La pila está vacia.\n");
        return;
    }

    printf("Contenido de la pila:\n");
    for (int i = p->tope; i >= 0; i--) {
        printf("%d\n", p->elementos[i]);
    }
}

// Programa principal
int main() {
    Pila p;
    inicializar(&p);

    int opcion, valor;

    do {
        printf("\n--- MENU DE PILA ---\n");
        printf("1. PUSH (insertar)\n");
        printf("2. POP (eliminar)\n");
        printf("3. Mostrar pila\n");
        printf("4. Salir\n");
        printf("Seleccione una opcion: ");
        scanf("%d", &opcion);

        switch(opcion) {
            case 1:
                printf("Ingrese un valor: ");
                scanf("%d", &valor);
                push(&p, valor);
                break;
            case 2:
                pop(&p);
                break;
            case 3:
                mostrar(&p);
                break;
            case 4:
                printf("Saliendo...\n");
                break;
            default:
                printf("Opción no válida.\n");
        }
    } while (opcion != 4);

    return 0;
}
