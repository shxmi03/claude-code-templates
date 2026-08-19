# P1 — Inbox Autopilot

Nacrt odgovora na upit gosta, spreman u Gmail Draftovima. **Ništa se ne šalje
automatski** — vlasnik pročita i klikne Pošalji.

## Tok

```
Gmail (novi upit)
  → Pripremi kontekst   (izvuče tekst + ubaci podatke o objektu)
  → Claude              (prepozna jezik, izvuče termin/osobe, napiše nacrt)
  → Parsiraj odgovor    (JSON.parse, odbaci ne-upite)
  ├→ Gmail Draft        (nacrt u istom threadu)
  └→ Airtable           (log upita)
```

## Instalacija kod klijenta

1. Import `n8n-workflow.json` u n8n.
2. Spoji credentials: **Gmail OAuth2** (klijentov račun) i **Airtable token**.
3. Postavi environment varijable u n8n:
   - `ANTHROPIC_API_KEY`
   - `AIRTABLE_BASE_ID`
4. U čvoru **Pripremi kontekst** popuni `PROPERTY_CONTEXT` — sve `{{POPUNITI}}`
   markere. Ovo je najvažniji korak: kvaliteta nacrta ovisi gotovo isključivo
   o točnosti ovog konteksta.
5. U Airtableu napravi tablicu `Upiti` s poljima: Gost, Email, Jezik, Dolazak,
   Odlazak, Osoba, Jedinica, Nedostaje, Zaprimljeno, Status.

## Zaštite ugrađene u prompt

- Odgovara na jeziku kojim je gost pisao.
- Koristi **isključivo** cijene iz `PROPERTY_CONTEXT`. Ako podatak nedostaje,
  upisuje `[PROVJERITI: ...]` umjesto da izmisli cijenu.
- Nikad ne potvrđuje dostupnost kao sigurnu — rezervacija je potvrđena tek
  nakon vlasnikove potvrde.
- Poruke koje nisu upiti (newsletteri, računi, spam) se odbacuju prije nego
  dođu do Draftova.
- `stop_reason: "refusal"` i neuspjeli JSON parse se hvataju i preskaču, ne
  ruše workflow.

## Testiranje prije predaje

1. Pošalji si probni upit na hrvatskom → provjeri nacrt.
2. Pošalji probni upit na njemačkom → provjeri da je nacrt na njemačkom.
3. Pošalji upit s nemogućim terminom → provjeri da ne izmišlja dostupnost.
4. Pošalji običan newsletter → provjeri da nacrt **nije** stvoren.
5. Provjeri da svaki test ima red u Airtableu.

Tek kad svih 5 prođe, workflow ide klijentu.

## Trošak po upitu

Model `claude-opus-5`, ~2–4 tis. ulaznih i ~500 izlaznih tokena po upitu.
Pri $5/M ulaz i $25/M izlaz to je oko **2–3 centa po upitu** — čak i uz 50
upita dnevno to je ispod 1 € dnevno. Trošak snosi klijent na svom API ključu.
