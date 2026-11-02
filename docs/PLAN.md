# Jarvis: plan och roadmap

## Roadmap
### v0: Grund (nu)
- [x] Repo, struktur, README och plan
- [ ] Bestäm hur Jarvis loggar in mot Claude: API-nyckel eller Claude Code-inloggning (kolla kostnad och villkor)
- [ ] Kolla Python-version, och om Jarvis ska köras i Windows eller WSL (mikrofon och ljud är enklast i Windows)

### v1: Prata och få svar
- [ ] Push-to-talk med en tangent, tal-till-text och Claude som svarar med edge-tts
- [ ] Enkel HUD som visar "lyssnar / tänker / pratar" och texten
- [ ] `START.bat` som startar allt

### v2: Händer
- [ ] Koppla in MCP-verktyg: Windows-MCP, Kalender, Gmail, Obsidian
- [ ] Allowlist för vad Jarvis får göra, och en fråga innan något raderas eller skickas
- [ ] Logg över allt Jarvis gör

### v3: Smartare
- [ ] `faster-whisper` lokalt (gratis och privat)
- [ ] Wake word ("Hey Jarvis") med `openwakeword`, först när resten är stabilt
- [ ] Proaktiva påminnelser (morgonbrief, möten, deadlines)
- [ ] Minne i Obsidian

## Viktiga beslut
- **Push-to-talk före wake word.** Wake word ger många falska träffar, och det är där liknande projekt brukar fastna.
- **Säkerhet först.** Allowlist från dag 1. Inga nycklar i koden, bara i `.env` (som ligger i .gitignore).
- **Kostnad.** En röstloop som alltid är på betyder anrop hela tiden. Därför push-to-talk i v1.

## Öppna frågor
- Auth och kostnad för `claude-agent-sdk` (se code.claude.com/docs)
- Vilken röst i edge-tts (svenska eller engelska)?
- HUD-stil: Iron Man-blå eller Anders gröna design?

## Portfölj och LIA
Det här är ett bra projekt att visa upp: event, insamling, tolkning och handling. Det kopplar ihop AI-agenter, API:er och data.
