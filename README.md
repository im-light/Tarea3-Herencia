# Tarea 3-Herencia
___
###  1.  Define: Clase Base, Clase Derivada.



El termino de clase base surge a partir de la herencia la cual como hemos visto a lo largo del curso es una parte esencial del paradigma de programación orientada a objetos.


La herencia consiste en la creación de nuevas clases a partir de otras.


Entonces la clase base seria aquella de la cual se heredarán otras clases ya que tendrá una estructura mas general 
Y la clase derivada será aquella que obtiene propiedades y atributos de la clase base. 
___
###  2.  Haz un diagrama UML donde se muestre la relación de herencia entre las  clases Figura, Rectángulo y Circulo como vimos en clase.

![UML](https://github.com/im-light/Tarea3-Herencia/blob/master/imagenes/uml%20figura.png)
___
###  3.  Indica cuales son las clases base y las derivadas.
```c#
abstract class Figura
{
    // esta seria mi clase base
}
class Circulo : Figura
{
    // esta seria mi clase derivada
}

```
___
###  4. ¿Que es herencia simple y herencia múltiple? ¿En c# se puede hacer herencia múltiple?

La herencia es simple cuando la clase derivada que estamos considerando sólo tiene una clase base.


La herencia multiple es cuando una clase puede heredar comportamientos y características de más de una superclase.


En c# no se puede hacer herencia múltiple ya que no se sabría con exactitud de cual clase se va a heredar por lo que habría ambigüedad 
___
###  5. Escribe el programa de Figura como vimos en clase, donde agregues varios tipos de figuras a una lista y recorre la lista llamando a un metodo de las figuras,además :

```c#
using System;
using System.Collections.Generic;
namespace figuras01_01
{
    class Vector2d
    {
        public int x, y;
        public Vector2d(int x, int y)
        {
            this.x=x; this.y=y;
        }
        public override string ToString()
        {
            return String.Format("{0},{1}", x, y);
        }
    }
    abstract class Figura
    {
        public Vector2d position;
        public string fill ,border;

        public Figura():this( new Vector2d(100, 100))
        {
        
        }
        public Figura(Vector2d pos)
        {
            position= pos;
            border= "black";
        }

        public abstract void Dibuja();

    }

    class Circulo : Figura
    {
     private int radio;
     public Circulo(Vector2d pos, int radio):base(pos)
     {
         this.radio= radio;
     }
     public Circulo ():base()
     {
         this.radio= 10;
     }
     public override void Dibuja() 
     {
         fill="green";
         Console.WriteLine("Se dibuja un circulo en {0} de color {1}", position, fill);
     }
    }
 
    class Rectangulo : Figura
    {
     
     public Rectangulo(Vector2d pos):base(pos)
     {
         
     }
     public Rectangulo ():base()
     {
        
     }

     public override void Dibuja() 
     {
         fill="red";
         Console.WriteLine("Se dibuja un Rectangulo en {0} de color {1}", position, fill);
     }
    }
    class Triangulo:Figura
    {
        private int altura;
        public Triangulo (Vector2d pos,int altura):base(pos)
        {
            this.altura=altura;
        }
        public Triangulo():base()
        {
            this.altura=3;
        }
        public override void Dibuja() 
     {
         fill="orange";
         Console.WriteLine("Se dibuja un triangulo en {0} de color {1}", position, fill);
     }
    }

    class Program
    {
        static void Main(string[] args)
        {
            List<Figura> figuras = new List<Figura>();
            figuras.Add(new Circulo());
            figuras.Add(new Rectangulo(new Vector2d(200,200) ));
            figuras.Add(new Triangulo());
            foreach(Figura f in figuras)
            f.Dibuja();
        }
    }
}

```
___
#### 5.1 Se sobrecarguen los constructores y se acceda a los constructores de la clase base 
```c#

```
___
#### 5.2 Explica para que nos sirve la palabra base

La palabra base es para mandar la información que ocupemos a el constructor de la clase padre o clase base 
___
#### 5.3  Haz el método Dibuja() que sea virtual y redefinelo en solo una de las clases derivadas.
```c#
using System;
using System.Collections.Generic;
namespace figuras01_01
{
     class Vector2d
    {
        public int x, y;
        public Vector2d(int x, int y)
        {
            this.x=x; this.y=y;
        }
        public override string ToString()
        {
            return String.Format("{0},{1}", x, y);
        }
    }
    class Figura
    {
        public Vector2d position;
        public string fill ,border;

        public Figura():this( new Vector2d(100, 100))
        {
        
        }
        public Figura(Vector2d pos)
        {
            position= pos;
            border= "black";
        }

        public virtual void Dibuja()
        {

        }

    }

    class Circulo : Figura
    {
     private int radio;
     public Circulo(Vector2d pos, int radio):base(pos)
     {
         this.radio= radio;
     }
     public Circulo ():base()
     {
         this.radio= 10;
     }
     public override void Dibuja() 
     {
         fill="green";
         Console.WriteLine("Se dibuja un circulo en {0} de color {1}", position, fill);
     }
    }
 
    class Rectangulo : Figura
    {
     
     public Rectangulo(Vector2d pos):base(pos)
     {
         
     }
     public Rectangulo ():base()
     {
        
     }

     public new void Dibuja() 
     {
         fill="blue";
         Console.WriteLine("Se dibuja un rectangulo en {0} de color {1}", position, fill);

     }
    }
    class Triangulo:Figura
    {
        private int altura;
        public Triangulo (Vector2d pos,int altura):base(pos)
        {
            this.altura=altura;
        }
        public Triangulo():base()
        {
            this.altura=3;
        }
        public new void Dibuja() 
     {
         fill="orange";
         Console.WriteLine("Se dibuja un triangulo en {0} de color {1}", position, fill);
     }
    }

    class Program
    {
        static void Main(string[] args)
        {
            List<Figura> figuras = new List<Figura>();
            figuras.Add(new Circulo());
            figuras.Add(new Rectangulo(new Vector2d(200,200) ));
            figuras.Add(new Triangulo());
            foreach(Figura f in figuras)
            f.Dibuja();
        }
    }
}

```



