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
            Console.WriteLine("Adivina un n�mero entre el 1 y el 50");
            var entrada = Console.ReadLine();

                if (string.IsNullOrEmpty(entrada))
                {
                    throw new ArgumentNullException("entrada","Debes introducir un n�mero ...");
                }

                int numero = Convert.ToInt32(entrada);

                if (numero < 1)
                {
                    throw new ArgumentOutOfRangeException("numero", "Por favor, no introduzcas n�meros menores de 1...");
                }

                if (numero > 50)
                {
                    throw new ArgumentOutOfRangeException("numero", "Por favor, no introduzcas n�meros mayores de 50...");
                }
            
            if (numero > numaleatorio)
            {
                Console.WriteLine("El n�mero que buscas es MENOR, sigue intent�ndolo");
            } else if (numero < numaleatorio)
            {
                Console.WriteLine("El n�mero que buscas es MAYOR, sigue intent�ndolo");
            }
                
            if (numero == numaleatorio)
            {
                Console.WriteLine("�Enhorabuena, lo has acertado! El n�mero era " + numaleatorio);
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