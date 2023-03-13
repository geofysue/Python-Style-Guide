# Python-Style-Guide
*Style guide based on Python Enhanced Proposals (PEP).*

Como señala el autor de las guías de estilo originales, Guido van Rossum, el código se lee mucho más a menudo de lo que se escribe. Ante todo, cualquier guía de estilo de Python debe tener como base los enunciados de Tim Peters, conocidos como "El Zen de Python". A saber:

- Lo bonito es mejor que lo feo.

- Lo explícito es mejor que lo implícito.

- Lo simple es mejor que lo complejo.

- Lo complejo es mejor que lo complicado.

- Plano es mejor que anidado.

- Espaciado (*sparse*) es mejor que denso.

- La legibilidad cuenta.

- Los casos especiales no son tan especiales como para romper las reglas.

- Aunque lo práctico gana a la pureza.

- Los errores nunca deben pasar en silencio.

- A menos que se silencien explícitamente.

- Ante la ambigüedad, rechaza la tentación de adivinar.

- Debe haber una -y preferiblemente sólo una- forma obvia de hacerlo.

- Aunque esa manera puede no ser obvia al principio, a menos que seas holandés.

- Ahora es mejor que nunca.

- Aunque a menudo "nunca" es mejor que "ahora mismo".

- Si la implementación es difícil de explicar, es una mala idea.

- Si la implementación es fácil de explicar, puede ser una buena idea.

- Los *namespaces* son una gran idea: ¡hagamos más!

Lo ideal sería ser consistente con la guía de estilo propuesta. Sin embargo, a veces hay que saber cuando ser inconsistente. Dicho esto, comencemos.

## Formato

### Sangría o indentación, *indentation*
Se usarán cuatro espacios por cada nivel de sangría. Aunque esto es opcional para líneas de continuación. 

Las líneas de continuación deben alinearse con los elementos que las delimitan.

```python
eggs = long_function_name(var_one, var_two,
                          var_thre, var_four)
```

Se añadirán cuatro espacios (un nivel extra de indentación) para distinguir los argumentos del resto.

```python
def long_function_name(var_one,var_two,
        var_three, var_four, var_five,
        var_six, var_seven):
    print(var_one)
    print(var_two)
```

Lo siguiente es incorrecto:

```python
# Incorrecto:
eggs = long_function_name(var_one, var_two,
    var_thre, var_four)
```

En el caso de las sentencias ``if`` que necesiten expresarse en varias líneas, es útil darse cuenta que la combinación de una palabra clave de dos caracteres (como ``if``), junto con un espacio y un paréntesis, crea de forma natural un indentado de cuatro espacios. Esto puede generar un conflicto visual con el bloque de código indentado anidado dentro de la sentencia ``if``. Hay varias maneras de solucionarlo, pero tampoco es necesario.

```python
# Sin indentación extra.
if (long_condition_one and
    long_condition_two):
    do_something()

# Añadir un comentario para generar distinción.
if (long_condition_one and
    long_condition_two):
    # Comentario sobre las condiciones para distinguir
    do_something()

# Añadir una indentación extra.
if (long_condition_one
        and long_condition_two):
    do_something()
```

### Tabs o espacios
Los espacios son el método preferido para indentación. Solo se deberían usar tabs para ser consistentes con algún código que ya está indentado con tabs, ya que Python desaconseja mezclar tabs y espacios para la sangría.

### Longitud máxima de línea
Se limitan todas las líneas a un máximo de 79 caracteres. Para comentarios y docstrings, 72 caracteres. La manera preferible de concatenar líneas largas es usando la continuación de línea implícita dentro de paréntesis, llaves o corchetes. Esto debe usarse preferentemente a la barra invertida como continuación de línea.

### Dividir la línea antes o después del operador binario
El estilo recomendado durante mucho tiempo fue romper la línea después del operador. Pero los matemáticos siguen la convención opuesta, mejorando la legibilidad en muchos casos. Seguir la tradición matemática resulta en un código más legible.

```python
# Correcto:
# Fácil relacionar los operadores con los operandos
income = (gross_wages
          + taxable_interest
          + (dividends - qualified_dividends)
          - ira_deduction
          - student_loan_interest)
 
# Incorrecto:
# Los operadores están lejos de los operandos
income = (gross_wages +
          taxable_interest +
          (dividends - qualified_dividends) -
          ira_deduction -
          student_loan_interest)
```

### Líneas vacías
Rodea las funciones y las clases con dos líneas en blanco.

