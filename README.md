# Digital Restaurangassistent

En live-demo av en AI-driven restaurangassistent byggd för att hjälpa restauranger att svara på vanliga frågor från gäster direkt på hemsidan.

## Live demo

[Öppna demon här](https://jennyliljefeldt.github.io/restaurant-assistant-demo/)

## Vad assistenten kan göra

- Visa dagens lunch
- Svara på frågor om öppettider
- Besvara vanliga frågor om restaurangen
- Starta en bokningsdialog
- Ge snabb hjälp direkt i en chat-widget på sidan

## Exempel på frågor

- Vad är dagens lunch?
- Är ni öppna nu?
- Kan jag boka bord kl 18 för fyra personer?
- Har ni vegetariskt?
- Finns glutenfritt?
- Kan man ta med hund?

## Teknik

Projektet består av:

- **Frontend:** HTML, CSS, JavaScript
- **Automation/backend:** n8n
- **AI-agent:** LLM via n8n
- **Datakällor:** Google Sheets
- **Hosting:** GitHub Pages

## Hur det fungerar

1. Besökaren skriver i chatten på webbsidan
2. Meddelandet skickas till ett webhook-flöde i n8n
3. AI-agenten tolkar frågan
4. Assistenten använder rätt verktyg för att hämta information, till exempel lunchmeny eller öppettider
5. Svaret skickas tillbaka till chatten på sidan

## Funktioner i demon

- Chat-widget i hörnet av sidan
- Välkomstmeddelande
- “Assistenten skriver...”
- Snabbknappar för vanliga frågor
- Enkel konversationshistorik
- FAQ-svar för restaurangrelaterade frågor
- Live publicerad demo

## Syfte

Projektet är byggt som en produktdemo för att visa hur en digital restaurangassistent kan:

- spara tid för personalen
- minska återkommande frågor
- ge gäster snabb hjälp
- skapa en modernare kundupplevelse på hemsidan

## Kontakt

Byggd av **Clipora Studio**  
Kontakt: [jenny.liljefeldt@gmail.com](mailto:jenny.liljefeldt@gmail.com)
