class Program2
{
    public static void Main(string[] args)
    {
        Random random = new Random();
        int numaleatorio = random.Next(1,51);

        int numintentos = 0;

        while (numintentos < 10)
        {
            try
            {
            Console.WriteLine("Adivina un número entre el 1 y el 50");
            var entrada = Console.ReadLine();

                if (string.IsNullOrEmpty(entrada))
                {
                    throw new ArgumentNullException("entrada","Debes introducir un número ...");
                }

                int numero = Convert.ToInt32(entrada);

                if (numero < 1)
                {
                    throw new ArgumentOutOfRangeException("numero", "Por favor, no introduzcas números menores de 1...");
                }

                if (numero > 50)
                {
                    throw new ArgumentOutOfRangeException("numero", "Por favor, no introduzcas números mayores de 50...");
                }
            
            if (numero > numaleatorio)
            {
                Console.WriteLine("El número que buscas es MENOR, sigue intentándolo");
            } else if (numero < numaleatorio)
            {
                Console.WriteLine("El número que buscas es MAYOR, sigue intentándolo");
            }
                
            if (numero == numaleatorio)
            {
                Console.WriteLine("¡Enhorabuena, lo has acertado! El número era " + numaleatorio);
                break;
            }
            }
            catch (ArgumentNullException ex) {
                Console.WriteLine(ex.Message);
            }
            catch (FormatException ex)
            {
                Console.WriteLine("Error. Introduce solo numeros...");
            }
            catch(ArgumentOutOfRangeException ex)
            {
                Console.WriteLine(ex.Message);  
            }

            numintentos++;
        }
    }
}