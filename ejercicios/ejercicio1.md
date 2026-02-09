### EJERCICIO 1

## Escriba una función que imprima únicamente los números primos de la serie de Fibonacci hasta el n-ésimo término. Escriba una función que reciba una cantidad entera de segundos y retorne un string que muestre esa cantidad en formato HH:MM:SS. NO utilizar la clase DateTime.


```

#include <iostream>
using namespace std;

bool esPrimo(int n) {
    if (n <= 1) return false;

    for (int i = 2; i * i <= n; i++) {
        if (n % i == 0)
            return false;
    }
    return true;
}

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


