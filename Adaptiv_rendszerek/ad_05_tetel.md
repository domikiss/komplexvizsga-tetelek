# 5. Tétel

AX~B probléma megoldása (legkisebb négyzetek, totál legkisebb négyzetek (TLS) és STLS becslés)

---

## Legkisebb négyzetek

A mért kimenetek ($`y_i`$) és a mért bemeneti vektorok ($`\mathbf{x}_i`$) között a következő, paraméterekben ($\vartheta$) lineáris összefüggést feltételezzük:

```math
y_i \sim \hat y_i = \mathbf{x}_i^T \vartheta
```

A cél a mért kimenet és a mért bemenet alapján modellezett (becsült) kimenet közötti négyzetes hiba minimalizálása:
```math
S(\vartheta) = \sum_{i=1}^{N} \left( y_i - \mathbf{x}_i^T \vartheta \right)^2
```

```math
\hat \vartheta = \arg \min_\vartheta S(\vartheta)
```

A mérési minta kimeneti elemeit rendezzük egy $\mathbf{y}$ vektorba, a mért bemeneti vektorokat pedig egy $\mathbf{X}$ mátrixba:
```math
\mathbf{y} = \begin{bmatrix} y_1,\dots,y_n \end{bmatrix} ^T
```
```math
\mathbf{X} = \begin{bmatrix} \mathbf{x}_1,\dots,\mathbf{x}_n \end{bmatrix} ^T
```
Ekkor a be- és kimenetek közötti összefüggés és a négyzetes hibaösszeg a következő alakban írható:

```math
\mathbf{y} \sim \hat{\mathbf{y}}_i = \mathbf{X} \vartheta
```
```math
S = \left( \mathbf{y} - \mathbf{X} \vartheta \right)^T \left( \mathbf{y} - \mathbf{X} \vartheta \right) =
```
```math
= \mathbf{y}^T \mathbf{y} - \mathbf{y}^T \mathbf{X} \vartheta - \vartheta^T \mathbf{X}^T \mathbf{y} + \vartheta^T \mathbf{X}^T \mathbf{X} \vartheta
```

A minimum szükséges feltétele (ami a kvadratikus célfüggvény miatt elégséges is):
```math
\frac{\partial S}{\partial \vartheta} = -2\mathbf{X}^T \mathbf{y} + 2 \mathbf{X}^T \mathbf{X} \hat \vartheta_{LS} = 0
```
```math
 \hat \vartheta_{LS} = \left( \mathbf{X}^T \mathbf{X} \right)^{-1} \mathbf{X}^T \mathbf{y}
```

Vegyük észre, hogy a $`\left( \mathbf{X}^T \mathbf{X} \right)^{-1}\mathbf{X}^T`$ mátrix az $\mathbf{X}$ mátrix Moore-Penrose-féle pszeudoinverze.


Abban az esetben, ha a mérési adatok közül csak az $\mathbf{y}$-t tekintjük valószínűségi változónak (pl. determinisztikus rendszer kimenetére kerülő zaj miatt), akkor a be- és kimenet közötti összefüggés a következő:

```math
\mathbf{y} = \mathbf{X} \vartheta + \xi
```

Ekkor a becslés tulajdonságai a következők:

1. Lineáris a becslés: $`\hat\vartheta = \mathbf{Ly}`$, ahol $`\mathbf{L} = \left( \mathbf{X}^T \mathbf{X} \right)^{-1} \mathbf{X}^T`$

2. Torzítatlan: $`E \left( \hat\vartheta \right) = \vartheta`$

3. A becslés kovarianciája: $` \text{Cov} \bigl( \hat{\vartheta} \bigr) = \sigma^2 \left( \mathbf{X}^T \mathbf{X} \right)^{-1}`$, ahol $\sigma^2$ az $\xi$ valószínűségi változó (a zaj) varianciája. Ezt azonban nem ismerjük, ezért becsülni kell.

4. A zaj varianciájára torzítatlan becslés adható a minimális négyzetes hibaösszeg segítségével ($N$ a mérési pontok száma, $m$ a paraméterek száma):
```math
\hat\sigma^2 = \frac{S\left( \hat\vartheta \right)}{N-m}
```   

5. Megfelelő gerjesztés esetén a $\hat\vartheta$ becslés konzisztens is, mert ilyenkor $`\left( \mathbf{X}^T \mathbf{X} \right)^{-1}`$ főátlóbeli elemei nullához tartanak.

6. Az LS becslő a lineáris becslők közül a leghatásosabb.



## Totál legkisebb négyzetek

Nincs egyértelmű bemenet és kimenet, illetve mind a bemenetet, mind a kimenetet zajosan tudjuk mérni (és ezek még korreláltak is lehetnek). Explicit modell helyett implicit modellel dolgozunk.

Azt feltételezzük, hogy a mérések normális eloszlásúak: Maximum likelihood módszerrel határozzuk meg a $\vartheta$ paramétervektor becslését. Egy egyenlőség típusú korlátozás melletti optimalizálási feladatot kapunk, ahol a korlátozás maga az implicit modell.

A Lagrange-függvényt a log-likelihood függvény alapján írjuk fel, és a $\vartheta$ szerinti derivált zérushelyének keresése egy általánosított sajátérték-problémához vezet. Ennek megoldása után a legkisebb sajátértékhez tartozó sajátvektor lesz a becsült paramétervektor.


## STLS

Erről nem volt szó a mi időnkben...
