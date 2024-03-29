using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace LemonCodeJoreZafra
{
    internal class PatientProgram
    {
    public class Patient
    {
        public int id { get; set; }
        public string name { get; set; }
        public string lastName { get; set; }
        public string sex { get; set; }
        public float temperature { get; set; }
        public int heartRate { get; set; }
        public string specialty { get; set; }
        public int age { get; set; }

            public override string ToString()
            {
                return $"Patient's data: ID: {id}, name: {name}, lastName: {lastName}, sex: {sex}, temperature: {temperature}, heartRate: {heartRate}, specialty: {specialty}, age: {age}";
            }
        }

    public static void Main(string[] args)
    {
            var patients = new List<Patient>
            {
                new Patient { id = 1, name = "John", lastName = "Doe", sex = "Male", temperature = 36.8f, heartRate = 80, specialty = "general medicine", age = 44 },
                new Patient { id = 2, name = "Jane", lastName = "Doe", sex = "Female", temperature = 36.8f, heartRate = 70, specialty = "general medicine", age = 43 },
                new Patient { id = 3, name = "Junior", lastName = "Doe", sex = "Male", temperature = 36.8f, heartRate = 90, specialty = "pediatrics", age = 8 },
                new Patient { id = 4, name = "Mary", lastName = "Wien", sex = "Female", temperature = 36.8f, heartRate = 120, specialty = "general medicine", age = 20 },
                new Patient { id = 5, name = "Scarlett", lastName = "Somez", sex = "Female", temperature = 36.8f, heartRate = 110, specialty = "general medicine", age = 30 },
                new Patient { id = 6, name = "Brian", lastName = "Kid", sex = "Male", temperature = 39.8f, heartRate = 80, specialty = "pediatrics", age = 11 }
            };

            // Ejercicio 1. Extraer la lista de pacientes que sean de la especialidad pediatrics y que tengan menos de 10 años.

            var patientsPediatrics = patients.Where(patient => patient.specialty == "pediatrics" && patient.age < 10);

            foreach (var patient in patientsPediatrics)
            {
                Console.WriteLine(patient);
            }

            Console.ReadLine();

            // Ejercicio 2. Queremos activar el protocolo de urgencia si hay algún paciente con ritmo cardíaco mayor que 100 o temperatura mayor a 39.

            var emergencyProtocol = patients.Where(patient => patient.heartRate > 100 || patient.temperature > 39);

            foreach (var emergency in emergencyProtocol)
            {
                Console.WriteLine("EMERGENCY PROTOCOL ACTIVATED WITH PATIENT: "+emergency);
            }

            Console.ReadLine();

            // Ejercicio 3. No podemos atender a todos los pacientes hoy por lo que vamos a crear una nueva coleccion y reasignar a los pacientes de pediatrics a general medicine.

            var movedPatients = new List<Patient>();

            var patientsToChange = patients.Where(patient => patient.specialty == "pediatrics");
            
            foreach (var patient in patientsToChange)
            {
                patient.specialty = "general medicine";
                movedPatients.Add(patient);
                Console.WriteLine("Patient moved from pediatrics to general medicine correctly" + patient);
            }

            Console.ReadLine();

            // Ejercicio 4. Queremos conocer de una sola consulta el numero de pacientes que estan asignado a general medicine y a pediatrics.
            // (Sale que los 6 están en general medicine por lo realizado en el ejercicio 3)

            var countPatients = patients.GroupBy(patient => patient.specialty).Select(x => $"{x.Key}: {x.Count()}");

            foreach (var patient in countPatients)
            {
                Console.WriteLine(patient);
            }
            Console.WriteLine(countPatients);

            Console.ReadLine();

            // Ejercicio 5. Devuelve una lista nueva que por cada paciente se indique si tiene prioridad o no.
            // Se tendrá prioridad si el ritmo cardiaco es mayor 100 o la temperatura es mayor a 39.

            List<bool> patientPriority = patients.Select(patient =>
            {
                return patient.heartRate > 100 || patient.temperature > 39;
            }).ToList();

            foreach (var priority in patientPriority)
            {
                Console.WriteLine(priority ? "Prioridad" : "No Prioridad");
            }

            Console.ReadLine();

            // Ejercicio 6. Queremos conocer de una sola consulta La edad media de pacientes asignados a pediatrics y general medicine.
            // (Da 26 y no otro número porque sólo hay pacientes en general medicine y ninguno en pediatrics por el ejercico 3...)

            var avgPatients = patients.GroupBy(patient => patient.specialty).Select(x => $"{x.Key}: {x.Average(patient => patient.age)}");

            foreach (var patient in avgPatients)
            {
                Console.WriteLine(patient);
            }
        }
    }
}