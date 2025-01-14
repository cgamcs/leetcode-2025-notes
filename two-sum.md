# Two Sum

``` JAVASCRIPT
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    const hashMap = {}  // Creamos un objeto (hash map) para almacenar los números que hemos visto y sus índices

    for(let i = 0; i < nums.length; i++) { // Recorremos el array 'nums'
        const currentNum = nums[i] // Obtenemos el número actual
        const numToFind = target - currentNum // Calculamos el número necesario para completar el target

        // Verificamos si 'numToFind' ya está en el hash map
        if(hashMap[numToFind] >= 0) { // `>= 0` asegura que tenemos un índice válido
            return [hashMap[numToFind], i] // Si lo encontramos, devolvemos los índices del número actual y de 'numToFind'
        } else {
            hashMap[currentNum] = i // Si no encontramos 'numToFind', guardamos el número actual y su índice en el hash map
        }
    }

    // Si no se encuentran dos números que sumen el target, no se devuelve nada. Esto asume que siempre habrá solución
};
```

**Explicación:**

- **Declaración de variables:**
    - `nums` es el arreglo que contiene los números: `[2, 7, 11, 15]`.
    - `target` es el valor objetivo que queremos obtener al sumar dos números: `9`.
    - `hashMap` es un objeto que se utiliza como un diccionario para almacenar los números que ya hemos visitado junto con sus índices.
- **Bucle `for`:**
    - Recorremos el arreglo `nums` utilizando un índice `i`.
- **Cálculo del número necesario:**
    - `currentNum` es el número actual del arreglo: `nums[i]`.
    - `numToFind` es el número que necesitamos para que, sumado a `currentNum`, dé como resultado el `target`. Se calcula como:
    numToFind=target−currentNum
        
        numToFind=target−currentNum\text{numToFind} = \text{target} - \text{currentNum}
        
- **Verificación en el `hashMap`:**
    - Se verifica si `numToFind` ya existe como una clave en el `hashMap`:
        - Si existe, significa que previamente encontramos un número que, sumado al número actual (`currentNum`), cumple con el objetivo.
        - Se retorna un arreglo con los índices: `[hashMap[numToFind], i]`.
- **Actualización del `hashMap`:**
    - Si `numToFind` no está en el `hashMap`, agregamos el número actual (`currentNum`) como clave, y su índice (`i`) como valor: `hashMap[currentNum] = i;`