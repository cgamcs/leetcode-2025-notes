``` JAVASCRIPT
/**
 * @param {string} s
 * @return {number}
 */
var romanToInt = function(s) {
    const symbols = { 'I': 1, 'V': 5, 'X': 10, 'L': 50, 'C': 100, 'D': 500, 'M': 1000 }

    let total = 0

    s.split('').forEach((num, i) => {
        let curr = s[i]
        let next = s[i+1]

        if(symbols[curr] < symbols[next]) {
            total -= symbols[curr]
        } else {
            total += symbols[curr]
        }
    })

    return total
};
```

La solución para el problema Roman to Integer convierte un número en formato romano a un número entero utilizando un enfoque basado en iteración y comparación de valores.

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