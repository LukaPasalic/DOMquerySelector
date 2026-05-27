# Lekcija 1 — querySelector i classList

## 1. querySelector — novi način dohvaćanja elemenata

Do sada  ste koristili `getElementById`. Postoji bolji način koji koristi **iste selektore kao CSS**:

```javascript
// Stari način
document.getElementById("naslov")

// Novi način — querySelector
document.querySelector("#naslov")    // po id-u (# kao u CSS-u)
document.querySelector(".kartica")   // po klasi (. kao u CSS-u)
document.querySelector("h1")         // po HTML tagu
```

**Pravilo:** Sve što možeš pisati kao CSS selektor, možeš staviti u `querySelector`.

### Što ako ima više elemenata?

```javascript
// querySelector → vraća samo PRVI element
const prvaKartica = document.querySelector(".kartica");

// querySelectorAll → vraća SVE elemente (kao listu)
const sveKartice = document.querySelectorAll(".kartica");

// Za querySelectorAll trebaš petlju!
for (const kartica of sveKartice) {
    kartica.textContent = "Promijenjeno!";
}
```

### ⚠️ Pazi — ako element ne postoji:

```javascript
const el = document.querySelector("#nePostoji");
console.log(el); // null

el.textContent = "test"; // ❌ GREŠKA! Ne možeš raditi s null
```

Ako u konzoli vidiš grešku — provjeri je li id/klasa ispravno napisana.

---

## 2. classList — mijenjanje CSS klasa iz JS-a

Umjesto da pišeš stilove direktno u JS, bolji pristup je **dodavati i skidati CSS klase**:

```javascript
const el = document.querySelector("#mojDiv");

el.classList.add("aktivan")       // dodaj klasu
el.classList.remove("aktivan")    // ukloni klasu
el.classList.toggle("aktivan")    // dodaj ako nema, ukloni ako ima
el.classList.contains("aktivan")  // provjeri → vraća true ili false
```

### Primjer — dark mode gumb:

```css
/* U CSS-u definiraš kako izgleda */
.tamno {
    background: #1a1a2e;
    color: white;
}
```

```javascript
// JS samo dodaje/uklanja klasu
const gumb = document.querySelector("#temaGumb");

gumb.addEventListener("click", () => {
    document.body.classList.toggle("tamno");
});
```

**Zašto ovako a ne `element.style.color = "red"`?**  
Jer stilovi trebaju biti u CSS-u, a logika u JS-u. Lakše se mijenja i održava.

---

## Rezime

```javascript
document.querySelector("#id")         // jedan element po id-u
document.querySelector(".klasa")       // jedan element po klasi
document.querySelectorAll(".klasa")    // svi elementi → treba petlja

el.classList.add("klasa")             // dodaj
el.classList.remove("klasa")          // ukloni
el.classList.toggle("klasa")          // dodaj/ukloni
el.classList.contains("klasa")        // provjeri → true/false
```

---

## ✏️ Otvori vjezba.html i riješi zadatke

---

## Zaglavljen si?

**querySelector vraća null** → provjeri piše li `#` ispred id-a i `.` ispred klase.

**classList ne mijenja izgled** → provjeri je li ista klasa u CSS-u i u JS-u. Jedna tipfela i neće raditi.

**querySelectorAll ne radi** → ne možeš direktno pisati `.textContent` na listi. Trebaš `for...of` petlju.
