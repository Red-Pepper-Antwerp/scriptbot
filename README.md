# Scriptbot (Revenue Lab)

Plugin voor Claude Code waarmee het team (videograaf, planner) advertentiescripts schrijft voor klanten van Revenue Lab:

1. In gewone taal vragen, bv. *"Schrijf twee scripts voor Bouwbedrijf Voorbeeld over de winterpromotie, we filmen op de werf in Gent."*
2. De bot controleert de feiten in **Client Check** (telkens vers) en kijkt naar de scripts die de klant al heeft.
3. Je kiest een invalshoek; de bot schrijft het script (alleen tekst: 2 hooks en de takes, met de vaste calculatorbody) en controleert dat het nog niet gebruikt is.
4. Na je akkoord in de chat staat het script **finaal in het portaal**. De klant leest het via de scriptlink (die je zelf
   doorstuurt), keurt goed of geeft opmerkingen.
5. *"Verwerk de opmerkingen van de klant op Bouwbedrijf Voorbeeld"*: de bot past aan, na je akkoord staat het nieuwe script klaar.
6. Na het akkoord van de klant leest de videobot het script als montageplan.

## Installeren met één prompt (aanrader)

Plak dit in een chat van Claude Code (VS Code, de desktop-app of de terminal). Claude doet de installatie zelf; jij logt
op het einde alleen in.

```text
Installeer voor mij de Scriptbot van Revenue Lab (een plugin voor Claude Code). Doe het zelf met de terminal, stap voor
stap, en zeg in gewone taal wat je doet. Verander niets anders op mijn computer en verstuur niets.

1. Zoek het programma claude. Probeer in deze volgorde: `claude`, `~/.local/bin/claude`, `~/.claude/local/claude`, het
   nieuwste `~/.vscode/extensions/anthropic.claude-code-*/resources/native-binary/claude`. Gebruik wat werkt (`--version`).
2. Kijk of ik bij de repo kan: `GIT_TERMINAL_PROMPT=0 git ls-remote https://github.com/Red-Pepper-Antwerp/scriptbot.git`.
   Lukt dat niet, stop dan en zeg me dat ik de beheerder van het portaal moet vragen om toegang tot Red-Pepper-Antwerp/scriptbot op GitHub.
3. Voeg de marketplace toe: `<claude> plugin marketplace add Red-Pepper-Antwerp/scriptbot` (bestaat ze al:
   `<claude> plugin marketplace update revenuelab`). Installeer dan: `<claude> plugin install scriptbot@revenuelab` (staat
   hij er al: `<claude> plugin update scriptbot@revenuelab`).
4. Kijk met `<claude> mcp list` naar plugin:scriptbot:client-check en plugin:scriptbot:revenuelab-portaal.
5. Zeg me tot slot precies wat ik nog moet doen:
   a. een NIEUWE chat van Claude Code openen (de plugin laadt alleen bij de start van een chat);
   b. daar /mcp typen, bij elke koppeling met "needs authentication" kiezen voor Authenticate, en in de browser inloggen
      met mijn account van Red Pepper (zelfde login als Client Check);
   c. als test typen: "Zoek Dries Test in het portaal en zeg hoeveel scripts hij heeft. Alleen lezen."
   Zegt de test "geen lid van het portaal", dan vraag ik de beheerder van het portaal om me toe te voegen.
```

## Installeren met de hand

Je hebt nodig: Claude Code (desktop-app, tab Code, of de terminal), toegang tot deze repo op GitHub, een account in Client
Check en lidmaatschap van het portaal (vraag de beheerder).

In Claude Code:

```
/plugin marketplace add Red-Pepper-Antwerp/scriptbot
/plugin install scriptbot@revenuelab
```

Daarna eenmalig inloggen: typ `/mcp`, kies **client-check** en log in de browser in met je account van Red Pepper; doe
hetzelfde voor **revenuelab-portaal**. Geen sleutels of wachtwoorden op je laptop: alles loopt met je eigen login.

Bijwerken: `/plugin marketplace update revenuelab`.

## Wat erin zit

| Pad | Wat |
| --- | --- |
| `skills/scriptbot/SKILL.md` | de werkwijze en de regels |
| `skills/scriptbot/references/stijl.md` | de schrijfstijl van Revenue Lab: soorten scripts, hooks, toon, lengte, wat nooit voorkomt |
| `skills/scriptbot/references/scriptformaat.md` | het scriptformaat: titel, 2 hooks en de takes (alleen tekst), met het JSON-formaat voor het portaal |
| `.mcp.json` | de koppelingen: Client Check (`copilot-mcp`) en het portaal (`portaal-mcp`), allebei met OAuth |
| `.claude-plugin/` | de plugin en de marketplace `revenuelab` |

Ontwerp en beslissingen: repo AI-Weekend, `01-scriptbot/`. Het portaal: repo revenuelab-portaal, `docs/08_PORTAAL.md` §15.
