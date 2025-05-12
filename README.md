El polimorfismo es una característica de la Programación Orientada a Objetos que permite que un mismo método trabaje con objetos de diferentes clases, siempre que estas clases hereden de una clase base o implementen una interfaz común.

Esto significa que podemos escribir un método general que reciba un objeto del tipo de la clase base (por ejemplo, Vehículo) y ese método funcionará correctamente con cualquier clase que herede de Vehículo (como Carro o Motocicleta).

Además, si se desea usar un comportamiento específico de una clase hija (como EncenderRadio() en la clase Carro), se puede usar el operador is para hacer una conversión segura del objeto.
