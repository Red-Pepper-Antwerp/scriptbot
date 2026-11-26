# Scriptformaat

Een script is de tekst (titel, 2 hooks, de takes) met per hook en per take één concrete regel **Filmen**. Geen
montage en geen visuele hook: dat doet de videobot zelf.

## Opbouw

```
S<n> · <titel>
Invalshoek: <één regel>

H1  <gesproken opening>      Filmen: …
H2  <gesproken opening>      Filmen: …   ← in één van de twee: "bereken het in 2 minuten"

T1  <zin>                    Filmen: …
…
calculatorbody               Filmen: niets, alleen een schone audiotake
Tn  <CTA>                    Filmen: …

Shootlijst per plek (alle scripts samen)

Feiten: <feit> (<bron>, <datum>) · …
Controle: Nieuw ✓ · 2 minuten in H<x> ✓ · calculatorbody ✓
```

Elke hook is een aparte video met dezelfde takes. Richtduur standaard ±35 s, of wat de gebruiker vraagt.

## Feiten
Per feit: *wat* (letterlijk zoals in het script), *bron* (gesprek of mail in Client Check + datum). Een feit zonder bron komt
niet in het script. Bedragen met "vanaf" of "ongeveer"; een promotie alleen met einddatum.

## Wat de klant ziet in het portaal
De titel, de hooks als "Opening 1" en "Opening 2", en daarna de takes als lopende tekst.

## Voorbeeld (testklant, VERZONNEN feiten, alleen om het formaat te tonen)

**S1 · Wat kost een nieuw plat dak?**
Invalshoek: de prijsvraag die elke eigenaar heeft

- **H1** Wat kost een nieuw plat dak nu eigenlijk? Bereken het in 2 minuten.
  Filmen: op het dak, recht in de lens, veel ruimte boven het hoofd.
- **H2** Lekt je plat dak weer na de eerste regen?
  Filmen: bij de dakrand, wijst naar de oude, gebarsten dakbedekking.

| Take | Tekst | Filmen |
| --- | --- | --- |
| T1 | Bij ons begint een nieuw plat dak vanaf ongeveer 85 euro per vierkante meter. | Op het dak, recht in de lens. |
| T2 | Daarin zit alles: de oude laag eraf, isolatie, en een nieuwe dichting. | B-roll: oude dakbedekking lostrekken (5 s) · isolatieplaat leggen (5 s) · dichting branden (5 s). |
| T3 | Daarom hebben wij een gratis online calculator gemaakt. | Niets: alleen een schone audiotake (calculator over het scherm). |
| T4 | Je vult enkele gegevens in over jouw dak en de werken die je wil laten uitvoeren, en binnen 2 minuten krijg je al een eerste richtprijs. | Idem. |
| T5 | Zo weet je meteen met welk budget je ongeveer rekening moet houden. | Idem. |
| T6 | Benieuwd wat jouw dak kost? Bereken het hieronder. | Op het dak, stapt naar de camera, wijst naar onder. |

Feiten: "vanaf ongeveer 85 euro per vierkante meter" (onboardingcall, 12/11)
Controle: Nieuw ✓ · 2 minuten in H1 ✓ · calculatorbody ✓ · filmen ✓

**Shootlijst (werf)**
1. Op het dak, recht in de lens: H1, T1, T6
2. Bij de dakrand: H2
3. B-roll: oude dakbedekking lostrekken · isolatieplaat leggen · dichting branden (elk ±5 s)
4. Schone audiotake: T3-T5

## JSON voor `script_zetten`

```json
{
  "titel": "Wat kost een nieuw plat dak?",
  "invalshoek": "de prijsvraag die elke eigenaar heeft",
  "hooks": [
    { "id": "H1", "tekst": "Wat kost een nieuw plat dak nu eigenlijk? Bereken het in 2 minuten.",
      "filmen": { "plek": "op het dak", "actie": "recht in de lens, veel ruimte boven het hoofd" } },
    { "id": "H2", "tekst": "Lekt je plat dak weer na de eerste regen?" }
  ],
  "takes": [
    { "id": "T2", "tekst": "Daarin zit alles: de oude laag eraf, isolatie, en een nieuwe dichting.",
      "filmen": { "plek": "op het dak", "actie": "alleen b-roll",
                  "extra_beeld": ["oude dakbedekking lostrekken (5 s)", "isolatieplaat leggen (5 s)", "dichting branden (5 s)"] } },
    { "id": "T3", "tekst": "Daarom hebben wij een gratis online calculator gemaakt.",
      "filmen": { "actie": "niets filmen: alleen een schone audiotake (calculator over het scherm)" } }
  ],
  "feiten": [
    { "tekst": "vanaf ongeveer 85 euro per vierkante meter", "bron": "onboardingcall", "datum": "2026-11-12", "take": "T1" }
  ]
}
```
`filmen` per hook en take: `plek`, `actie`, en bij b-roll `extra_beeld` (één shot per gezegd ding). Geen `montage`.
