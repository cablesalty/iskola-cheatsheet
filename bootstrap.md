<h1 align="center">Bootstrap</h1>
Ez a dokumentum elmagyarázza az összes bootstrapes anyagot amit kilencedikben tanultunk. Ha valamit kihagytam, nyissatok egy issue-t vagy írjatok rám.

---

# Kezdés
> [!NOTE]  
> **Minimális magyarázat erre a szekcióra.** Ha nem tudsz ennyi segítség nélkül berakni egy CSS fájlt a dokumentumodba, akkor sajnálom.


Mielőtt a bootstrapet elkezdenénk használni, be kell valahogy **importálnunk** a HTML dokumentumunkba. Erre a szükséges linkeket megtaláljuk a [Bootstrap hivatalos dokumentációjában. (getbootstrap.com)](https://getbootstrap.com/docs/5.3/getting-started/introduction/)

Görgessünk le, amég meg nem találjuk a linkeket a **CDN links** cím alatt.
Itt van például a Bootstrap 5.3.7-nek a linkje

| Leírás | URL                                                                          |
| ------ | -----                                                                        |
| CSS    | https://cdn.jsdelivr.net/npm/bootstrap@5.3.7/dist/css/bootstrap.min.css      |
| JS     | https://cdn.jsdelivr.net/npm/bootstrap@5.3.7/dist/js/bootstrap.bundle.min.js |

Ezeket a linkeket be tudjuk másolni `<link>` vagy `<script>` tagokba hogy belerakjuk a dokumentumunkba.

# Breakpointok
A breakpointok előre megszabott *törésvonalak*, amik segítenek behatárolni egy objektumnak, vagy egy kijelzőnek a méretét.

Leggyakrabban a [grid rendszerben](#row-és-a-col-grid) és a [containerek](#tárolók---containers)nél használjuk, hogy megszabjuk melyik törésvonal alatt töltse ki a szülőobjektumnak a 100%-át.

### Itt vannak azok a breakpointok, amiket órán használtunk:
| Megnevezés | Breakpoint | Kijelző/Szülőobjektum méret |
| --- | --- | --- |
| Telefonos méret (small) | `sm` | &ge;576px |
| Tablet méret (medium) | `md` | &ge;768px |
| Asztali gép méret (large) | `lg` | &ge;992px |
| Extra large | `xl` | &ge;1200px |

# Tárolók - Containers
A containerek segítenek nekünk egy **fix szélességű tárolót** készíteni. A feladatuk, hogy mindig egy előre megszabott szélességük legyen egy bizonyos [breakpoint](#breakpointok)-ig.

[A hivatalos angol dokumentációt meg találod itt.](https://getbootstrap.com/docs/5.3/layout/containers/)

> [!IMPORTANT]  
> A "fix szélesség" alól a `.container-fluid` kivételt szolgál, mivel az mindig a szülő tároló 100%-át foglalja el.

## Hogyan működik?
Tegyük fel, hogy raksz egy container-t egy `<div>`-re, valahogy így:
```html
<div class="container"></div>
```
Ennek a `<div>`-nek nincsen *szülőobjektuma*, azaz nem egy másik `<div>`-be vagy más tagban van, hanem csak magában.  
Például egy teljes HTML dokumentum amiben benne van így nézne ki:
```html
<!DOCTYPE html>
<html lang="hu">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Az én oldalam!</title>
</head>
<body>
    <div class="container"></div>
</body>
</html>
```
Ebben a példában a container class beállít egy megszabott szélességet arra a `<div>`-re a kijelződ, vagy a böngészőablakod mérete szerint.

### Szóval itt a definíció:
Egy container fix szélessége breakpointonkénk változik, és addig maradnak fix szélességűek, ameddig a szülőobjektumának szélessége el nem éri a megszabott breakpoint alatti határt. Utánna a szülőobjektum 100%-át tölti ki. Például egy `.container-md` addig marad fix szélességű, ameddig a szülőobjektum szélessége az `md` breakpointnál nem kisebb.

---

Itt van egy táblázat az összes container variációra minden breakpoint között:

|  | Extra small (<576px) | Small (&ge;576px) | Medium (&ge;768px) | Large (&ge;992px) | X-Large (&ge;1200px) | XX-Large (&ge;1400px) |
| --- | --- | --- | --- | --- | --- | --- |
| `.container` | 100% | 540px | 720px | 960px | 1140px | 1320px |
| `.container-sm` | 100% | 540px | 720px | 960px | 1140px | 1320px |
| `.container-md` | 100% | 100% | 720px | 960px | 1140px | 1320px |
| `.container-lg` | 100% | 100% | 100% | 960px | 1140px | 1320px |
| `.container-xl` | 100% | 100% | 100% | 100% | 1140px | 1320px |
| `.container-xxl` | 100% | 100% | 100% | 100% | 100% | 1320px |
| `.container-fluid` | 100% | 100% | 100% | 100% | 100% | 100% |

## Container-fluid??
Igen, a container fluid **minden esetben** a szülőobjektum 100%-át tölti ki.


## Szintaxis:
```
.container-{breakpoint}
```
Például:
```
.container-md
```

## Próba kód
Próbáld ki ezt a HTML fájlt, és teszteld le a containereket:
```html
<!DOCTYPE html>
<html lang="hu">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.7/dist/css/bootstrap.min.css">
    <title>Bootstrap példa</title>
</head>
<body>
    <h1>Bootstrap példa</h1>
    <p>Próbáld meg átméretezni a böngészőablakokat, és nézd meg hogyan változnak a containerek.</p>
    <br>
    <div class="bg-success text-light mb-2 p-2 rounded container">.container</div>
    <div class="bg-success text-light mb-2 p-2 rounded container-sm">.container-sm</div>
    <div class="bg-success text-light mb-2 p-2 rounded container-md">.container-md</div>
    <div class="bg-success text-light mb-2 p-2 rounded container-lg">.container-lg</div>
    <div class="bg-success text-light mb-2 p-2 rounded container-xl">.container-xl</div>
    <div class="bg-success text-light mb-2 p-2 rounded container-xxl">.container-xxl</div>
    <div class="bg-success text-light mb-2 p-2 rounded container-fluid">.container-fluid</div>
    <br>
    <p>&copy 2025 Szabó Patrik</p>
</body>
</html>
```

# Row és a col (grid rendszer)

## Hogyan működik?
A `.row` class ad nekünk egy sort, amibe oszlopokat, vagyis `.col`-okat rakhatunk.

Például:
```html
<div class="container">
    <div class="row">
        <div class="col">
            Oszlop
        </div>

        <div class="col">
            Oszlop
        </div>

        <div class="col">
            Oszlop
        </div>
    </div>
</div>
```

Ebben a példában mindegyik sor ugyan akkora, és mivel egy sor **mindig 12 egységből áll**, ezért ezt ezzel a kóddal is el tudjuk érni:
```html
<div class="container">
    <div class="row">
        <div class="col-4">
            Oszlop
        </div>

        <div class="col-4">
            Oszlop
        </div>

        <div class="col-4">
            Oszlop
        </div>
    </div>
</div>
```

Viszont, meg tudunk minden oszlopnak külön adni egy méretet. Egy sor az mindig **12 egységből** áll. Szóval például ha egy 2:1 arányű sort akarunk csinálni, akkor az egyik col az 8 a másik meg 4 lesz.

Ezt be is tudjuk vinni kódba így:
```html
<div class="container">
    <div class="row">
        <div class="col-8">
            Oszlop
        </div>

        <div class="col-4">
            Oszlop
        </div>
    </div>
</div>
```