Rodea los métodos de dentro de las clases con una línea en blanco.

Pueden usarse líneas extra para separar grupos de funciones relacionadas. Pueden omitirse para separar un conjunto de varias instrucciones de una línea.

Usa líneas vacías en funciones para indicar secciones lógicas.

Es posible usar ``#%%`` para separar celdas de distinto contenido en el código.

### Import
Se hacen siempre al comienzo del archivo, justo después de los comentarios, y antes de las constantes. Las importaciones deben hacerse en líneas distintas. Debe evitarse usar ``from <module> import *``.

```python
# Correcto
import os 
import sys

# Incorrecto
import os, sys

# Correcto
from subprocess import Popen, PIPE
```

Deben agruparse siguiendo el siguiente orden:
1. Librerías estándar.
2. Librerías de terceros.
3. Librerías y aplicaciones locales.

Estos grupos deben separarse con una línea en blanco. 

### Dunders nivel módulo
Los dunders de nivel módulo (``__all__``, ``__version__``, etc.), deben localizarse justo después del docstring, pero antes de las importaciones de librerías, excepto ``from __future__``.

```python
"""This is the example module.

This module does stuff.
"""

from __future__ import barry_as_FLUFL

__all__ = ['a', 'b', 'c']
__version__ = '0.1'
__author__ = 'Cardinal Biggles'

import os
import sys
```

## Espacios en blanco en expresiones
Evita añadir espacios superfluos en las siguientes situaciones:
- Al comienzo y final de paréntesis, llaves y corchetes.
  ```python
  # Correcto:
  spam(ham[1], {eggs: 2})
  
  # Incorrecto:
  spam( ham[ 1 ], { eggs: 2 } )
  ```
- Entre una coma y un paréntesis de cierre.
  ```python
  # Correcto:
  foo = (0,)
  
  # Incorrecto:
  bar = (0, )
  ```
- Antes de comas, dos puntos o punto y coma.
  ```python
  # Correcto:
  if x == 4: print(x, y); x, y = y, x
  
  # Incorrecto:
  if x == 4 : print(x , y) ; x , y = y , x
  ```
- Sin embargo, al crear slices, los dos puntos actúan como un operador binario, y deben tener el mismo número de espacios a uno y otro lado. Cuando un parámetro del slice se omite, también quitamos el espacio.
  ```python
  # Correcto:
  ham[1:9], ham[1:9:3], ham[:9:3], ham[1::3], ham[1:9:]
  ham[lower:upper], ham[lower:upper:], ham[lower::step]
  ham[lower+offset : upper+offset]
  ham[: upper_fn(x) : step_fn(x)], ham[:: step_fn(x)]
  ham[lower + offset : upper + offset]
  
  # Incorrecto:
  ham[lower + offset:upper + offset]
  ham[1: 9], ham[1 :9], ham[1:9 :3]
  ham[lower : : upper]
  ham[ : upper]
  ```
- Más de un espacio para alinear operadores.
  ```python
  # Correcto:
  x = 1
  y = 2
  long_variable = 3
  
  # Incorrecto:
  x             = 1
  y             = 2
  long_variable = 3
  ```
- No usar espacios alrededor de signo ``=`` cuando indica keywords o valores por defecto. Sin embargo, usadlo cuando se combina una anotación de argumento con un valor por defecto
  ```python
  # Correcto:
  def complex(real, imag=0.0):
      return magic(r=real, i=imag)
  
  # Incorrecto:
  def complex(real, imag = 0.0):
      return magic(r = real, i = imag)
      
  # Correcto:
  def munge(sep: AnyStr = None): ...
  def munge(input: AnyStr, sep: AnyStr = None, limit=1000): ...
  
  # Incorrecto:
  def munge(input: AnyStr=None): ...
  def munge(input: AnyStr, limit = 1000): ...
  ```

Algunas recomendaciones más.

```python
# Correcto:
i = i + 1
submitted += 1
x = x*2 - 1
hypot2 = x*x + y*y
c = (a+b) * (a-b)

# Incorrecto:
i=i+1
submitted +=1
x = x * 2 - 1
hypot2 = x * x + y * y
c = (a + b) * (a - b)
```

```python
# Correcto:
def munge(input: AnyStr): ...
def munge() -> PosInt: ...

# Incorrecto:
def munge(input:AnyStr): ...
def munge()->PosInt: ...
```

