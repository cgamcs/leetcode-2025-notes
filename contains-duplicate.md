# Contains Duplicate

``` JAVASCRIPT
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var containsDuplicate = function(nums) {
    const seen = new Set() // Se inicializa un conjunto vació para almacenar los números vistos

    for (const num of nums) { // Iteramos sobre cada n´mero en el arreglo 'nums'
        if (seen.has(num)) { // Si el número ya está en el conjunto, hay un duplicado
            return true // Retornamos 'true' si es así
        }

        seen.add(num) // Si no está en el conjunto lo añadimos
    }
    return false // Si terminamos el buble sin encontrar duplicados, retornamos 'false'
};
```

**Explicación:**

- **Uso de un conjunto (`Set`):**
    - Un conjunto es una estructura de datos que almacena elementos únicos. Esto significa que no permite valores duplicados.
    - El acceso a los elementos en un conjunto (`add`, `has`) tiene una complejidad promedio de O(1), lo que lo hace ideal para este problema.
        
        O(1)O(1)
        
- **Bucle sobre el arreglo `nums`:**
    - Se recorre cada número (`num`) en el arreglo `nums`:
        - Si el número ya existe en el conjunto (`seen.has(num)`), significa que se ha encontrado un duplicado y se retorna `true`.
        - Si no existe en el conjunto, se añade a este (`seen.add(num)`).
- **Retorno al final:**
    - Si el bucle termina sin encontrar ningún duplicado, significa que todos los números son únicos, y se retorna `false`.