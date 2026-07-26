# AI Automation Agency — Curated Components

> Adaptacija `claude-code-templates` za AI agenciju koja nudi automatizaciju klijentima.
> Orginal: [aitmpl.com](https://aitmpl.com) | Fork: `shxmi03/claude-code-templates`

## Što je ovo?

Kurirana kolekcija komponenti iz `claude-code-templates` (3955 ukupno) — odabrano ono što je najkorisnije za AI agenciju koja nudi:
- Web scraping & monitoring
- Content automation
- Business process automation
- Knowledge management
- Custom AI agenti

## Top komponente po kategoriji

### 1. Business & Marketing Agenti

| Agent | Opis | Kategorija |
|---|---|---|
| `content-marketer` | Generiranje marketing copy, strategija | business-marketing |
| `seo-specialist` | SEO analiza, optimizacija sadržaja | business-marketing |
| `competitive-analyst` | Analiza konkurencije | business-marketing |
| `market-researcher` | Istraživanje tržišta | business-marketing |
| `product-strategist` | Produktna strategija | business-marketing |
| `sales-automator` | Automatizacija prodajnog procesa | business-marketing |
| `customer-success-manager` | Klijentska podrška | business-marketing |
| `communication-excellence-coach` | Pisanje emailova, komunikacija | business-marketing |

**Install:**
```bash
npx claude-code-templates@latest --agent business-marketing/content-marketer --yes
npx claude-code-templates@latest --agent business-marketing/seo-specialist --yes
npx claude-code-templates@latest --agent business-marketing/competitive-analyst --yes
```

### 2. Content & Media Automation

| Agent | Opis | Kategorija |
|---|---|---|
| `content-curator` | Kuration sadržaja | obsidian-ops-team |
| `blog-writer` | Generiranje blog postova | .claude/agents |
| `podcast-creator-team` | Proizvodnja podcasta | agents |
| `video-creation` | Video generacija | development-team |

**Install:**
```bash
npx claude-code-templates@latest --agent obsidian-ops-team/content-curator --yes
```

### 3. Data & Research

| Agent | Opis | Kategorija |
|---|---|---|
| `data-ai/analyst` | Analiza podataka | data-ai |
| `deep-research-team` | Dubinsko istraživanje | deep-research-team |
| `web-tools/scraper` | Web scraping | web-tools |
| `ocr-extraction-team` | OCR i ekstrakcija | ocr-extraction-team |

### 4. Development & DevOps

| Agent | Opis | Kategorija |
|---|---|---|
| `frontend-developer` | Frontend development | development-team |
| `development-tools/code-reviewer` | Code review | development-tools |
| `devops-infrastructure` | DevOps, infrastruktura | devops-infrastructure |
| `api-graphql` | API dizajn | api-graphql |

### 5. Autonomni Loopovi (ključno za agenciju!)

Loopovi = agenti koji rade sami u pozadini s ciljem + intervalom + stop uvjetom.

| Loop | Opis | Što radi |
|---|---|---|
| `engineering/docs-sweep-loop` | Automatsko ažuriranje dokumentacije | Periodicno čisti i ažurira docs |
| `engineering/build-test-fix-loop` | CI/CD loop | Testira, gradi, fixa |
| `engineering/production-error-sweep-loop` | Monitoring grešaka | Prati logove, javlja greške |
| `engineering/goal-refiner-loop` | Refiniranje ciljeva | Analizira progres, prilagođava ciljeve |

**Install:**
```bash
npx claude-code-templates@latest --loop engineering/docs-sweep-loop --yes
npx claude-code-templates@latest --loop engineering/production-error-sweep-loop --yes
```

### 6. MCP Integracije (vanjski servisi)

MCP-ovi omogućavaju agentima da koriste vanjske alate.

| MCP | Opis | Use case |
|---|---|---|
| `github-integration` | GitHub API | Repo management, PR, issues |
| `slack-integration` | Slack bot | Timska komunikacija |
| `discord-integration` | Discord bot | Community management |
| `notion-mcp` | Notion API | Knowledge base |
| `bright-data-mcp` | Web scraping | Data extraction |

## Struktura projekta za agenciju

```
agency-client/
├── .claude/
│   ├── agents/           # Klijentski agenti
│   ├── commands/         # Custom komande
│   ├── settings/         # Konfiguracija
│   └── hooks/            # Automatski triggeri
├── src/
│   ├── scrapers/         # Firecrawl scraperi
│   ├── agents/           # Hermes agent skripte
│   ├── automation/       # Cron + workflow skripte
│   └── integrations/     # API integracije
├── docs/
│   ├── client-brief.md   # Zahtjevi klijenta
│   ├── architecture.md   # Arhitektura rješenja
│   └── reports/          # Izvještaji
├── .env                # API ključevi (NE commitati!)
├── package.json        # Node.js dependencije
└── docker-compose.yml  # Lokalni dev
```

## Primjer: Klijent "E-commerce Scraper"

**Scenario:** Klijent želi pratiti cijene 50 konkurenata i dobiti Telegram alert kad se cijena promijeni.

```bash
# 1. Install potrebne komponente
npx claude-code-templates@latest \
  --agent web-tools/scraper \
  --agent business-marketing/competitive-analyst \
  --loop engineering/docs-sweep-loop \
  --command testing/generate-tests \
  --mcp web-data/brightdata \
  --yes

# 2. Kreiraj projekt
mkdir agency-client/ecommerce-scraper
cd agency-client/ecommerce-scraper

# 3. Setup Hermes agenta za scraping
cat > .claude/agents/scraper-agent.md << 'EOF'
# Scraper Agent

## Role
Monitoring cijena konkurenata za e-commerce klijenta.

## Tasks
1. Dohvati cijene s 50 URL-eva (Firecrawl)
2. Usporedi s prethodnim vrijednostima
3. Pošalji Telegram alert ako je promjena > 5%
4. Generiraj tjedni izvještaj (Excel/CSV)

## Schedule
- Svakih 6 sati (cron)
- Tjedni izvještaj: nedjelja 18:00
EOF
```

## Dodatni resursi

- **Dashboard:** [aitmpl.com](https://aitmpl.com) — browse all 3955 components
- **Orginal repo:** [davila7/claude-code-templates](https://github.com/davila7/claude-code-templates)
- **Fork:** [shxmi03/claude-code-templates](https://github.com/shxmi03/claude-code-templates)

---

*Agency adaptation — 2026-07-24*
