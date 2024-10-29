[<-- Volver a inicio](https://github.com/ACBC-DEV/halloweenDev)

<details>
<summary>📝 Instrucciones</summary>
Durante la noche de Halloween 🎃, una bruja 🧙‍♀️ está preparando una mezcla mágica. Tiene una lista de pociones, cada una con un poder asociado, y quiere combinar dos de ellas para obtener un poder total específico.

Dada una lista de enteros donde cada número representa el poder de una poción 🧪 y un número entero que representa el poder objetivo, debes encontrar el índice de las dos primeras pociones que sumen exactamente el poder objetivo.

Por ejemplo:
```typescript
const potions = [4, 5, 6, 2]
const goal = 8

createMagicPotion(potions, goal) // [2, 3]
```
Si no se encuentra ninguna combinación, devuelve undefined
```typescript
const potions = [1, 2, 3, 4]
const goal = 9

createMagicPotion(potions, goal) // undefined
```
En el caso que haya más de una combinación posible, selecciona la combinación cuya segunda poción aparezca primero en la lista.
```typescript
const potions = [1, 2, 3, 4]
const goal = 5

createMagicPotion(potions, goal) // [1, 2]
```

// también podría ser [0, 3] pero hay una combinación antes
</details>

<br>

```typescript
function createMagicPotion(potions, target) {
  const map=new Map()
  for (let i = 0; i < potions.length; i++) {
    const neededPower=target-potions[i]
    if(map.has(neededPower)){
      return [map.get(neededPower),i]
    }
    map.set(potions[i],i)
  }

  return undefined
}
```

> Caramelos: 460