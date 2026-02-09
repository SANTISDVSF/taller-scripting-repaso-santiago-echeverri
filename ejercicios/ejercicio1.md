### EJERCICIO 1


```

#include <iostream>
using namespace std;

// Función para verificar si un número es primo
bool esPrimo(int n) {
    if (n <= 1) return false;

    for (int i = 2; i * i <= n; i++) {
        if (n % i == 0)
            return false;
    }
    return true;
}

// Función que imprime los números primos de la serie de Fibonacci
void imprimirFibonacciPrimos(int n) {
    int a = 0, b = 1, c;

    for (int i = 1; i <= n; i++) {
        if (esPrimo(a)) {
            cout << a << endl;
        }
        c = a + b;
        a = b;
        b = c;
    }
}

int main() {
    int n;
    cout << "Ingrese la cantidad de terminos: ";
    cin >> n;

    imprimirFibonacciPrimos(n);

    return 0;
}

```


