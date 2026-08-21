# Ponuda — 5 proizvoda

> Proizvod nisu komponente iz ovog repoa. One su MIT-licencirane, tuđe
> (© Daniel Ávila) i besplatno dostupne na aitmpl.com. Prodaje se **usluga
> implementacije** na njima: postavljanje, integracija, testiranje, predaja.

Sve cijene su bez PDV-a i podrazumijevaju rad na daljinu.

---

## P1 — Inbox Autopilot ⭐ glavni proizvod

**299 €** jednokratno · isporuka 3–5 dana

Dolazni upit gosta → AI pročita, prepozna jezik, izvuče termin i broj osoba →
napiše **nacrt** odgovora s cijenom i dostupnošću → nacrt čeka u Gmail
Draftovima → vlasnik pročita i klikne Pošalji. Svaki upit se logira u Airtable.

**Ključno:** nacrt, ne automatsko slanje. Vlasnik zadržava punu kontrolu nad
onim što ide gostu. To je i glavni prodajni argument — nitko ne želi da robot
piše gostima u njegovo ime bez nadzora.

Uključeno:
- n8n workflow (`products/p1-inbox-autopilot/n8n-workflow.json`)
- Prompt prilagođen njihovom objektu, cjeniku i tonu
- Airtable baza upita s izvorom i statusom
- 30 dana podrške na ispravke

Komponente iz repoa: `cli-tool/components/skills/business-marketing/email-sequence/`,
`.../email-systems/`, `cli-tool/components/agents/business-marketing/customer-support.md`

**Zašto sad:** kolovoz je vrhunac sezone. Bol je akutna danas, ne u listopadu.

---

## P2 — Radar konkurencije

**349 €** setup + **49 €/mj** održavanje

Dnevno skeniranje N konkurentskih oglasa (Firecrawl) → povijest cijena u
Airtableu → Telegram/email alert kad cijena skoči ili padne >5% → tjedni
izvještaj.

Komponente: `skills/web-data/scrape/`, `agents/business-marketing/competitive-analyst.md`
Referentna implementacija cron + Telegram već postoji u repou:
`cloudflare-workers/pulse/index.js`

---

## P3 — Reputation Guard

**249 €** jednokratno

Praćenje Google i Booking recenzija → alert na svaku novu, prioritet na
negativne → AI nacrt odgovora u tonu vlasnika. Isti princip kao P1: nacrt,
odobrenje, slanje.

---

## P4 — Web/SEO audit u 48 h

**149 €** — ulazni proizvod

Crawl stranice + analiza → PDF s prioritiziranim popravcima (što, zašto,
koliko vrijedi). Služi kao jeftini "da" i most prema P1/P2, ne kao glavni
izvor prihoda: treba 4 prodaje za 500 €.

Komponente: `skills/business-marketing/seo-audit/`, `.../page-cro/`

---

## P5 — Lead Engine

**399 €** setup + **99 €/mj**

Firecrawl po definiranom profilu idealnog klijenta nalazi prospekte →
obogaćuje podatke → puni Airtable CRM → generira nacrte outreach mailova.

Komponente: `skills/business-marketing/lead-research-assistant/`

**Prodajni argument:** to je doslovno sustav koji je izgrađen za ovu kampanju.
Demo je vlastiti rezultat, ne screenshot iz tuđe prezentacije.

---

## Put do 500 €

| Kombinacija | Iznos |
|---|---|
| 2 × P1 | **598 €** ← ciljna |
| P1 + P2 | 648 € |
| P2 + P4 | 498 € |
| P5 | 399 € (nedovoljno samo) |

Kapacitet je 1–2 klijenta s punom implementacijom, pa je 2 × P1 realna meta.

---

## ⚠️ Naplata — otvoreno pitanje

Bez registriranog obrta/d.o.o. ne postoji način izdavanja računa. Hrvatska
tvrtka neće platiti 299 € bez R1 računa jer to ne može knjižiti kao trošak, a
ponavljana naplaćena djelatnost bez registracije je neprijavljeni rad.

Zato je 30 od 50 meta u inozemstvu — mikro-operateri koji plate PayPal linkom
i kojima je PayPal potvrda dovoljna.

**Trajno rješenje:** paušalni obrt, prijava online preko e-Obrt, ~1–3 dana.
Pokreni paralelno ako želiš prodavati hrvatskim tvrtkama.

**Druga provjera:** PayPal osobni račun ima limite za primanje poslovnih
uplata i traži verifikaciju nakon prvih uplata. Provjeri limit prije nego
pošalješ prvu ponudu.
