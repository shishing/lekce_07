# Tvořím web A–Z: lekce 7

jaro 2021, Praha

<small>27. dubna 2021</small>

---

## Sémantické značky

---

Značky vol podle toho, co daná část HTML dokumentu představuje: bude to běžný text, poznámka pod čarou, seznam, článek, navigace atd.?

Nikdy nepoužívej značku podle toho, jak vypadá. Vzhled řeš pomocí CSS, nikoli HTML.

---

### Rozdíl mezi `article` a `section`


note:

- čerpal jsem z [článku na Smashing Magazine](https://www.smashingmagazine.com/2020/01/html5-article-section/)

---

#### `article`

- samostatná část stránky (úryvek článku ve výpise, výrobek v e-shopu apod.)
- má svůj ekvivalent v podobě samostatné stránky (viz výše uvedené: celý článek, detail výrobku atd.)

---

#### `section`

- zjednodušeně: tam, kde se nedá použít `article`, ale přesto máme vymezenou část stránky (shrnutí článku, popis kategorie ve výpisu zboží)

note:

- Když v takovém případě použijete `div` není to hrubá chyba, ale snížíte přístupnost stránky pro ty, co jsou odkázáni na strojové čtení.
- původně byly se `section` širší plány, ale bohužel se neujaly. Šlo o to, že `section` by určovala úroveň nadpisů, ale nikdy to žádný prohlížeč plně neimplementoval. To se někdy děje.

---

### Kdy použít `div` (případně `span`)?

Pokud potřebuješ do HTML přidat prvek, abys dosáhla kýženého stylu, například chceš vytvořit flexboxový kontejner, přidej `div`.

Pro řádkové prvky bez významu, použij `span`.

---

### Pár značek pro začátek


Pro začátek se držte doporučení z [Marksheet.io](https://marksheet.io) (mimochodem výborný zdroj pro začátky s HTML/CSS: stručný a přehledný a v angličtině):

---

> Máte na výběr asi stovku HTML elementů. To je _dost_. Dá to fušku procházet celý jejich seznam, abyste vybraly tu správnou značku. Takže si to nekomplikujte a nemarněte čas výběrem vhodné značky pro ten který kousek stránky. Pro začátek po stačí, když si osvojíte tyto značky (a postupně se seznámíte s dalšími):

---

<table>
    <tbody>
        <tr>
            <th>Structure</th>
            <th>Text</th>
            <th>Inline</th>
        </tr>
        <tr>
            <td>
                <code>main</code><br>
                <code>header</code><br>
                <code>h1</code><br>
                <code>h2</code><br>
                <code>h3</code><br>
                <code>nav</code><br>
                <code>footer</code><br>
                <code>article</code><br>
                <code>section</code>
            </td>
            <td>
                <code>p</code><br>
                <code>ul</code><br>
                <code>ol</code><br>
                <code>li</code><br>
                <code>blockquote</code>
            </td>
            <td>
                <code>a</code><br>
                <code>strong</code><br>
                <code>em</code><br>
                <code>q</code><br>
                <code>abbr</code><br>
                <code>small</code>
            </td>
        </tr>
    </tbody>
  </table>

note:

- [Sémantika v HTML](https://marksheet.io/html-semantics.html)
- [Sémantika řádkových prvků](https://marksheet.io/html-inline-semantics.html)
- [How to section your HTML](https://css-tricks.com/how-to-section-your-html/) ­– opravdu vyčerpávající článek o strukturování HTML dokumentu

---

### HTML se pořád vyvíjí

Přesto sledujte dění a mějte oči otevřené. HTML vám toho dává k dispozici mnohem víc, než jen nadpisy, odkazy a odstavce.

<details>
    <summary>Prvek <code>details</code></summary>
    Něco, co byste dříve nevytvořily bez užití JavaScriptu, nabízí nyní HTML v základu.
</details>

```html
<details>
    <summary>Prvek <code>details</code></summary>
    Něco, co byste dříve nevytvořily bez užití JavaScriptu, nabízí nyní HTML v základu.
</details>
```

---

## Obrázkové pozadí

---

### Vlastnost `background-image`

```css
article {
    background-image: url('cesta/k/obrazku.jpg');
}
```
<!-- .element: class="c-text-xs" -->

---

### Vlastnost `background-repeat`

```css
article {
    background-repeat: no-repeat;
}
```
<!-- .element: class="c-text-xs" -->

note:

- ve výchozím nastavení se obrázky na pozadí opakují (je-li pro ně místo)

---

### Vlastnost `background-size`

```css
article {
    background-size: cover; /* roztáhne se přes celou plochu prvku */
    background-size: contain; /* zobrazí se tak, aby byl vidět celý */
    background-size: 100px 200px; /* zobrazí se přesně na pixel */
    background-size: 100% auto; /* zobrazí se přesně na pixel */
}
```
<!-- .element: class="c-text-xs" -->

note:

- U `cover` a `contain` se zachovává poměr stran obrázku.
- U číselných hodnot hrozí deformace. Vyhneš se tomu, pokud nastavíš jeden z rozměrů na `auto`.
- [Další informace na VzhůruDolů.cz](https://www.vzhurudolu.cz/prirucka/css3-background-size)

---

### Vlastnost `background-position`

```css
article {
    background-position: left top;
    background-position: 25% center;
    background-position: 25px 150px;
    background-position: center;
}
```
<!-- .element: class="c-text-xs" -->

note:

- souřadnice jako při pozicování prvků, navíc lze zadat `center`

---

### Lineární gradient

- přechod z jedné barvy do druhé
- a to i přes mnoho dalších barev
- může být velmi složitý, [používají se generátory](https://cssgradient.io/)

---

#### Zápis gradientu

```css
article {
    background-image: linear-gradient(white, black);
}
```
<!-- .element: class="c-text-xs" -->

note:

- gradient se považuje za obrázek
- obšírnější [výklad o gradientech na Marksheet.io](https://marksheet.io/css-gradients.html)
- nemá rozměry, je roztažený přes celý prvek

---

### Několikanásobné pozadí v CSS

```css

.dlazdice {
    background-image:
        url('img/pravy-horni.png'),
        url('img/levy-dolni.png');
    background-position:
        right top,
        left bottom;
    background-repeat:
        no-repat,
        no-repeat;
}

```
<!-- .element: class="c-text-xs" -->

note:

- Pořadím v kódu určuješ vrstvení na stránce. První obrázek na pozadí, bude nejvýše, a dojde-li k překryvu, překryje ostatní.

---

## HTML entity

Snad všechny myslitelné znaky (písmena, číslice, klikyháky, emotikony) se dají v HTML vyjádřit kódem, tzv. entitou. Například `š` lze zapsat jako `&scaron;`. S tím, že HTML entita vždy začíná `&` a končí `;`. Mezi nimi je buď pojmenovaná entita, jako v příkladě výše, nebo číselný kód. Pozor, na velikosti písmen záleží (`&scaron;` = š, `&Scaron;` = Š).

---

Dnes, když je kódování UTF-8 plně rozšířeno, ztrácejí entity na významu. Většinu písmen a symbolů stačí zapsat prostým znakem. Z entit nám pak zůstává nejčastěji nezalomitelná (pevná mezera) `&nbsp;` (Non-Breaking SPace). Tu bychom například v českých textech měli používat vždy za jednopísmennými předložkami: `<q>v&nbsp;řece</q>`. Nebo mezi číslem a jednotkou: `<q>80&nbsp;kg</q>`.

---

**Pozor, entitou vždy zapisujeme, tzv. escapujeme řídicí znaky (které mají v&nbsp;HTML zvláštní význam):**

```html
&gt; = >
&lt; = <
&amp; = &
```

**Entitu musíme například použít, když chceme vypsat `&lt;` ve smyslu _větší než_. Nepoužití entity mate prohlížeč, který vidí začátek otevírací značky.**

---

Nově se entity vracejí na scénu v podobě populárních emoji, např. `&#128567;` = 😷

note:

- [Přehled HTML entit](https://www.w3schools.com/html/html_entities.asp)
- [Jiný přehled týchž HTML entit](https://www.toptal.com/designers/htmlarrows/symbols/)
