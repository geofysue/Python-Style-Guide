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

## Sangría o indentación, *indentation*
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

