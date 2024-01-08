# 4. Tétel

Paraméter, konfidencia invervallum és struktúra becslés regressziós feladatoknál

---


## Paraméterbecslés

A paraméterbecslés regressziós feladat esetén azt jelenti, hogy valószínűségi változók közötti összefüggés paramétereit becsüljük ismert struktúra esetén. Például egy regeressziós feladat az, ha tudjuk (feltételezzük), hogy egy adott kimeneti változó milyen bemenetektől függ, és hogy az összefüggés lineáris, és ezek mellett a feltételezések mellett keressük az összefüggés (modell) paramétereit.

Tipikus módszer a legkisebb négyzetek módszere


## Konfidenciaintervallum-becslés

Annak meghatározása, hogy ha van egy $\hat\vartheta$ pontbecslésünk, akkor az mennyire megbízható. A feladat az, hogy a becslés eredménye ($\hat\vartheta$) és egy megadott valószínűség (konfidencia, pl. 95%) alapján meghatározzuk, hogy a valós paraméter az adott valószínűséggel milyen két érték közötti intervallumba esik.


## Struktúrabecslés (hipotézisvizsgálat)

A feladat egy adott hipotézisről eldönteni, hogy elutasítsuk-e. Kell egy nullhipotézis és egy alternatív hipotézis. Stuktúrabecslés esetén azt kell eldönteni, hogy két különböző struktúrájú (különböző számú paraméterrel rendelkező) modell statisztikailag szignifikánsan különbözik-e egy adott minta (mérés) ismeretében. Másképpen fogalmazva: egy adott paraméter jelenléte a modellben statisztikailag szignifikánsan más eredményt ad-e, mint ha nincs jelen (értéke nulla). Ilyenkor a nullhipotézis az, hogy nincs jelentősége az adott paraméternek, vagyis hogy a 0 paraméterérték és a becsült paraméterérték statisztikailag nem különbözik szignifikánsan. A hipotézisvizsgálat eredménye, hogy elvessük-e a nullhipotézist, vagy nem.

