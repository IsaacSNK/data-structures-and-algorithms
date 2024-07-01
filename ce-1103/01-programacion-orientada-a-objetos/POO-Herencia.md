# **Herencia**
-Reutilización de codigo
-Clase en jerarquía:
Estudiante ---> Ciudadano ---> Persona
Carné           Cedula         Nombre
                               Apellido
-Es-un
-Cuando se sube en la jerarquia, se vuelve más genérico
-Cuando se baja en la jerarquia, se vuelve más especializa
-Solo un padre, si hay transitividad:
    A=>B=>C
    A=>C
-La clase padre se llama base
-La clase hija, se llama derivada
```Java
public persona{
    String nombre;
    String apellido;
    protected void decirnombre(){
        Sys.out("Soy" + nombre)
    }
}
persona p1 = new persona();
p1.nombre = "Isaac";
p1.apellido = "Ramirez";
p1.decirnombre();
class ciudadano extends persona{
    String cedula;
    
    void foo(){
        decirnombre();
    }
}
ciudadano c1 = new ciudadano();
//si hacemos c1. apareceran los atributos y metodos de persona y ciudadano (cedula, nombre, apellido, decirnombre() y foo())

class estudiante extends ciudadano{
    String carne;
}

ciudadano c1 = new ciudadano();
c1.nombre = "Pedro";
c1.cedula = 7;
c1.decir nombre();
```
-Override: Cuando se sobreescribe el metodo padre