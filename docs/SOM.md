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
