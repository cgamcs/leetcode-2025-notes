# Valid Anagram

``` JAVASCRIPT
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isAnagram = function(s, t) {
    if (s.length !== t.length) { // Si las longitudes son diferentes, no pueden ser anagramas
        return false
    }

    const count = new Array(26).fill(0) // Array para contar la frecuencia de cada letra (a-z)

    for (let i = 0; i < s.length; i++) { // Iteramos sobre cada carácter de las cadenas
        count[s.charCodeAt(i) - 'a'.charCodeAt(0)]++ // Incrementamos el contador para la letra de 's'
        count[t.charCodeAt(i) - 'a'.charCodeAt(0)]-- // Decrementamos el contador para la letra de 't'
    }

    return count.every(val => val === 0) // Verificamos que todos los contadores sean 0
};
```

**Explicación:**

- **Comprobar longitudes:**
    - Si las cadenas `s` y `t` no tienen la misma longitud, **no pueden ser anagramas**, ya que el número total de caracteres sería diferente.
    - Si las longitudes son diferentes, se retorna `false` de inmediato.
- **Inicializar el arreglo `count`:**
    - Se crea un arreglo `count` con 26 posiciones, inicializado en 0. Este arreglo representa las 26 letras del alfabeto inglés (`a-z`).
    - La posición de cada letra en el arreglo se calcula utilizando el valor Unicode de los caracteres. Por ejemplo:
        - `'a'.charCodeAt(0)` devuelve 97, `'b'.charCodeAt(0)` devuelve 98, etc.
        - Para mapear `'a'` a la posición `0`, se resta el código de `'a'`: `charCodeAt(i) - 'a'.charCodeAt(0)`.
- **Contar las frecuencias:**
    - Se itera sobre las cadenas `s` y `t` al mismo tiempo:
        - Para cada carácter en `s`, se incrementa el contador correspondiente en `count`.
        - Para cada carácter en `t`, se decrementa el contador correspondiente en `count`.
    - Al final del bucle:
        - Si `s` y `t` son anagramas, todos los contadores en `count` serán 0, porque los incrementos y decrementos se habrán cancelado.
- **Verificar el arreglo `count`:**
    - Se utiliza el método `every` para verificar que cada valor en `count` sea 0.
    - Si todos los valores son 0, significa que las dos cadenas tienen las mismas letras con las mismas frecuencias, y se retorna `true`.
    - Si algún valor no es 0, se retorna `false`.