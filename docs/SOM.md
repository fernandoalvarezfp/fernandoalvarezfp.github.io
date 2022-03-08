# SOM

## Programación estructurada en PowerShell
El primer paso que debemos realizar en nuestra máquina virtual de W10, es la ejecución del siguiente comando (en una ventana de powershell con permisos de administrador):
``` ps1
Set-ExecutionPolicy Unrestricted
```

### Declaración de variables
``` ps1
$variable = valor
```
Por ejemplo:
``` ps1
#System.Int32
$entero = 3
#System.String
$cadenaDeCaracteres = "Hola" 
```
### Entrada y salida 
Para poder mostrar por pantalla el valor de una variable o de una operación utilizaremos la función:
``` ps1
Write-Host $variable
Write-Host ($operando1 + $operando2)
```
Para poder recibir valores por teclado (y asignarlos a una variable), utilizaremos la función:
``` ps1
$variable = Read-Host "Mensaje"
```
Por ejemplo:
``` ps1
[int]$edad = Read-Host "Por favor, introduzca su edad"
```
!!! tip
    La función ```Read-Host``` devuelve siempre una variable cadena de texto. Si queremos almacenar en nuestra variable un número entero tendremos que declararlo de forma explícita utilizando ```[int]```

### Argumentos de llamada a un script .ps1
Podemos pasarle a nuestro script los valores que queramos como argumentos:
``` ps1
./script.ps1 1 2 3
```
Dentro de nuestro script, podremos recuperar estos valores de la siguiente manera:
``` ps1
$primerNumero = $args[0]
$segundoNumero = $args[1]
$tercerNumero = $args[2]
```

### Operadores de comparación
Estos operadores los utilizaremos tanto en las sentencias condicionales como en los bucles:

**-eq** (equal to):igual a

**-lt** (less than): menos que

**-gt** (greater than): más que

**-ge** (greater than or equal to): mayor o igual a

**-le** (less than or equal to): menor o igual a

**-ne** (not equal to): no es igual a

### Operaciones lógicas

**-and** Permite relacionar varios predicados condicionales. Para que el predicado global sea verdadero, tienen que ser verdaderos todos los predicados relacionados.
``` ps1
if ( ($num1 -gt 5) -and ($num2 -gt 5) )
{
    Write-Host "Los dos números son mayores que 5"
}
```

**-or** Permite relacionar varios predicados condicionales. Para que el predicado global sea verdadero, tiene que ser verdadero, al menos uno de los predicados relacionados.
``` ps1
if ( ($num1 -gt 5) -or ($num2 -gt 5) )
{
    Write-Host "Al menos uno de los dos números son mayores que 5"
}
```

**-not** Permite negar predicados condicionales.
``` ps1
if ( -not($num -gt 5) )
{
    Write-Host "El número no es mayor que 5"
}
```

### Sentencias condicionales

#### IF
```ps1
$a=5

if($a -eq 5)

{

Write-Host "5"

}
```

#### IF-ELSE
```ps1
$a=5

if($a -eq 5)

{

    Write-Host "La variable a tiene asignado el valor 5"

}

else

{

    Write-Host "La variable a no tiene asignado el valor 5"

}
```

#### ELSEIF
```ps1
$a=6

if($a -eq 5)

{

    Write-Host "La variable a tiene asignado el valor 5"

}

elseif($a -eq 6)

{

    Write-Host "La variable a tiene asignado el valor 6"

}

else

{

    Write-Host "La variable a no tiene asignado ni el valor 5 ni el 6"

}
```
#### SWITCH
```ps1
$a=5

switch($a)
{

    5
    {
        Write-Host "La variable a tiene asignado el valor 5"
        break
    }

    6
    {
        Write-Host "La variable a tiene asignado el valor 6"
        break
    }

    7
    {
        Write-Host "La variable a tiene asignado el valor 7"
        break

    }
    default
    {
        Write-Host "La variable a no tiene asignado ni el valor 5 ni el 6 ni el 7"
    }

}
```

