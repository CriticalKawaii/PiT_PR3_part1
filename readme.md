## ПРАКТИЧЕСКАЯ РАБОТА №3 Часть 1
## ОТЛАДКА ПРОГРАММЫ РАЗЛИЧНЫМИ СПОСОБАМИ
### Выполнили Студенты группы 3ИСИП-122 Саргас К. Романов Д.
### 1. [Отладка консольного приложения «Фибоначчи»](https://learn.microsoft.com/ru-ru/training/modules/dotnet-debug-visual-studio/4-use-visual-studio-debugger)
**Использованные средства отладчика**:
- Пошаговое выполнение с использованием Breakpoints (точки остановы)
- Проверка состояния локальных переменных
- Использование Debugger controls (step into, step over, step out)

[Fibonacci.cs](https://github.com/CriticalKawaii/PiT_PR3_part1/blob/master/Fibonacci.cs)
```c#
int result = Fibonacci(5);
Console.WriteLine(result);

static int Fibonacci(int n)
{
    int n1 = 0;
    int n2 = 1;
    int sum;

    for (int i = 2; i <= n; i++)
    {
        sum = n1 + n2;
        n1 = n2;
        n2 = sum;
    }

    return n == 0 ? n1 : n2;
}
```

### 2. [Отладка консольного приложения «Галактики»](https://learn.microsoft.com/ru-ru/visualstudio/debugger/debugging-absolute-beginners?view=vs-2022&source=recommendations&tabs=csharp)
**Использованные средства отладчика**:
- Пошаговое выполнение с использованием Breakpoints
- Использование Debugger controls (step into, step over, step out)
- Использование переменных и состояния объектов во время отладки

[Galaxy.cs](https://github.com/CriticalKawaii/PiT_PR3_part1/blob/master/Galaxy.cs)
```c#
using System;
using System.Collections.Generic;

namespace ConsoleApp_FirstApp
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Welcome to Galaxy News!");
            IterateThroughList();
            Console.ReadKey();
        }

        private static void IterateThroughList()
        {
            var theGalaxies = new List<Galaxy>
        {
            new Galaxy() { Name="Tadpole", MegaLightYears=400, GalaxyType=new GType('S')},
            new Galaxy() { Name="Pinwheel", MegaLightYears=25, GalaxyType=new GType('S')},
            new Galaxy() { Name="Cartwheel", MegaLightYears=500, GalaxyType=new GType('L')},
            new Galaxy() { Name="Small Magellanic Cloud", MegaLightYears=.2, GalaxyType=new GType('I')},
            new Galaxy() { Name="Andromeda", MegaLightYears=3, GalaxyType=new GType('S')},
            new Galaxy() { Name="Maffei 1", MegaLightYears=11, GalaxyType=new GType('E')}
        };

            foreach (Galaxy theGalaxy in theGalaxies)
            {
                Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
            }
        }
    }

    public class Galaxy
    {
        public string Name { get; set; }

        public double MegaLightYears { get; set; }
        public object GalaxyType { get; set; }

    }

    public class GType
    {
        public GType(char type)
        {
            switch(type)
            {
                case 'S':
                    MyGType = Type.Spiral;
                    break;
                case 'E':
                    MyGType = Type.Elliptical;
                    break;
                case 'I':
                    MyGType = Type.Irregular;
                    break;
                case 'L':
                    MyGType = Type.Lenticular;
                    break;
                default:
                    break;
            }
        }
        public object MyGType { get; set; }
        private enum Type { Spiral, Elliptical, Irregular, Lenticular}
    }
}
```
### 3. [Отладка консольного приложения «Буквы»](https://learn.microsoft.com/ru-ru/visualstudio/get-started/csharp/tutorial-debugger?toc=%2Fvisualstudio%2Fdebugger%2Ftoc.json&view=vs-2022#create-a-project)
**Использованные средства отладчика**:
- Пошаговое выполнение с использованием Breakpoints
- Инспекция переменных с помощью подсказок данных
- Проверка состояния локальных переменных
- Использование окна "Наблюдение"
- Проверка стека вызовов

[Letters.cs]((https://github.com/CriticalKawaii/PiT_PR3_part1/blob/master/Letters.cs))
```c#
using System;

class ArrayExample
{
    static void Main()
    {
        char[] letters = { 'f', 'r', 'e', 'd', ' ', 's', 'm', 'i', 't', 'h' };
        string name = "";
        int[] a = new int[10];
        for (int i = 0; i < letters.Length; i++)
        {
            name += letters[i];
            a[i] = i + 1;
            SendMessage(name, a[i]);
        }
        Console.ReadKey();
    }

    static void SendMessage(string name, int msg)
    {
        Console.WriteLine("Hello, " + name + "! Count to " + msg);
    }
}
```
