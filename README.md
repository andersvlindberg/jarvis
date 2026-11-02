# 🤖 Jarvis

En röststyrd AI-assistent för Windows, i stil med Iron Mans Jarvis. Du pratar, den svarar med röst och gör saker på datorn åt dig, med en snygg HUD på skärmen.

> **Status:** Planeringsfas. Inget är byggt än, bara strukturen och planen. Se [`docs/PLAN.md`](docs/PLAN.md).

## Vision
- **Prata och få svar direkt**: tal-till-text, sedan Claude, sedan en röst tillbaka
- **Gör saker på datorn**: öppnar program, letar filer, kollar kalendern och mejlen
- **HUD**: ett genomskinligt fönster som visar vad Jarvis hör, tänker och gör
- **Säker från början**: allowlist för vad den får göra, och den frågar innan den raderar eller skickar något

## Arkitektur (v1)
```
[Push-to-talk] → mikrofon → tal-till-text
      → Claude (claude-agent-sdk) → MCP-verktyg (Windows-MCP, Gmail, Kalender, Obsidian)
      → svar → edge-tts (röst)
                    ↑
           HUD i pywebview-fönster
```

| Del | Val | Varför |
|---|---|---|
| Hjärna | `claude-agent-sdk` | Agent-loop och MCP-stöd direkt |
| Tal → text | `SpeechRecognition` först, sedan `faster-whisper` lokalt | Enkelt att komma igång, sedan gratis och privat |
| Text → tal | `edge-tts` | Neurala röster, gratis, låter bra |
| Händer | Windows-MCP | PowerShell, skärmdumpar, klick |
| HUD | `pywebview` + HTML/CSS | Lätt och snyggt, använder Edge WebView2 |
| Minne | Obsidian-valvet | Finns redan |

## Struktur
```
jarvis/
├── src/jarvis/      # Python-koden (tom tills vidare)
├── hud/             # HUD:en i HTML/CSS/JS
├── docs/PLAN.md     # Plan, roadmap och öppna frågor
├── .env.example     # Mall för nycklar (den riktiga .env committas aldrig)
└── requirements.txt # Paket som behövs (utkast)
```

## Kom igång (när det är dags)
```bash
cd ~/projects/jarvis
uv venv && source .venv/bin/activate
uv pip install -r requirements.txt
cp .env.example .env   # fyll i nycklar
```

## Inspiration
- [anuragnepal1999/JARVIS](https://github.com/anuragnepal1999/JARVIS): Linux-projekt med röstloop, HUD och flera agenter

---
Byggt av [Anders Lindberg](https://github.com/andersvlindberg) · Data & Analytics Engineering-student på IHM Business School
