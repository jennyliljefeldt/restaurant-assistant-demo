# Clipora Studio — Arkitektur & Beslut

> Levande dokument. Uppdatera när nya beslut fattas.

---

## Övergripande arkitektur

Clipora Studio bygger en **generell AI-assistent-motor** som kan användas av olika typer av företag — salonger, restauranger, butiker, hotell m.fl.

Varje kund är en egen "tenant" med sitt eget Google Sheet och en rad i ett centralt Registry-sheet. Ett och samma n8n-workflow hanterar alla kunder.

---

## Beslutade principer

### 1. En motor — inte en per bransch
**Beslut:** Vi bygger och underhåller ett enda n8n-workflow, inte separata per bransch.

**Motivering:** Workflow-logiken (ta emot meddelande → hämta data → AI-agent → svara) är identisk oavsett bransch. Det som skiljer är systemprompten och sheet-strukturen — och dessa är redan per-kund.

**Konsekvens:** Systemprompten i varje kunds `SystemPrompt`-flik gör det branschanpassade jobbet. Workflowet ska vara tillräckligt generellt för att hämta det som finns och ignorera det som saknas.

---

### 2. Generella variabelnamn
**Beslut:** Byt ut restaurangspecifika variabelnamn mot generella.

| Nuvarande | Ska bli |
|---|---|
| `restaurantId` | `clientId` |
| `restaurantName` | `clientName` eller `businessName` |

**Gäller i:** n8n workflow, webhook-URL, Google Sheets, systemprompter, kod och dokumentation.

**Status:** ⏳ Att göra — innan nästa kund efter Lisa

---

### 3. Generella sheet-flikar
**Beslut:** Fliknamn i Google Sheet ska vara branschneutrala.

| Funkar för alla | Branschspecifik — undvik |
|---|---|
| `OpeningHours` | `MenuItems` |
| `FAQ` | `TableCapacity` |
| `PriceList` | `DishCategories` |
| `SystemPrompt` | |
| `Bookings` | |
| `Customers` | |
| `Capacity` | |

**Konsekvens:** Varje kund har bara de flikar de behöver. Workflowet hanterar att vissa flikar saknas.

---

### 4. BusinessType i Google Sheet
**Beslut:** Lägg till en `BusinessType`-rad i `SystemPrompt`-fliken (eller ett eget fält i Registry).

**Motivering:** Gör det möjligt för AI-agenten att automatiskt anpassa sitt beteende och tonalitet baserat på typ av verksamhet.

**Exempel:** `salon`, `restaurant`, `retail`, `hotel`

**Status:** ⏳ Att designa och implementera

---

### 5. Registry-sheetet
**Beslut:** Överväg att lägga till en `businessType`-kolumn i Registry för framtida filtrering och rapportering per bransch.

**Status:** ⏳ Att göra

---

## Kunder & tenants

| clientId | Namn | Bransch | Status |
|---|---|---|---|
| `DEMO_999` | Demo | Restaurang | ✅ Aktiv |
| `newplace_001` | New Place | Restaurang | ✅ Aktiv |
| `lisas_klipp_001` | Lisas Klipp | Salong | 🔜 Potentiell |

---

## Att göra — prioriterat

- [ ] Byt variabelnamn: `restaurantId` → `clientId` etc. i workflow och webhook
- [ ] Lägg till `businessType` i Registry-sheet
- [ ] Designa hur workflowet hanterar saknade flikar gracefully
- [ ] Testa med Lisas Klipp-sheet (salong) mot befintligt workflow
- [ ] Dokumentera sheet-struktur per branschtyp

---

## GitHub — så använder du det för dokumentation

GitHub är inte bara för kod. Du kan använda det för:
- **Levande dokument** som det här — versionshanterade och alltid tillgängliga
- **Ändringshistorik** — se exakt vad som ändrades och när
- **Enkelt att dela** — skicka en länk till en kollega eller samarbetspartner
- **Gratis och säkert** — perfekt för ett litet studio

**Så laddar du upp den här filen:**
1. Gå till github.com → ditt repo `jennyliljefeldt/cliporastudio-website`
2. Klicka på `Add file` → `Upload files`
3. Skapa gärna en mapp som heter `docs` och lägg filen där
4. Commit-meddelande: `Lägg till arkitektur-beslut`

---

*Skapad: April 2026 · Clipora Studio*