### Bucles (Sentencias de repetición)

#### WHILE
``` ps1
$i=1
while($i -le 10)
{
    $i
    $i++
}
```

#### DO-WHILE
``` ps1
$i=1
do{
    $i
    $i++
}while($i -le 10)
```

#### FOR
``` ps1
for($i=1;$i -le 10;$i++)
{
    $i
}
```

#### FOREACH
``` ps1
foreach($i in 1..10)
{
    $i
}
```

### Función random
La función Get-Random nos permite obtener valores aleatorios.

``` ps1
#Obtener un número aleatorio entre 0 y 100
Get-Random -Minimum 0 -Maximum 100
```

``` ps1
#Obtener dos colores aleatorios de la lista
'verde', 'amarillo', 'rojo', 'azul', 'negro', 'blanco' | Get-Random -Count 2
```

``` ps1
#Reorganiza de forma aleatoria toda la lista de colores
'verde', 'amarillo', 'rojo', 'azul', 'negro', 'blanco' | Get-Random -Shuffle
```

### Funciones de cadenas de caracteres
#### Length
Muestra la longitud de una cadena de caracteres
```ps1
$c = 'casa'
$c.length
4
```

#### IndexOf
Muestra la posición de la primera ocurrencia de un carácter dentro de una cadena de texto. En caso de que el carácter no esté dentro de la cadena de texto devuelve -1.
```ps1
$c = 'casa'
$c.indexOf('c')
0
$c.indexOf('s')
2
$c.indexOf('w')
-1
```

#### Replace
Reemplaza una sección de una cadena de caracteres por otra.
```ps1
$c = 'casa'
$c.replace('ca','pa')
pasa
```

#### Insert
Introduce en una posición de una cadena de texto, otra cadena de texto.
```ps1
$c = 'casa'
$c.insert(4.'s')
casas
```

#### Equals 
Evalúa si una cadena de caracteres es igual a otra. Devuelve los valores booleanos True o False.
```ps1
$c = 'casa'
$c1 = 'casa'
$c2 = 'pasa'
$c.equals('casa')
True
$c.equals('pasa')
False
$c.equals($c2)
False
$c.equals($c1)
True
```

#### Split y Substring
Lo veremos en próximos capítulos.

## Ejercicios resueltos

### Contador de 1 a 10 utilizando el bucle WHILE
```ps1
$i = 1
while($i -le 10)
{
    Write-Host($i) 
    $i++
}
```

### Sensor de temperatura con ELSEIF
```ps1
[int]$temp = Read-Host "Por favor, introduzca la temperatura"
if ($temp -le 10)
{
    Write-Host "Frío"
}
elseif ($temp -gt 10 -and $temp -le 18)
{
    Write-Host "Fresquito"
}
elseif ($temp -gt 18 -and $temp -le 24)
{
    Write-Host "Temperatura agradable"
}
else
{
    Write-Host "Calor"
}
```

### Semáforo con SWITCH
```ps1
$color = $args[0]
switch($color)
{
    'verde'
    {
        Write-Host "Pasar"
        break
    }
    'amarillo'
    {
        Write-Host "Precaución"
        break
    }
    'rojo'
    {
        Write-Host "Parar"
        break
    }
    default
    {
        Write-Host "Color inválido"
    }
}
```

### Recorrer una lista utilizando el bucle FOR
```ps1
$frutas = 'fresa', 'manzana', 'platano', 'melon', 'naranja', 'limon'
for ($i=0; $i -lt $frutas.length; $i++)
{
    Write-Host $frutas[$i]
}
```

### Obtener N elementos de una lista de manera aleatoria
```ps1
$frutas = 'fresa', 'manzana', 'platano', 'melon', 'naranja', 'limon'
[int]$numFrutas = Read-Host "¿Cuántas frutas quiere?"
$frutas | Get-Random -Count $numFrutas
```

