## 1 - Read Books
Crea una función isBookRead que reciba una lista de libros y un título y devuelva si se ha leído o no dicho libro. 
Un libro es un objeto con title como string y isRead como booleano. En caso de no existir el libro devolver false.

namespace LemonCodeJoreZafra
{
     class Libro
    {

        string title;
        Boolean isRead;

        public Libro (string title, Boolean isRead)
        {
            this.title=title;
            this.isRead=isRead;
        }

        public static bool IsBookRead(Libro[] libros, string titleToSearch)
        {
            foreach (Libro libro in libros)
            {
                if (libro.title == titleToSearch)
                {
                    return libro.isRead;
                } 
            }
                return false;
        }

       public static void Main(string[] args)
        {

            Libro[] libros = new Libro[]
        {
            new Libro("El nombre del viento",true),
            new Libro("La resistencia",true),
            new Libro("El estrecho camino entre deseos",false),
            new Libro("Crónicas de Idhun",false)
        };

            Console.WriteLine(IsBookRead(libros, "El nombre del viento"));
            Console.WriteLine(IsBookRead(libros, "La resistencia"));
            Console.WriteLine(IsBookRead(libros, "El estrecho camino entre deseos"));
            Console.WriteLine(IsBookRead(libros, "Crónicas de Idhun"));

        }
    }
}

<hr>

## 2- Slot Machine

El objetivo de este ejercicio es crear una máquina tragaperras utilizando clases donde cada vez que juguemos insertemos una moneda. Cada máquina tragaperras (instancia) tendrá un contador de monedas que automáticamente se irá incrementando conforme vayamos jugando.

Cuando se llame al método play el número de monedas se debe incrementar de forma automática y debe generar tres booleanos aleatorios que representarán el estado de las 3 ruletas. El usuario habrá ganado en caso de que los tres booleanos sean true, y por tanto deberá mostrarse por consola el mensaje:

"Congratulations!!!. You won <número de monedas> coins!!";
y reiniciar las monedas almacenadas, ya que las hemos conseguido y han salido de la máquina. En caso contrario deberá mostrar otro mensaje:

"Good luck next time!!".
Se preguntará al usuario si quiere jugar o dejar.

Si el usuario elige jugar. Se llamará al método play.
Si usuario elige cualquier otra opción se terminará la ejecución de la aplicación.

namespace LemonCodeJoreZafra
{
     class SlotMachine
    {
        int contadorMoneda = 0;
        bool[] aleatorios = new bool[3];
        Random rand = new Random();


        public SlotMachine() 
        {
        } 

        public void Play()
        {
 
            Console.WriteLine("¿Hola, qué deseas hacer? Escribe 'jugar' si deseas jugar o cualquier otra cosa si quieres salir.");
            string respuesta = Console.ReadLine();

            while (respuesta == "jugar")
            {

                contadorMoneda++;

                int primerNum = rand.Next(2);
                if (primerNum == 0)
                {
                    aleatorios[0] = true;
                    Console.WriteLine("Primer número True!!");
                } else
                {
                    aleatorios[0] = false;
                    Console.WriteLine("Primer número False...");
                }

                int segundoNum = rand.Next(2);
                if (segundoNum == 0)
                {
                    aleatorios[1] = true;
                    Console.WriteLine("Segundo número True!!");
                } else
                {
                    aleatorios[1] = false;
                    Console.WriteLine("Segundo número False...");
                }

                int tercerNum = rand.Next(2);
                if (tercerNum == 0)
                {
                    aleatorios[2] = true;
                    Console.WriteLine("Tercer número True!!");
                }
                else
                {
                    aleatorios[2] = false;
                    Console.WriteLine("Tercer número False...");
                }

                if (aleatorios[0] == true && aleatorios[1] == true && aleatorios[2] == true)
                {
                    Console.WriteLine("Enhorabuena!!! Premio!!!! Has ganado " +contadorMoneda+ " monedas!");
                    contadorMoneda = 0;

                } else { Console.WriteLine("Sigue intentándolo, no todos han dado true!"); }

                Console.WriteLine("\"¿Hola, qué deseas hacer? Escribe 'jugar' si deseas jugar o cualquier otra cosa si quieres salir.\"");
                respuesta = Console.ReadLine();
            }
        }

        public static void Main(string[] args)
        {
            SlotMachine machine = new SlotMachine();

            machine.Play();
        }
    }
}


