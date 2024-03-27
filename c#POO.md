## 1 - Read Books
Crea una funci�n isBookRead que reciba una lista de libros y un t�tulo y devuelva si se ha le�do o no dicho libro. 
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
            new Libro("Cr�nicas de Idhun",false)
        };

            Console.WriteLine(IsBookRead(libros, "El nombre del viento"));
            Console.WriteLine(IsBookRead(libros, "La resistencia"));
            Console.WriteLine(IsBookRead(libros, "El estrecho camino entre deseos"));
            Console.WriteLine(IsBookRead(libros, "Cr�nicas de Idhun"));

        }
    }
}

<hr>

## 2- Slot Machine

El objetivo de este ejercicio es crear una m�quina tragaperras utilizando clases donde cada vez que juguemos insertemos una moneda. Cada m�quina tragaperras (instancia) tendr� un contador de monedas que autom�ticamente se ir� incrementando conforme vayamos jugando.

Cuando se llame al m�todo play el n�mero de monedas se debe incrementar de forma autom�tica y debe generar tres booleanos aleatorios que representar�n el estado de las 3 ruletas. El usuario habr� ganado en caso de que los tres booleanos sean true, y por tanto deber� mostrarse por consola el mensaje:

"Congratulations!!!. You won <n�mero de monedas> coins!!";
y reiniciar las monedas almacenadas, ya que las hemos conseguido y han salido de la m�quina. En caso contrario deber� mostrar otro mensaje:

"Good luck next time!!".
Se preguntar� al usuario si quiere jugar o dejar.

Si el usuario elige jugar. Se llamar� al m�todo play.
Si usuario elige cualquier otra opci�n se terminar� la ejecuci�n de la aplicaci�n.

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
 
            Console.WriteLine("�Hola, qu� deseas hacer? Escribe 'jugar' si deseas jugar o cualquier otra cosa si quieres salir.");
            string respuesta = Console.ReadLine();

            while (respuesta == "jugar")
            {

                contadorMoneda++;

                int primerNum = rand.Next(2);
                if (primerNum == 0)
                {
                    aleatorios[0] = true;
                    Console.WriteLine("Primer n�mero True!!");
                } else
                {
                    aleatorios[0] = false;
                    Console.WriteLine("Primer n�mero False...");
                }

                int segundoNum = rand.Next(2);
                if (segundoNum == 0)
                {
                    aleatorios[1] = true;
                    Console.WriteLine("Segundo n�mero True!!");
                } else
                {
                    aleatorios[1] = false;
                    Console.WriteLine("Segundo n�mero False...");
                }

                int tercerNum = rand.Next(2);
                if (tercerNum == 0)
                {
                    aleatorios[2] = true;
                    Console.WriteLine("Tercer n�mero True!!");
                }
                else
                {
                    aleatorios[2] = false;
                    Console.WriteLine("Tercer n�mero False...");
                }

                if (aleatorios[0] == true && aleatorios[1] == true && aleatorios[2] == true)
                {
                    Console.WriteLine("Enhorabuena!!! Premio!!!! Has ganado " +contadorMoneda+ " monedas!");
                    contadorMoneda = 0;

                } else { Console.WriteLine("Sigue intent�ndolo, no todos han dado true!"); }

                Console.WriteLine("\"�Hola, qu� deseas hacer? Escribe 'jugar' si deseas jugar o cualquier otra cosa si quieres salir.\"");
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


