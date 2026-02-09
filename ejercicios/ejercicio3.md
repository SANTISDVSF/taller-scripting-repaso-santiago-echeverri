### EJERCICIO 3


```

using System;


abstract class AbstractSample
{
    private string message;

    protected void SetMessage(string msg)
    {
        message = msg;
    }

    protected string GetMessage()
    {
        return message;
    }

    public abstract void PrintMessage(string msg);

    public virtual string InvertMessage(string msg)
    {
        SetMessage(msg);

        char[] chars = message.ToCharArray();
        Array.Reverse(chars);

        message = new string(chars);
        return message;
    }

    protected string SwapCase(string text)
    {
        char[] chars = text.ToCharArray();

        for (int i = 0; i < chars.Length; i++)
        {
            if (char.IsUpper(chars[i]))
                chars[i] = char.ToLower(chars[i]);
            else if (char.IsLower(chars[i]))
                chars[i] = char.ToUpper(chars[i]);
        }

        return new string(chars);
    }
}

class SimpleSample : AbstractSample
{
    public override void PrintMessage(string msg)
    {
        SetMessage(msg);
        Console.WriteLine(GetMessage());
    }
}

class SwapCaseSample : AbstractSample
{
    public override void PrintMessage(string msg)
    {
        SetMessage(msg);
        Console.WriteLine(SwapCase(GetMessage()));
    }

    // Sobrescribe InvertMessage
    public override string InvertMessage(string msg)
    {
        string inverted = base.InvertMessage(msg);
        string swapped = SwapCase(inverted);
        SetMessage(swapped);
        return swapped;
    }
}

class MessageManager
{
    private AbstractSample sample1;
    private AbstractSample sample2;

    public MessageManager()
    {
        sample1 = new SimpleSample();
        sample2 = new SwapCaseSample();
    }

    public void Execute(string message)
    {
        Console.WriteLine("---- SimpleSample ----");
        sample1.PrintMessage(message);

        Console.WriteLine("---- SwapCaseSample ----");
        sample2.PrintMessage(message);
    }
}

class Program
{
    static void Main(string[] args)
    {
        Console.Write("Ingrese un mensaje: ");
        string input = Console.ReadLine();

        MessageManager manager = new MessageManager();
        manager.Execute(input);
    }
}


```

