# 3. Tétel

Becslési módszerekkel szemben támasztott elvárások, statisztikai döntéselmélet, identifikációs paradigmák

---

A becslési módszerek lényege, hogy egy adott minta (mérések) alapján vonjunk le következtetéseket azzal a valószínűségi eloszlással kapcsolatban, amelyből a minta származik.

## A becslési feladatok típusai és alapfogalmai

### A becslési feladatok típusai

- __Pontbecslés__:  
  Egy adott $\vartheta$ paraméter(vektor) legvalószínűbb értékének meghatározása.


- __Konfidenciaintervallum-becslés__:  
  Annak meghatározása, hogy ha van egy $\hat\vartheta$ pontbecslésünk, akkor az mennyire megbízható. A feladat az, hogy a becslés eredménye ($\hat\vartheta$) és egy megadott valószínűség (konfidencia, pl. 95%) alapján meghatározzuk, hogy a valós paraméter az adott valószínűséggel milyen két érték közötti intervallumba esik.
  

- __Hipotézisvizsgálat (struktúrabecslés)__:  
  A feladat egy adott hipotézisről eldönteni, hogy elutasítsuk-e. Kell egy nullhipotézis és egy alternatív hipotézis. Stuktúrabecslés esetén azt kell eldönteni, hogy két különböző struktúrájú (különböző számú paraméterrel rendelkező) modell statisztikailag szignifikánsan különbözik-e egy adott minta (mérés) ismeretében. Másképpen fogalmazva: egy adott paraméter jelenléte a modellben statisztikailag szignifikánsan más eredményt ad-e, mint ha nincs jelen (értéke nulla). Ilyenkor a nullhipotézis az, hogy nincs jelentősége az adott paraméternek, vagyis hogy a 0 paraméterérték és a becsült paraméterérték statisztikailag nem különbözik szignifikánsan. A hipotézisvizsgálat eredménye, hogy elvessük-e a nullhipotézist, vagy nem.


### A pontbecslés alapfogalmai

Egy adott statisztika (paraméterbecslési módszer) egy függvény, amely a mérési mintához rendel egy becsült paramétervektort. A függvény bemenete ugyanabból a valószínűségi eloszlásból vett $n$ darab minta vektora (másképpen fogalmazva: $n$ db ugyanolyan típusú és paraméterű valószínűségi változó), kimenete pedig a vizsgált eloszlás $m$ darab paraméterét tartalmazó vektor:

```math
\vec{\vartheta} \approx \hat{\vec{\vartheta}} = d(\vec{\xi})
```

ahol $\vec{\vartheta}$ a tényleges paramétervektor, $\hat{\vec{\vartheta}}$ a becsült paramétervektor, $\vec{\xi}$ a mérési minta (ugyanannak a valószínűségi eloszlásnak $n$ db független megvalósulása), $d(\cdot)$ pedig a becslési módszer, másnéven statisztika.

A statisztika célja, hogy minimalizálja a __rizikófüggvényt__ azaz a becsült paramétereknek a tényleges paraméterektől való eltérésének várható értékét:

```math
R = E \biggl( W \!\left(\vec{\vartheta}, d(\vec{\xi}) \right) \biggr)
```
ahol $W(\cdot,\cdot)$ egy távolságfüggvény (metrika).

A későbbiekben a vektorjelölést elhagyjuk, $\vartheta$ mindig paramétervektort fog jelenteni, $\xi$ pedig a minták vektorát.


### Pontbecslési módszerekkel szemben támasztott elvárások

#### 1. Torzítatlanság

Azt jelenti, hogy a becsült paraméter várható értéke megegyezik a tényleges paraméterrel:

