[<-- Volver a inicio](https://github.com/ACBC-DEV/halloweenDev)

<details>
<summary>📝 Instrucciones</summary>
Estás atrapado en una pesadilla en la que Freddy Krueger te persigue 😭. El sueño está representado por un laberinto de celdas, donde cada celda tiene un valor numérico que indica el nivel de peligro de esa parte del sueño.

Debes encontrar el camino más seguro (es decir, el que tenga el menor valor total de peligro) desde la esquina superior izquierda hasta la esquina inferior derecha de la matriz.

En este desafío, solo puedes moverte hacia la derecha o hacia abajo (no puedes retroceder ni moverte en diagonal) y debes calcular el nivel total de peligro del camino más seguro.

La pesadilla está representada por una matriz dream de tamaño n x m donde cada celda es un número positivo que representa el nivel de peligro de esa celda en el sueño.

Y tienes que devolver el valor total de peligro del camino más seguro de la esquina superior izquierda (posición [0][0]) a la esquina inferior derecha (posición [n-1][m-1]).

```typescript

const dream = [
  [1, 3, 1],
  [1, 5, 1],
  [4, 2, 1]
]
const bestPath = findSafestPath(dream)  // Devuelve 7
// El mejor camino es:
// [0, 0] -> 1
// [0, 1] -> 3
// [0, 2] -> 1
// [1, 2] -> 1
// [1, 3] -> 1

// 1 -> 3 -> 1 -> 1 -> 1 = 7
```


</details>

<br>

```typescript
function findSafestPath(dream) {
  const n = dream.length;
  const m = dream[0].length;
  const dp = new Array(n).fill(0).map(() => new Array(m).fill(0));

  // Llenar la primera fila y la primera columna
  dp[0][0] = dream[0][0];
  for (let i = 1; i < n; i++) {
    dp[i][0] = dp[i-1][0] + dream[i][0];
  }
  for (let j = 1; j < m; j++) {
    dp[0][j] = dp[0][j-1] + dream[0][j];
  }

  // Llenar el resto de la matriz dp
  for (let i = 1; i < n; i++) {
    for (let j = 1; j < m; j++) {
      dp[i][j] = Math.min(dp[i-1][j], dp[i][j-1]) + dream[i][j];
    }
  }

  return dp[n-1][m-1];
}
```

> Caramelos: 310