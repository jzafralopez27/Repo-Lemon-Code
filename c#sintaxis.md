namespace AppLemonCode
{
    class Program
    {
        public static void Main(string[] args)
        {

            // Ejercicio 1.
            // 1 - Solicite el nombre de una persona, su edad y el nombre de una ciudad.
            // Después de solicitar estos datos deberá mostrar por pantalla el siguiente mensaje: Te llamas y tienes <años> años. Bienvenido a

            Console.WriteLine("Introduzca su nombre, edad y nombre de la ciudad");

            string nombre = Console.ReadLine();
            var edad = Console.ReadLine();
            string ciudad = Console.ReadLine();

            Console.WriteLine("Te llamas " + nombre + " , tienes " + edad + " años y has llegado a " + ciudad);

            Console.WriteLine();

            // Ejercicio 2.
            // 2 - Solicite dos números y diga cuál es el mayor.

            Console.WriteLine("Introduzca el primer número");
            var entrada1 = Console.ReadLine();
            int num1 = Convert.ToInt32(entrada1);

            Console.WriteLine("Introduzca el segundo número");
            var entrada2 = Console.ReadLine();
            int num2 = Convert.ToInt32(entrada2);

            if (num1 != null && num2 != null)
            {
                if (num1 == num2)
                {
                    Console.WriteLine("Son el mismo número");
                }
                
                if (num1 > num2)
                {
                    Console.WriteLine("El mayor es " + num1);
                } else
                {
                    Console.WriteLine("El mayor es " + num2);
                }
            }

            Console.WriteLine();

            // Ejercicio 3.
            // Pedir el nombre de la semana al usuario y decirle si es fin de semana o no. En caso de error, indicarlo.

            Console.WriteLine("Introduzca día de la semana");
            string diasemana = Console.ReadLine();

            diasemana = diasemana.ToLower(); // hago el lower para que me acepte también los días de la semana en minúscula

            if (!string.IsNullOrWhiteSpace(diasemana))
            {
                if (diasemana == "viernes" ||  diasemana == "sabado" || diasemana == "domingo")
                {
                    Console.WriteLine("El " + diasemana + " es parte del fin de semana");
                } else if (diasemana == "lunes" || diasemana == "martes" || diasemana == "miercoles" || diasemana == "jueves"){
                    Console.WriteLine("El " + diasemana + " no es parte del fin de semana");
                } else 
                {
                    Console.WriteLine("Por favor, introduzca un día de la semana");
                }
            }

            // Creo que es más óptimo hacerlo con un switch, pero bueno...

            // Ejercicio 4.
            // Recorre los números del 1 al 100. Muestra los números pares.

            for (int i = 0; i < 100; i++)
            {
                if (i % 2 == 0)
                Console.WriteLine(i);
            }

            // Ejercicio 5.
            // Solicitar un número n al usuario y generar una array de n números aleatorios.

            Console.WriteLine("Introduzca un número aleatorio");
            var entrada3 = Console.ReadLine();
            int capacidad = Convert.ToInt32(entrada3);

            int[] array = new int[capacidad];
            Random aleatorio = new Random();

            for (int i = 0;i < array.Length; i++)
            {
                array[i] = aleatorio.Next(100); // Ponendo el 100 entre paréntesis limito a que el máximo sea 100, porque si no, da números muy grandes.
            }

            foreach (int i in array)
            {
               Console.WriteLine(i);
            }

            // Ejercicio 6.
            // Solicitar un número y caracter al usuario. Crear una pirámide con n filas y el caracter solicitado.

            Console.WriteLine("Introduzca un número");
            var entrada4 = Console.ReadLine();
            int numero = Convert.ToInt32(entrada4);

            Console.WriteLine("Introduzca un caracter");
            char caracter = Console.ReadKey().KeyChar;

            for (int i = 0;i <= numero; i++)
            {
                for (int j = 0;j <= numero; j++)
                {
                    if (i == numero || j == 1 || j == i)
                    {
                        Console.Write(caracter);
                    }
                    else
                    {
                        Console.Write(" ");
                    }
                }
                Console.WriteLine();
            }
          }
        }
    }