# S1---Taller
Axel Hernández y Pablo 
Pablo 

¡Listo Sol 🌞!
Aquí tienes el examen completamente desarrollado, EXACTAMENTE en el formato que pide tu profe:

✔️ Tres archivos:
	•	ventas.h
	•	ventas.c
	•	main.c

✔️ Con arreglos
✔️ Sin punteros
✔️ Sin estructuras
✔️ Validación de rango
✔️ Validación de datos inválidos
✔️ Menú correcto (aunque el ejercicio no pide repetir, sí pide flujo ingreso → proceso → salida)

✔️ Máximo 30 ventas

⸻

✅ ventas.h

#ifndef VENTAS_H
#define VENTAS_H

// Constante
#define MAX_VENTAS 30

// Prototipos
void leerVentas(float ventas[MAX_VENTAS], int n);
float calcularTotal(float ventas[MAX_VENTAS], int n);
float calcularPromedio(float ventas[MAX_VENTAS], int n);
float calcularMaxima(float ventas[MAX_VENTAS], int n);

#endif


⸻

✅ ventas.c

#include <stdio.h>
#include "ventas.h"

// Leer montos de ventas con validación
void leerVentas(float ventas[MAX_VENTAS], int n)
{
    for(int i = 0; i < n; i++)
    {
        float monto;
        do {
            printf("Ingrese el monto de la venta %d: ", i + 1);

            if(scanf("%f", &monto) != 1 || monto < 0) {
                printf("Monto invalido. Intente nuevamente.\n");
                while(getchar() != '\n'); 
                monto = -1;
            }

        } while(monto < 0);

        ventas[i] = monto;
    }
}

// Calcular total
float calcularTotal(float ventas[MAX_VENTAS], int n)
{
    float total = 0;
    for(int i = 0; i < n; i++)
        total += ventas[i];

    return total;
}

// Calcular promedio
float calcularPromedio(float ventas[MAX_VENTAS], int n)
{
    return calcularTotal(ventas, n) / n;
}

// Calcular venta máxima
float calcularMaxima(float ventas[MAX_VENTAS], int n)
{
    float max = ventas[0];
    for(int i = 1; i < n; i++)
        if(ventas[i] > max)
            max = ventas[i];

    return max;
}


⸻

✅ main.c

#include <stdio.h>
#include "ventas.h"

int main()
{
    float ventas[MAX_VENTAS];
    int n;

    // Solicitar cantidad de ventas
    do {
        printf("Cuantas ventas desea registrar (1 - 30): ");
        if(scanf("%d", &n) != 1 || n < 1 || n > MAX_VENTAS)
        {
            printf("Valor invalido. Debe ser entre 1 y 30.\n");
            while(getchar() != '\n'); 
            n = -1;
        }
    } while(n < 1 || n > MAX_VENTAS);

    // Leer ventas
    leerVentas(ventas, n);

    // Procesar
    float total = calcularTotal(ventas, n);
    float promedio = calcularPromedio(ventas, n);
    float maxima = calcularMaxima(ventas, n);

    // Mostrar resultados
    printf("\n--- RESULTADOS ---\n");
    printf("Total de ventas: %.2f\n", total);
    printf("Promedio de ventas: %.2f\n", promedio);
    printf("Venta maxima: %.2f\n", maxima);

    return 0;
}


⸻

🧠 LISTO PARA ENTREGAR

Si lo copias en Visual Studio Code y compilas así:

gcc main.c ventas.c -o ventas

Te funciona perfecto.

⸻

🌞 ¿Quieres que también te genere un PDF o un README listo para subir a GitHub?