```python
# Correcto:
if foo == 'blah':
    do_blah_thing()
do_one()
do_two()
do_three()

# Incorrecto:
if foo == 'blah': do_blah_thing()
do_one(); do_two(); do_three()
```

## Comentarios
Es necesario mantener los comentarios actualizados conforme se modifica el código. Si el código es público, lo ideal es hacer los comentarios en inglés.

Los **bloques de comentarios** irán con la misma sangría que el código al que se hace referencia. Cada línea del bloque de comentarios comienza con ``#`` y un espacio, a menos que sea texto indentado dentro del comentario. Los parágrafos se separarán con una línea que contenga un único ``#``, de modo que la línea no se compute.

Los **comentarios inline** deben usarse de manera dispersa. Estos comentarios deben separarse del código con al menos dos espacios. Comienzan con ``#`` y un espacio. No usar comentarios innecesarios.

### *Docstrings*
Lo ideal es escribir docstrings para todos los módulos, funciones, clases y métodos públicos. Estos docstrings se convierten en el atributo especial ``__doc__`` del objeto al que se refieren. Un *package* puede ser comentado en el docstring del archivo ``__init__.py``. Los docstrings se indican con ``"""`` al principio y al final.

Hay dos tipos de docstrings. Los multi-line deben incluir una línea resumen, seguida de una descripción más elaborada. Si es el docstring de una función o método debe además resumir los argumentos y el output..

```python
# One-liner docstring.
def spam(eggs):
    """Multiplica el argumento por dos y devuelve un número."""
    ham = eggs * 2
    return ham

# Multi-line docstrings.
def complex(real=0.0, imag=0.0):
    """Form a complex number.

    Keyword arguments:
    real -- the real part (default 0.0)
    imag -- the imaginary part (default 0.0)
    """
    if imag == 0.0 and real == 0.0:
        return complex_zero
    ...

```

## Poner nombres

Hay distintos estilos a la hora de poner nombres. Algunos comunes son los siguientes:
- ``b``
- ``B``
- ``lowercase``
- ``lower_case_with_underscores``
- ``UPPERCASE``
- ``UPPER_CASE_WITH_UNDERSCORES``
- ``CamelCase``
- ``lowerCamelCase``
- ``Capitalized_Words_With_Underscores``

En los dos primeros casos, evitar usar  "l" (letra ele minúscula), "O" (letra o mayúscula), o "I" (letra i mayúscula).

### Nombres de módulos y paquetes
Deben seguir el estilo ``lowercase`` o ``lower_case_with_underscores``.

### Nombres de clases
Deben usar el estilo ``CamelCase``. Esto también aplica a las excepciones (ya que deben ser clases).

### Nombres de funciones y variables
Deben seguir el estilo ``lowercase`` o ``lower_case_with_underscores``.

### Nombres de constantes
Definidas a nivel de módulo, siguiendo el estilo ``UPPERCASE`` o ``UPPER_CASE_WITH_UNDERSCORES``.

## Anotaciones
### Anotación de variables
```python
# Correcto:

code: int

class Point:
    coords: Tuple[int, int]
    label: str = '<unknown>'
```
```python
# Incorrecto:

code:int  # No space after colon
code : int  # Space before colon

class Test:
    result: int=0  # No spaces around equality sign
```

### Anotación de funciones
```python
def greeting(name: str) -> str:
    return 'Hello ' + name
```

## Recomendaciones
- Comparaciones con *singletons* como ``None`` deben hacerse usando ``is`` o ``is not``, nunca con operadores de igualdad.
- Usa el operador ``is not`` en lugar de ``not ... is``.
  ```python
  # Correcto.
  if foo is not None:
  ```
  ```python
  # Incorrecto.
  if not foo is None:
  ```
- Deriva excepciones a partir de ``Exception``.
- Consistencia con los ``return``.
  ```python
  # Correcto.
  def foo(x):
      if x >= 0:
          return math.sqrt(x)
      else:
          return None
  
  # Incorrecto.
  def foo(x):
      if x >= 0:
          return math.sqrt(x)
  ```
- Usar ``isinstance()`` para comparar el tipo de objeto.
  ```python
  # Correcto:
  if isinstance(obj, int):
  ```
  ```python
  # Incorrecto:
  if type(obj) is type(1):
  ```
- No comparar valores booleanos usando ``True`` y ``False``.
  ```python
  # Correcto:
  if greeting:
  ```
  ```python
  # Incorrecto:
  if greeting == True:
  ```
