# Runbook — od nule do prve uplate

Stanje na 19.8.2026.: proizvodi, tekstovi i P1 workflow su gotovi.
17 prospekata identificirano, 5 s potvrđenom adresom. Ostalo traži izvršenje
koje ovisi o odobrenju MCP alata.

---

## Korak 0 — odblokiraj alate (bez ovoga ništa dalje ne ide)

Firecrawl, Airtable, Gmail i PayPal u zadnjoj sesiji traže odobrenje koje se
u neinteraktivnoj sesiji ne može dati. Pokreni interaktivnu sesiju i odobri
ih, ili ih dodaj u `.claude/settings.json` permissions.

Provjera da radi: `list_bases` na Airtableu mora vratiti odgovor bez traženja
odobrenja.

---

## Korak 1 — dovrši listu na 50 (≈2 h)

Trenutno: 17 identificiranih, 5 s potvrđenom adresom (`prospects.csv`).

**Nedostaje 33.** Metoda koja je dokazano dala rezultate — geo + vertikala,
grad po grad. Generički globalni upiti daju smeće.

Upiti koji su radili:
```
upravljanje apartmanima agencija {GRAD} kontakt info@
property management holiday rentals {REGIJA} contact info@
```

Gradovi koje treba pokriti: Šibenik, Dubrovnik, Pula, Rovinj, Poreč, Makarska,
Trogir, Opatija, Krk · Algarve, Costa del Sol, Amalfi, Kreta, Korfu, Dublin,
Cornwall.

**Pravila:**
- Samo `info@` / `booking@` / `kontakt@`. Nikad `ime.prezime@`.
- **Ne kupuj liste.** U pretrazi su iskočili brandnav i bookyourdata —
  preskoči ih: GDPR rizik i mrtve adrese.
- Svaki red dobiva izvorni URL.
- **Nikad ne vjeruj skraćenom snippetu.** Pretraga je za Irundo Zadar vratila
  `nici@irundo.com` — to je odsječak, prava adresa je `info@irundo.com`.
  Otvori stranicu i vidi adresu.

## Korak 2 — zapažanje po prospektu (≈2 h)

Za svaki od 50: otvori stranicu, nađi **jednu istinitu, konkretnu** stvar.
Ovo je jedini razlog zašto mail neće završiti u smeću.

Netočno zapažanje je gore nego nikakav mail. Ako ne nađeš ništa konkretno,
izbaci prospekt iz liste.

## Korak 3 — Airtable + PayPal (≈30 min)

Shema baze `Outreach` (polja): Tvrtka, Email, URL, Segment, Grad, Drzava,
Jezik, Proizvod, Zapazanje, Status, Datum slanja, Opt-out, Biljeske.

PayPal linkovi: 299 € (P1) i 149 € (P4).
**Otvori svaki link u pregledniku i potvrdi iznos i valutu prije nego ode
klijentu.** Provjeri i limit primanja na osobnom računu.

## Korak 4 — test mail na sebe

Pošalji si prvi mail po predlošku. Provjeri:
- ne pada u Promocije/Spam
- opt-out redak je vidljiv
- nema pokvarenih `{{ }}` placeholdera

Tek onda kreće serija.

## Korak 5 — slanje

| Dan | Broj | Segment |
|---|---|---|
| Sri 19.8. | 12 | HR, najviši prioritet |
| Čet 20.8. | 15 | HR + INT |
| Pet 21.8. | 15 | INT |
| Sub 22.8. | 8 | INT |
| Ned 23.8. | — | follow-up D+3 na prvu seriju |
| Pon 24.8. | — | zatvaranje |

Max 15/dan. Svaki mail zasebno. Nikad BCC.

**Stani odmah** ako: više od 2 bouncea u seriji, bilo koji opt-out (označi u
bazi i nikad više), ili Gmail upozorenje.

---

## Realno očekivanje

50 mailova → 3–8 odgovora → 1–3 razgovora → **0–2 prodaje**.

598 € je dostižno, nije zajamčeno. Najvjerojatniji ishod je 1 prodaja (299 €)
plus par razgovora koji se zatvore u rujnu. Ako do petka nema nijednog
odgovora, problem je u zapažanjima — nisu dovoljno konkretna. Nemoj slati
više mailova, popravi zapažanja.

## Ako netko kupi

1. Naplata **prije** rada (PayPal link).
2. Traži jedan stvarni upit gosta i podatke za `PROPERTY_CONTEXT`.
3. Slijedi `../products/p1-inbox-autopilot/README.md`.
4. Prođi svih 5 testova prije predaje.
