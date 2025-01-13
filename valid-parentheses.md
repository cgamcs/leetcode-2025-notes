# Valid Parentheses

``` JAVASCRIPT
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
    const mappings = new Map()

    mappings.set('(', ')')
    mappings.set('{', '}')
    mappings.set('[', ']')

    const stack = []

    for(let i = 0; i < s.length; i++) {
        if(mappings.has(s[i])) {
            stack.push(mappings.get(s[i]))
        } else if (stack.pop() !== s[i]) {
            return false
        }
    }

    return stack.length === 0
};
```

**Explicación:**

- **Mapeo de pares de apertura y cierre:**
    - Se crea un `Map` para almacenar los pares de paréntesis, llaves y corchetes.
    - Las claves son los caracteres de apertura (`(`, `{`, `[`), y los valores son los de cierre (`)`, `}`, `]`).
    - Esto permite determinar fácilmente el cierre correspondiente para un carácter de apertura.
- **Uso de la pila (`stack`):**
    - La pila es utilizada para realizar un seguimiento de los paréntesis de apertura y los cierres esperados.
    - Cada vez que se encuentra un carácter de apertura, se agrega su correspondiente cierre (según el `Map`) a la pila.
- **Iteración sobre la cadena:**
    - Para cada carácter `s[i]`:
        - **Si es un carácter de apertura (`(`, `{`, `[`):**
            - Agregamos el cierre correspondiente a la pila.
        - **Si es un carácter de cierre (`)`, `}`, `]`):**
            - Se elimina el último elemento de la pila (`stack.pop()`), que representa el cierre esperado.
            - Si este no coincide con el carácter actual, la cadena es inválida y se retorna `false`.
- **Validación final:**
    - Al final del bucle, si la pila está vacía (`stack.length === 0`), significa que todos los caracteres de apertura tuvieron un cierre correspondiente y en el orden correcto.
    - Si la pila no está vacía, hay paréntesis de apertura sin cerrar, y la cadena es inválida.