### Comprobar si una letra está presente en una palabra
```ps1
$palabra = 'casa'
$letra = Read-Host "Por favor, introduzca una letra"
if ($palabra.IndexOf($letra) -ne -1 )
{
    Write-Host "La letra está presente en la palabra"
}
else
{
    Write-Host "La letra NO está presente en la palabra"    
}
```

### Eliminar de una lista las palabras que comienzan por vocal
```ps1
$alumnos = 'Iker', 'Desirée', 'Andrei', 'Pablo', 'Aitor', 'Manuel', 'Mario', 'Daniel', 'Edwar', 'Nicolás'
for ($i=0; $i -lt $alumnos.length; $i++)
{
    $alumno = $alumnos[$i]
    $pl = $alumno[0]
    if ($pl -eq 'a' -or $pl -eq 'e' -or $pl -eq 'i' -or $pl -eq 'o' -or $pl -eq 'u')
    {
        $alumnos[$i] = '----'
    }
}
$alumnos
```

### Mostrar los personajes cuyo nombre y apellido comienzan por la misma letra
```ps1
$personajes = 'Peter Parker', 'Hercule Poirot', 'Stephen Strange', 'Harry Potter', 'Reed Richards', 'Matt Murdock', 'Oliver Twist'
$personaje = ''
$espacio = -1
$primeraLetraNombre = ''

for ($i=0;$i -lt $personajes.length;$i++)
{
	$personaje = $personajes[$i]
	$primeraLetraNombre = $personaje[0]
	for ($j = 0; $j -lt $personaje.length; $j++)
	{
		if ($personaje[$j] -eq ' ')
		{
				$espacio = $j
		}
	}
	if ($primeraLetraNombre -eq $personaje[$espacio + 1])
	{
		Write-Host $personaje
	}
}
```

## Examen 07/03/2022

### **Pregunta 1 -** Escribe un script que reciba 3 argumentos (utiliza $args): Le preguntará al usuari@ su nombre y apellidos y se lo mostrará por pantalla con el siguiente formato: apellido1 apellido2, nombre
```ps1
Write-Host $args[1] $args[2]','$args[0]
```
(Alternativa) Utilizando Read-Host y 3 variables
```ps1
$nombre = Read-Host "Introduzca su nombre"
$apell1 = Read-Host "Introduzca 1er apellido"
$apell2 = Read-Host "Introduzca 2º apellido"
Write-Host $apell1 $apell2', '$nombre
```

### **Pregunta 2 -** Escribe un script que genere un número aleatorio entre 0 y 50. Si el número resultante es 10 20 30 o 40 escribe “¡Has tenido suerte!”
```ps1
$num = Get-Random -Minimum 0 -Maximum 50
if ($num -eq 10 -or $num -eq 20 -or $num -eq 30 -or $num -eq 40)
{
	Write-Host "Has tenido suerte"	
}
```

### **Pregunta 3 -** Escribe un script calculadora en el que declares 2 variables (serán los operandos) y admita un argumento para seleccionar el tipo de operación a realizar mediante la estructura switch. El/la usuari@ puede elegir entre la operación de suma y la de multiplicación.

``` ps1
$op1 = 2
$op2 = 3
$op = $args[0]
switch($op)
{
+
	{
		Write-Host ($op1 + $op2)
		break
	}
*
	{
		Write-Host ($op1 * $op2)
		break
	}
}
```

### **Pregunta 4 -** Escribe un script que muestre los números del 15 al 1(orden descendente) mediante un bucle.
``` ps1
for ($i = 15;$i -gt 0;$i--)
{
	Write-Host $i
}
```
### **Pregunta 5 -** Script que muestre únicamente las palabras en plural (terminan por la letra s) de la siguiente lista: casa, aceitunas, verdura, futbolista, pilas, cosas
``` ps1
$lista = 'casa', 'aceitunas', 'verdura', 'futbolista', 'pilas', 'cosas'
for($i = 0; $i -lt $lista.length; $i++)
{
	$palabra = $lista[$i]
	if ($palabra[$palabra.length-1] -eq 's')
	{
		Write-Host $palabra	
	}
}
```
