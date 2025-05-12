El polimorfismo es una característica de la Programación Orientada a Objetos que permite que un mismo método trabaje con objetos de diferentes clases, siempre que estas clases hereden de una clase base o implementen una interfaz común.

Esto significa que podemos escribir un método general que reciba un objeto del tipo de la clase base (por ejemplo, Vehículo) y ese método funcionará correctamente con cualquier clase que herede de Vehículo (como Carro o Motocicleta).

Además, si se desea usar un comportamiento específico de una clase hija (como EncenderRadio() en la clase Carro), se puede usar el operador is para hacer una conversión segura del objeto.

using System; // Importa funcionalidades básicas como entrada/salida por consola

// Define un espacio de nombres para organizar las clases y evitar conflictos
namespace PolimorfismoEjemplo
{
    // Clase base llamada Vehículo: otras clases pueden heredar de ella
    public class Vehículo
    {
        // Propiedad Velocidad: almacena la velocidad actual del vehículo
        // Es pública, puede leerse o modificarse desde otras clases
        public int Velocidad { get; set; } = 0; // Inicia en 0 por defecto

        // Método virtual Acelerar: puede ser modificado ("sobrescrito") por clases hijas
        public virtual void Acelerar()
        {
            Velocidad += 10; // Aumenta la velocidad en 10 unidades
        }

        // Método virtual Reversa: también puede ser sobrescrito
        public virtual void Reversa()
        {
            Velocidad -= 5; // Disminuye la velocidad en 5 unidades
        }
    }

    // Clase derivada Carro: hereda de Vehículo y puede modificar o extender su comportamiento
    public class Carro : Vehículo
    {
        // Método propio del Carro, que no existe en la clase Vehículo
        public void EncenderRadio()
        {
            Console.WriteLine("Radio encendida 🎶"); // Imprime un mensaje indicando que la radio se encendió
        }

        // Sobrescribe el método Acelerar de la clase base
        public override void Acelerar()
        {
            Velocidad += 20; // Aumenta la velocidad en 20 unidades, más rápido que un vehículo genérico
            Console.WriteLine("El carro acelera rápidamente."); // Imprime mensaje indicando cómo acelera
        }
    }

    // Clase derivada Motocicleta: también hereda de Vehículo
    public class Motocicleta : Vehículo
    {
        // Sobrescribe el método Acelerar
        public override void Acelerar()
        {
            Velocidad += 15; // Aumenta la velocidad en 15 unidades
            Console.WriteLine("La moto acelera ágilmente."); // Imprime mensaje específico de la moto
        }
    }

    // Clase principal del programa
    class Program
    {
        // Método Reparar: recibe un objeto de tipo Vehículo (puede ser base o derivado)
        static void Reparar(Vehículo vehículo)
        {
            // Muestra mensaje inicial de reparación
            Console.WriteLine("\nIniciando reparación...");

            // Muestra la velocidad antes de acelerar
            Console.WriteLine($"Velocidad inicial: {vehículo.Velocidad}");

            // Llama al método Acelerar del objeto (usa polimorfismo: ejecutará la versión correspondiente)
            vehículo.Acelerar();

            // Muestra la velocidad luego de acelerar
            Console.WriteLine($"Velocidad después de acelerar: {vehículo.Velocidad}");

            // Llama al método Reversa del objeto
            vehículo.Reversa();

            // Muestra la velocidad luego de reversa
            Console.WriteLine($"Velocidad después de reversa: {vehículo.Velocidad}");

            // Verifica si el objeto es específicamente un Carro
            if (vehículo is Carro miCarro)
            {
                // Si es un carro, enciende la radio (método exclusivo del Carro)
                miCarro.EncenderRadio();
            }

            // Mensaje final de reparación
            Console.WriteLine("¡Reparación finalizada!\n");
        }

        // Método Main: punto de entrada del programa
        static void Main(string[] args)
        {
            // Crea un objeto de tipo Vehículo (usa la clase base)
            Vehículo miVehículo = new Vehículo(); // Tiene velocidad y métodos base

            // Crea un objeto de tipo Carro (usa clase hija que hereda y extiende Vehículo)
            Carro miCarro = new Carro(); // Tiene aceleración diferente y radio

            // Crea un objeto de tipo Motocicleta (también es una clase hija)
            Motocicleta miMoto = new Motocicleta(); // Tiene aceleración diferente

            // Llama al método Reparar con cada objeto creado
            Reparar(miVehículo); // Llama a métodos de Vehículo
            Reparar(miCarro);    // Llama a métodos sobreescritos en Carro (y radio)
            Reparar(miMoto);     // Llama a métodos sobreescritos en Motocicleta
        }
    }
}
