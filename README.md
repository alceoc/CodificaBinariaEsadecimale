[README.md](https://github.com/user-attachments/files/32753351/README.md)
# 🎲 Bit Challenge

**Gioco interattivo per allenarsi con la codifica binaria ed esadecimale.**
Esercizi generati a caso su conversioni di base, somme in complemento a 2 e numeri in virgola mobile IEEE-754, con punteggio, serie di risposte esatte, timer opzionale e svolgimento passo passo di ogni esercizio.

Pensato come materiale di supporto alla didattica di Informatica (scuola secondaria di secondo grado e primo anno universitario), ma utilizzabile da chiunque voglia esercitarsi da solo.

> Un solo file HTML, nessuna installazione, nessun server, nessuna dipendenza da installare.

---

## ✨ Caratteristiche

- **11 tipi di esercizio** estratti a caso (puoi sceglierne quanti vuoi).
- **3 livelli di difficoltà** (Facile, Medio, Difficile).
- **Modalità a tempo** opzionale (45 secondi a domanda) con bonus velocità.
- **Sfide da 5, 10 o 20 domande.**
- **Svolgimento guidato** dopo ogni risposta: somme in colonna con i riporti, divisioni e moltiplicazioni successive, passaggi della normalizzazione IEEE-754, ecc.
- **Suggerimenti** dedicati a ogni tipo di esercizio (costano 3 punti).
- **Punteggio con serie** (bonus per le risposte esatte consecutive) e **livello finale**.
- **Riepilogo per categoria** a fine sfida, per capire dove ripassare.
- **Record personale** salvato nel browser (`localStorage`).
- **Pulsante ⌂ Home** per annullare la sfida in corso e tornare alle impostazioni.
- **Responsive** (smartphone, tablet, LIM) e **tema chiaro/scuro** automatico.

---

## 🧩 Tipi di esercizio

| # | Categoria | Cosa si chiede |
|---|-----------|----------------|
| 1 | **Binario ⇄ Decimale** | Conversione in entrambe le direzioni |
| 2 | **Esadecimale ⇄ Decimale** | Conversione in entrambe le direzioni |
| 3 | **Esadecimale ⇄ Binario (diretta)** | Conversione a gruppi di 4 bit, senza passare dal decimale |
| 4 | **Somma stesso segno** | Somma in Ca2 di due positivi o due negativi |
| 5 | **Somma tra numeri negativi** | Somma in Ca2 di due numeri negativi |
| 6 | **Somma segno opposto** | Somma in Ca2 di un positivo e un negativo |
| 7 | **Somma con overflow** | Risultato su n bit oppure `OVF` se non rappresentabile |
| 8 | **Sottrazione in Ca2** | A − B calcolata come A + (−B) |
| 9 | **Rappresentazione Ca1/Ca2** | Da decimale negativo a complemento a 1 o a 2 |
| 10 | **Virgola binaria ⇄ Decimale** | Numeri con parte frazionaria (algoritmo della moltiplicazione per 2) |
| 11 | **Virgola mobile IEEE-754 ⇄ Decimale** | Single precision a 32 bit, in entrambe le direzioni |

### Livelli di difficoltà

| Parametro | Facile | Medio | Difficile |
|-----------|:------:|:-----:|:---------:|
| Bit nelle conversioni bin ⇄ dec | 4 | 8 | 12 |
| Bit nelle somme/sottrazioni Ca2 | 4 | 6 | 8 |
| Valore massimo esadecimale ⇄ dec | FF | FFF | FFFF |
| Cifre esadecimali ⇄ binario | 2 | 3 | 4 |
| Bit di mantissa IEEE-754 | 2 | 4 | 5 |
| Esponente reale IEEE-754 | 0 … 4 | −4 … 8 | −8 … 10 |

---

## 🚀 Come usarlo

### In locale
1. Scarica `gioco-esercizi-binari.html` (o clona il repository).
2. Aprilo con un doppio clic nel browser (Chrome, Edge, Firefox, Safari).

```bash
git clone https://github.com/<tuo-utente>/bit-challenge.git
cd bit-challenge
# apri il file nel browser, ad esempio:
open gioco-esercizi-binari.html        # macOS
xdg-open gioco-esercizi-binari.html    # Linux
start gioco-esercizi-binari.html       # Windows
```

### Online con GitHub Pages
1. Rinomina il file in `index.html` (oppure aggiungi un redirect).
2. In **Settings → Pages** scegli il branch `main` e la cartella `/ (root)`.
3. Il gioco sarà disponibile su `https://<tuo-utente>.github.io/bit-challenge/`.

### In classe
Il file può essere caricato così com'è su Moodle, Google Classroom, Teams o su qualsiasi sito scolastico, oppure aperto da chiavetta USB sulla LIM.

---

## ✍️ Formato delle risposte

| Situazione | Come rispondere |
|------------|-----------------|
| Conversione in decimale | Numero intero, ad esempio `45` |
| Conversione in binario | Solo cifre 0 e 1 (gli zeri iniziali sono facoltativi) |
| Conversione in esadecimale | Cifre `0-9 A-F`, maiuscole o minuscole, anche con prefisso `0x` o `#` |
| Somme, sottrazioni, Ca1/Ca2 | **Esattamente n bit**, come indicato nella domanda |
| Overflow | Scrivi `OVF` (o `overflow`) se il risultato non è rappresentabile |
| Numeri con la virgola | Vanno bene sia `,` sia `.` (es. `5,375`) |
| IEEE-754 → binario | 32 bit con o senza spazi, con `\|` come separatore oppure 8 cifre esadecimali |
| IEEE-754 → decimale | Numero decimale, anche negativo (es. `−13,25`) |

---

## 🏆 Punteggio

```
risposta esatta = 10 + 2 × min(serie, 5) + bonus tempo − 3 (se hai usato il suggerimento)
```

- La **serie** aumenta a ogni risposta esatta consecutiva e si azzera con un errore.
- Il **bonus tempo** (solo in modalità a tempo) è `secondi rimasti / 5`, arrotondato.
- Ogni risposta esatta vale almeno 1 punto.

**Livello finale** in base alla percentuale di risposte esatte:

| Percentuale | Livello |
|:-----------:|---------|
| ≥ 90 % | 🏆 Maestro del binario |
| ≥ 70 % | 🥈 Esperto |
| ≥ 50 % | 🥉 Apprendista |
| < 50 % | Principiante |

---

## 🗂️ Struttura del codice

Tutto è contenuto in un unico file HTML, organizzato in tre blocchi: `<style>`, markup e `<script>`.

```
gioco-esercizi-binari.html
├── <style>          CSS con variabili per tema chiaro/scuro
├── <body>           Tre schermate: setup · game · end
└── <script>
    ├── utilità             R(), pad(), ca2(), dec2(), addColumns(), divSteps() …
    ├── TIPS                Testi dei suggerimenti per categoria
    ├── CATS                Elenco delle categorie {id, name, gen}
    ├── gen…()              Un generatore per categoria
    └── stato e interfaccia S, show(), nextQ(), resolve(), finish() …
```

### Come è fatto un esercizio

Ogni generatore `gen…(difficoltà)` restituisce un oggetto con questa forma:

```js
{
  label:   "Testo della consegna",
  body:    "<div class='big'>…</div>",   // HTML mostrato nel riquadro scuro
  ph:      "placeholder del campo di risposta",
  check:   (risposta) => true | false,   // verifica la risposta dell'utente
  correct: "risposta corretta da mostrare",
  sol:     () => "HTML dello svolgimento passo passo"
}
```

---

## 🔧 Personalizzazione

### Aggiungere una nuova categoria di esercizi

1. Scrivi un generatore che restituisca un oggetto nel formato qui sopra:

```js
function genEsempio(d) {
  const v = R(1, 100);
  return {
    label: 'Converti in binario',
    body: `<div class="big">${v}</div>`,
    ph: 'numero binario',
    check: s => parseInt(clean(s), 2) === v,
    correct: v.toString(2),
    sol: () => `<pre>${divSteps(v, 2)}</pre>`
  };
}
```

2. Aggiungilo all'array `CATS`:

```js
{ id: 'es', name: 'Il mio esercizio', gen: genEsempio }
```

3. (Facoltativo) aggiungi un suggerimento in `TIPS` con la stessa chiave `id`.

### Altre modifiche comuni

| Cosa | Dove |
|------|------|
| Cambiare i bit per livello | funzione `widths()` |
| Cambiare la durata a domanda | valore `45` in `nextQ()` (e nel testo del pulsante «45s a domanda») |
| Cambiare i colori | variabili CSS in `:root` |
| Cambiare le soglie dei livelli | funzione `finish()` |

---

## ✅ Verifica del funzionamento

Il codice è stato verificato con test automatici (jsdom) che generano centinaia di esercizi per ogni categoria e livello controllando che:

- la risposta corretta venga sempre accettata e le risposte prive di senso sempre rifiutate;
- lo svolgimento passo passo venga costruito senza errori;
- le somme in colonna coincidano con il calcolo decimale;
- le codifiche IEEE-754 coincidano con la conversione a `float` a 32 bit fornita dal computer.

---

## 🌐 Compatibilità

Funziona con qualsiasi browser moderno (Chrome, Edge, Firefox, Safari, anche da mobile).
I caratteri (Space Grotesk, Inter, JetBrains Mono) sono caricati da Google Fonts; senza connessione il gioco funziona comunque con i caratteri di sistema.

---

## 📚 Argomenti trattati

Materiale collegato alla presentazione didattica *«Codifica binaria ed esadecimale»*:
sistemi di numerazione, conversioni tra basi, complemento a 1 e a 2, operazioni con i numeri binari, overflow, numeri reali in virgola fissa, standard IEEE-754.

---

## 🤝 Contribuire

Segnalazioni di errori e proposte di nuove categorie di esercizi sono benvenute:
apri una **Issue** oppure una **Pull Request**.

## 📄 Licenza

Distribuito con licenza **MIT** — sei libero di usarlo, modificarlo e condividerlo, anche in ambito scolastico.
Aggiungi un file `LICENSE` al repository con il testo della licenza scelta.
