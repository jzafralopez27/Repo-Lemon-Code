namespace AppLemonCode
{
    class Program
    {
        public static void Main(string[] args)
        {

            // Ejercicio 1.
            // 1 - Solicite el nombre de una persona, su edad y el nombre de una ciudad.
            // Despu�s de solicitar estos datos deber� mostrar por pantalla el siguiente mensaje: Te llamas y tienes <a�os> a�os. Bienvenido a

            Console.WriteLine("Introduzca su nombre, edad y nombre de la ciudad");

            string nombre = Console.ReadLine();
            var edad = Console.ReadLine();
            string ciudad = Console.ReadLine();

            Console.WriteLine("Te llamas " + nombre + " , tienes " + edad + " a�os y has llegado a " + ciudad);

            Console.WriteLine();

            // Ejercicio 2.
            // 2 - Solicite dos n�meros y diga cu�l es el mayor.

            Console.WriteLine("Introduzca el primer n�mero");
            var entrada1 = Console.ReadLine();
            int num1 = Convert.ToInt32(entrada1);

            Console.WriteLine("Introduzca el segundo n�mero");
            var entrada2 = Console.ReadLine();
            int num2 = Convert.ToInt32(entrada2);

            if (num1 != null && num2 != null)
            {
                if (num1 == num2)
                {
                    Console.WriteLine("Son el mismo n�mero");
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

            Console.WriteLine("Introduzca d�a de la semana");
            string diasemana = Console.ReadLine();

            diasemana = diasemana.ToLower(); // hago el lower para que me acepte tambi�n los d�as de la semana en min�scula

            if (!string.IsNullOrWhiteSpace(diasemana))
            {
                if (diasemana == "viernes" ||  diasemana == "sabado" || diasemana == "domingo")
                {
                    Console.WriteLine("El " + diasemana + " es parte del fin de semana");
                } else if (diasemana == "lunes" || diasemana == "martes" || diasemana == "miercoles" || diasemana == "jueves"){
                    Console.WriteLine("El " + diasemana + " no es parte del fin de semana");
                } else 
                {
                    Console.WriteLine("Por favor, introduzca un d�a de la semana");
                }
            }

            // Creo que es m�s �ptimo hacerlo con un switch, pero bueno...

            // Ejercicio 4.
            // Recorre los n�meros del 1 al 100. Muestra los n�meros pares.

            for (int i = 0; i < 100; i++)
            {
                if (i % 2 == 0)
                Console.WriteLine(i);
            }

            // Ejercicio 5.
            // Solicitar un n�mero n al usuario y generar una array de n n�meros aleatorios.

            Console.WriteLine("Introduzca un n�mero aleatorio");
            var entrada3 = Console.ReadLine();
            int capacidad = Convert.ToInt32(entrada3);

            int[] array = new int[capacidad];
            Random aleatorio = new Random();

            for (int i = 0;i < array.Length; i++)
            {
                array[i] = aleatorio.Next(100); // Ponendo el 100 entre par�ntesis limito a que el m�ximo sea 100, porque si no, da n�meros muy grandes.
            }

            foreach (int i in array)
            {
               Console.WriteLine(i);
            }

            // Ejercicio 6.
            // Solicitar un n�mero y caracter al usuario. Crear una pir�mide con n filas y el caracter solicitado.

            Console.WriteLine("Introduzca un n�mero");
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