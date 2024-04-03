# CODING CHALLENGE

1. Implemente un algoritmo que determine si todos los caracteres de un string son únicos o no.
2. ¿Qué haría si no se permite estructuras de datos adicionales?

## Requerimientos

- Devuelve True o False.
- Ejemplos de inputs y outputs:

“” → True

“AAB” → False

“ABC” → True

- Input de la A - Z solo mayúscula.
- Utiliza ASCII únicamente.

## Solución

```cpp
	boolean[] seen = new boolean (128);
	for(int i = 0; i < input.len; i++){
		int val = input.charAt(i);
		if (seen[val]){
			return false;
		}
		seen[val] = true;
	}
	return true;
}
```

Complejidad→ O(n)

Complejidad espacial → constante, 128
