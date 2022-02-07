![](Img/Cabecera_Logo.png)
![](Img/Maven.png)

# Maven 

## ¿Qué es Maven?

Maven es una herramienta open-source, que se creó en 2001 con el objetivo de simplificar los procesos de build (compilar y generar ejecutables a partir del código fuente).


## ¿Cómo crear un proyecto maven?
Hay dos tipos de crear un proyecto maven, uno a través de del programa que vamos a utilizar y otro a través de la terminal. En mi caso explicaré como se hace a través de la terminal. 

1. Entrar en el github.

3. Hacer **clic** en el **+** de la esquina superior derecha, junto a su avatar o icono de identificación

2. **Seleccionar New repository** .

4. **Crear** un **repositorio vacio**. Poner un nombre, descripción al repositorio y poner el repositorio que sea publico. 

5. Clicar **Create repository**

6. Abrir la terminal.

 _A través de los comandos seleccionaremos donde queremos crear el proyecto._

- `ls` lee los archivos que están en la carpeta 
- `cd nombreCarpeta` entra en la carpeta que has seleccionado 
- `cd` va a una carpeta atrás
- `mkdir nombreCarpetaNueva`  crea una carpeta del nombre que le has dado 
- `clear` limpiar la pantalla 

7. **Crear** una **nueva carpeta**.

    ```mkdir nombreDeCarpeta```

8.  Entrar en la carpeta que hemos creado. 

    ```cd nombreDeCarpeta```

9. Copiar la siguiente instrucción, hay que tener en cuenta que ha que modificar cosas para poderlo dejar como más te convenga. 

```
mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.4 -DinteractiveMode=false
```

En la parte `DgroupId=` hay que sustituir com.mycompany.app por el nombre de la empresa en la que estamos trabajando o la empresa la cual va dirigida. 
Ej:

```
DgroupId= NombreEmpresa
```

Por otra parte en la parte de `DarchetypeArtifactId=` hay que poner el nombre de la aplicación.
Ej:

```
DarchetypeArtifactId= nombreApp
```

_Archetyp_  es un complemento que contiene una colección de objetivos con un propósito general. Por lo que crea un proyecto simple basado en un arquetipo maven-archetype-quickstart .

En este momento ya se a creado un nuevo directorio. 

`
    CarpetaProyecto

        | src
            | main
                |java
                    | edu
                        | nombreEmpresa
                            | app
                                | App.java

            | test
                | java
                    | com
                        | mycompany
                            | app
                                | AppTest.java

        |target
            |classes
                | edu
                    | nombreEmpresa
                        | App.class

            | test-classes
                |edu
                    | nombreEmpresa
                        AppTest.class
    | pom.xml`
`
El archovo **_src_** es donde estará el código.

El archivo **_pom.xml_** es donde estaá la configuración.

El archivo **_main_** dentro de la carpeta els **_nombreEmpresa_** hay que crear una carpeta llamada **_domain_** dode crearemos documentos para el codigo de la aplicación. **IMPORANTE** el nombre del nuevo archivo tine que empezar en mayúsculas.  
Ej :

`
CarpetaProyecto

    | src
        | main
            |java
                | edu
                    | nombreEmpresa
                        | domanin* 
                            | TarjetaUsusario.java*
                        | app
                            | App.java

        | test
            | java
                | com
                    | mycompany
                        | app
                            | AppTest.java

    |target
        |classes
            | edu
                | nombreEmpresa
                    | App.class

        | test-classes
            |edu
                | nombreEmpresa
                    |AppTest.class
    | pom.xml
`

10. Abrir el archivo `pom.xml`  hay que comprobar:
- Tiene que poner el nombre de la empresa.
```
<groupId>nombreEmpresa</groupId>
``` 

- Tiene que poner el nombre de la aplicación.
``` 
<artifactId>calculadora</artifactId>
```

- Poner el link del repositorio.
```
<url>http://www.example.com</url>
```

- Especificar la versión SDK. 
```
<properties>
	<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
	<maven.compiler.source>11</maven.compiler.source>
	<maven.compiler.target>11</maven.compiler.target>
</properties>
```

11. En el mismo documento ( _pom.xml_ ) hay que añadir una sección de configuración pata generar la aplicación. 

Esa parte va después de 
`<plugin>
 	<artifactId>maven-jar-plugin</artifactId>
 	<version>3.0.2</version>`
```
<!-- Seccion configuration para generar un jar ejecutable de la app -->
          <configuration>
            <archive>
              <manifest>
                <addClasspath>true</addClasspath>
                <mainClass>edu.elsmancs.gildedrose.App</mainClass>
              </manifest>
              <manifestEntries>
                <url>${project.url}</url>
              </manifestEntries>
            </archive>
          </configuration>
```
12. Cambiar `<mainClass>… </mainClass>`, la cual tendremos que poner la ruta del archivo donde esta el archivo _App.java_ . 

Ej:

```
<mainClass>edu.elsmancs.App</mainClass> 
```

# Bibliografía

- [maven.apache](https://maven.apache.org/)
- [Blog javiergarzas](https://www.javiergarzas.com/2014/06/maven-en-10-min.html)
- [github.com(dEzequiel)](https://github.com/dEzequiel/maven-notebook)

