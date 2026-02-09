### Ejercicio 2

```

using System;

class Program
{
    const int APUESTA = 1000;

    static void SepararDigitos(int num, int[] digitos)
    {
        digitos[3] = num % 10;
        digitos[2] = (num / 10) % 10;
        digitos[1] = (num / 100) % 10;
        digitos[0] = (num / 1000) % 10;
    }

    static int CalcularPremio(int num, int resultado)
    {
        int[] n = new int[4];
        int[] r = new int[4];

        SepararDigitos(num, n);
        SepararDigitos(resultado, r);

        if (n[0] == r[0] && n[1] == r[1] && n[2] == r[2] && n[3] == r[3])
            return 4500 * APUESTA;

        bool[] usados = new bool[4];
        int aciertos = 0;

        for (int i = 0; i < 4; i++)
        {
            for (int j = 0; j < 4; j++)
            {
                if (n[i] == r[j] && !usados[j])
                {
                    usados[j] = true;
                    aciertos++;
                    break;
                }
            }
        }

        if (aciertos == 4)
            return 200 * APUESTA;

        if (n[1] == r[1] && n[2] == r[2] && n[3] == r[3])
            return 400 * APUESTA;

        if (n[2] == r[2] && n[3] == r[3])
            return 50 * APUESTA;

        // Última cifra
        if (n[3] == r[3])
            return 5 * APUESTA;

        return 0;
    }

    static void Main(string[] args)
    {
        Console.Write("Ingrese el numero apostado (4 digitos): ");
        int num = int.Parse(Console.ReadLine());

        Console.Write("Ingrese el numero ganador (4 digitos): ");
        int resultado = int.Parse(Console.ReadLine());

        int premio = CalcularPremio(num, resultado);

        if (premio > 0)
            Console.WriteLine("Ganaste $" + premio);
        else
            Console.WriteLine("No obtuviste ningun premio.");
    }
}
