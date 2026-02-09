### EJERCICIO 1

## Escriba una función que imprima únicamente los números primos de la serie de Fibonacci hasta el n-ésimo término. Escriba una función que reciba una cantidad entera de segundos y retorne un string que muestre esa cantidad en formato HH:MM:SS. NO utilizar la clase DateTime.


```

using System;

class Program
{
    static bool EsPrimo(int n)
    {
        if (n <= 1) return false;

        for (int i = 2; i * i <= n; i++)
        {
            if (n % i == 0)
                return false;
        }
        return true;
    }

    static void ImprimirFibonacciPrimos(int n)
    {
        int a = 0, b = 1, c;

        for (int i = 1; i <= n; i++)
        {
            if (EsPrimo(a))
            {
                Console.WriteLine(a);
            }
            c = a + b;
            a = b;
            b = c;
        }
    }

    static string SegundosAHora(int totalSegundos)
    {
        int horas = totalSegundos / 3600;
        int minutos = (totalSegundos % 3600) / 60;
        int segundos = totalSegundos % 60;

        return horas.ToString("D2") + ":" +
               minutos.ToString("D2") + ":" +
               segundos.ToString("D2");
    }

    static void Main(string[] args)
    {
        Console.Write("Ingrese la cantidad de términos de Fibonacci: ");
        int n = int.Parse(Console.ReadLine());

        Console.WriteLine("\nNúmeros primos en Fibonacci:");
        ImprimirFibonacciPrimos(n);

        Console.Write("\nIngrese una cantidad de segundos: ");
        int segundos = int.Parse(Console.ReadLine());

        Console.WriteLine("Formato HH:MM:SS -> " + SegundosAHora(segundos));
    }
}


```


