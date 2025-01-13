# Longest Common Prefix

``` JAVASCRIPT
/**
 * @param {string[]} strs
 * @return {string}
 */
var longestCommonPrefix = function(strs) {
    let prefix = strs[0]
    if (strs.length === 0) return 'prefix'

    for(let i = 0; i < strs.length; i++) {
        while(strs[i].indexOf(prefix) != 0) {
            prefix = prefix.substring(0, prefix.length - 1)
        }
    }

    return prefix
};
```

**Explicación:**

1. **Inicializar el prefijo común:**
    - La variable `prefix` se inicializa con la primera cadena del arreglo (`strs[0]`).
    - Esto supone que inicialmente, el prefijo común más largo puede ser toda la primera cadena.
2. **Caso especial - Arreglo vacío:**
    - Si el arreglo `strs` está vacío (`strs.length === 0`), se retorna directamente `'prefix'`. Este comportamiento parece ser un error del código, ya que debería retornar una cadena vacía (`""`) según el enunciado estándar del problema.
3. **Iteración sobre el arreglo:**
    - Se recorre el arreglo `strs` desde la primera hasta la última cadena.
    - Para cada cadena en el arreglo (`strs[i]`), se verifica si la cadena comienza con el prefijo actual (`prefix`).
4. **Ajustar el prefijo:**
    - Si la cadena actual (`strs[i]`) no comienza con el prefijo (`strs[i].indexOf(prefix) != 0`), significa que el prefijo actual es demasiado largo.
    - En ese caso, se reduce el prefijo eliminando el último carácter (`prefix.substring(0, prefix.length - 1)`).
    - Este proceso se repite en un bucle `while` hasta que la cadena actual comience con el prefijo ajustado o el prefijo quede vacío.
5. **Retorno del prefijo:**
    - Una vez procesadas todas las cadenas, la variable `prefix` contendrá el prefijo común más largo.
    - Si no hay ningún prefijo común, `prefix` será una cadena vacía (`""`).