```math
E \! \left( \hat\vartheta_n \right) = \vartheta
``````

#### 2. Hatásosság

Egy statisztika annál hatásosabb, minél kisebb a becsült paraméterek szórása. Ha van $s$ darab különféle statisztikánk, akkor az $i$-edik statisztika hatásossága a következőképpen fejezhető ki:

```math
\eta_i = \dfrac{\inf_{i \in \{1,\dots,s\}} D(d_i)}{D(d_i)}
```

Annak eldöntésére, hogy egy adott torzítatlan statisztika maximálisan hatásos-e ($`\eta_i = 1`$), a Cramer-Rao egyenlőtlenség ad lehetőséget:

```math
\text{Cov} \! \left( \hat\vartheta \right) \geq \mathbf{M}^{-1}
```

Ez az összefüggés a becslők varianciájának alsó korlátját fejezi ki, jelentése az, hogy 
```math
\text{Cov} \! \left( \hat\vartheta \right) - \mathbf{M}^{-1} \geq 0
```
vagyis a $`\text{Cov} \! \left( \hat\vartheta \right) - \mathbf{M}^{-1}`$ mátrix pozitív szemidefinit, ahol $`\text{Cov} \! \left( \hat\vartheta \right)`$ a vizsgált becslő kovarianciamátrixa, $\mathbf{M}^{-1}$ pedig a Fisher-féle információs mátrix:
```math
\mathbf{M} = E \left( \left[ \frac{\partial \ln f(y|\vartheta)}{\partial \vartheta} \right] \left[ \frac{\partial \ln f(y|\vartheta)}{\partial \vartheta} \right]^T \right)
```
ahol $f(y|\vartheta)$ a likelihood-függvény, ami az $y$ mért kimenet $\theta$ paramétertől függő valószínűségi sűrűségfüggvénye. 

Abban az esetben, ha a fenti egyenlőtlenségben az egyenlőség esete, vagyis $`\text{Cov} \! \left( \hat\vartheta \right) = \mathbf{M}^{-1}`$ valósul meg, akkor a vizsgált becslő maximálisan hatásos, azaz nem lehet nála jobb statisztikát konstruálni.



#### 3. Konzisztencia

A konzisztencia azt fejezi ki, hogy a mintaszám növelésével a becslés pontossága javul.

- _Gyenge konzisztencia:_  
  A mintaszám növelésével nullához tart annak a valószínűsége, hogy az abszolút becslési hiba egy adott $\varepsilon$ értéknél nagyobb legyen. Jelölje $`\vartheta_n`$ az $n$ db minta alapján számított becslést, ekkor:

```math
\lim_{n \to \infty} P \left( \left| \hat\vartheta_n -\vartheta \right| \geq \varepsilon\right) = 0
```

- _Erős konzisztencia:_  
  Akkor áll fenn, ha a becslés torzítatlan és a mintaszám növelésével a becslés varianciája nullához tart:

```math
E \! \left( \hat\vartheta_n \right) = \vartheta
```
```math
\lim_{n \to \infty} D^2 \! \left( \hat\vartheta_n \right) = 0
```


#### 4. Elégségesség

Egy statisztika elégséges, ha a vizsgált paraméterre vonatkozólag nem veszítünk információt, más szóval $d(x)$ statisztikát (a becslés összefüggését) behelyettesítve a likelihood-függvénybe, az eredmény nem függ a becsült $\vartheta$ paramétertől:

```math
f \left( x \ | \ d(x) \right) \neq g(\vartheta)
```


## Identifikációs paradigmák


### Legkisebb négyzetek módszere (LS)

A cél a mérések kimeneti adatai és a modell kimenete közötti négyzetes hiba minimalizálása. Regressziós feladatoknál tipikus:

```math
\hat\vartheta_{LS} = \arg \min_{\vartheta} \frac{1}{2} \sum_{i=1}^n \left( y_i - \hat{y}_i\right)^2
```

ahol az $y_i$ a mért kimeneti adatokat jelöli, $`\hat y_i`$ pedig a modell kimenete, a becsülendő paraméterek a modell paraméterei.


### Maximum likelihood módszer (ML)

A cél a likelihood függvény maximalizálása, vagyis ismert minta esetén annak a paramétervektornak a megtalálása, amelyik esetén a legnagyobb az adott minta előfordulásának a valószínűsége:

```math
\hat\vartheta_{ML} = \arg \max_{\vartheta} f(y|\vartheta)
```



### Maximum a posteriori becslés (MAP)

Ha van előzetes (a priori) információnk a $\vartheta$ paraméter eloszlásáról, akkor ennek ismeretében maximalizáljuk a $\vartheta$ a posteriori (adott minta esetén fennálló) valószínűségét:

```math
\hat\vartheta_{MAP} = \arg \max_{\vartheta} f(\vartheta | y)
```

ahol $f(\vartheta | y)$ a $\vartheta$ paraméter a posteriori sűrűségfüggvénye, amelyet a likelihood függvény és az $f(\vartheta)$ a priori sűrűségfüggvény alapján a Bayes-tétel alapján származtatunk:

```math
f(\vartheta | y) = \frac{f(y|\vartheta) f(\vartheta)}{f(y)}
```

Ha $f(\vartheta)$ egyenletes eloszlású, vagyis nincs a priori információnk, akkor a MAP és az ML becslés ugyanazt az eredményt adja.


### Minimumrizikójú becslés (MRE)

A minimumrizikójú becslés esetén az adott rizikófüggvényt minimalizáljuk.

```math
\hat\vartheta_{MRE} = \arg \min_{\vartheta} E \biggl( W \! \Bigl( \vartheta, d(y) \Bigr) \biggr)
```
Ehhez szükséges a likelihood függvénynek, $\vartheta$ a priori eloszlásának és a rizikófüggvénynek is az ismerete.
