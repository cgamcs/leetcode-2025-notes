# Roman to Integer

``` JAVASCRIPT
/**
 * @param {string} s
 * @return {number}
 */
var romanToInt = function(s) {
    const symbols = { // Diccionario que mapea los símbolos romanos a sus valores enteros
        'I': 1,
        'V': 5,
        'X': 10,
        'L': 50,
        'C': 100,
        'D': 500,
        'M': 1000
    }

    let total = 0 // Inicializamos el total en 0

    s.split('').forEach((num, i) => { // Dividimos la cadena en un array de caracteres y recorremos cada uno con forEach
        let curr = s[i] // Símbolo actual
        let next = s[i+1] // Símbolo siguiente

        if(symbols[curr] < symbols[next]) { // Comparamos el valor del símbolo actual con el del siguiente
            total -= symbols[curr] // Si el símbolo actual tiene un valor menor que el siguiente, restamos su valor
        } else {
            total += symbols[curr] // Si el símbolo actual tiene un valor mayor o igual, sumamos su valor
        }
    })

    return total // Devolvemos el total acumulado
};
```

**Explicación:**

1. **Tabla de símbolos (`symbols`):**
    - Se define un objeto `symbols` donde cada clave es un símbolo romano y su valor asociado es su equivalente en entero:
        
        ```jsx
        javascript
        Copiar código
        { 'I': 1, 'V': 5, 'X': 10, 'L': 50, 'C': 100, 'D': 500, 'M': 1000 }
        
        ```
        
2. **Variable `total`:**
    - Se inicializa en `0` y se utilizará para acumular el resultado final.
3. **Bucle sobre la cadena `s`:**
    - Se itera sobre cada carácter de la cadena `s` desde el primer símbolo hasta el penúltimo (cuando `s[i + 1]` todavía es válido).
4. **Variables `curr` y `next`:**
    - `curr` es el símbolo actual (`s[i]`).
    - `next` es el símbolo siguiente (`s[i + 1]`).
5. **Regla principal de los números romanos:**
    - Si el valor de `curr` es menor que el valor de `next`, significa que este es un caso especial, y `curr` debe restarse del total:
        
        ```jsx
        javascript
        Copiar código
        if (symbols[curr] < symbols[next]) {
            total -= symbols[curr];
        }
        
        ```
        
        Ejemplo: En "IV", `I (1) < V (5)`, por lo que `I` se resta y obtenemos `-1`.
        
    - Si el valor de `curr` es mayor o igual al de `next`, simplemente se suma al total:
        
        ```jsx
        javascript
        Copiar código
        else {
            total += symbols[curr];
        }
        
        ```
        
        Ejemplo: En "VI", `V (5) > I (1)`, por lo que `V` se suma.
        
6. **Resultado final:**
    - Una vez que el bucle termina, el valor acumulado en `total` es el número entero correspondiente al número romano dado.