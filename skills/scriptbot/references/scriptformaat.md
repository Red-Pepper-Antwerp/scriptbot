# Scriptformaat

Een script is **alleen tekst**: titel, 2 hooks en de takes. Geen filmen, geen montage, geen visuele hook: dat doen de
videograaf en de videobot zelf.

## Opbouw

```
S<n> · <titel>
Invalshoek: <één regel>

H1  <gesproken opening>
H2  <gesproken opening>      ← in één van de twee: "bereken het in 2 minuten"

T1  <zin>
T2  <zin>
…
Tn-1  <calculatorbody>        ← vast, vlak voor de CTA
Tn    <CTA: "Benieuwd …? … hieronder.">

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
- **H2** Lekt je plat dak weer na de eerste regen?

1. T1 Bij ons begint een nieuw plat dak vanaf ongeveer 85 euro per vierkante meter.
2. T2 Daarin zit alles: de oude laag eraf, isolatie, en een nieuwe dichting.
3. T3 Daarom hebben wij een gratis online calculator gemaakt.
4. T4 Je vult enkele gegevens in over jouw dak en de werken die je wil laten uitvoeren, en binnen 2 minuten krijg je al
   een eerste richtprijs.
5. T5 Zo weet je meteen met welk budget je ongeveer rekening moet houden.
6. T6 Benieuwd wat jouw dak kost? Bereken het hieronder.

Feiten: "vanaf ongeveer 85 euro per vierkante meter" (onboardingcall, 12/11)
Controle: Nieuw ✓ · 2 minuten in H1 ✓ · calculatorbody ✓

## JSON voor `script_zetten`

```json
{
  "titel": "Wat kost een nieuw plat dak?",
  "invalshoek": "de prijsvraag die elke eigenaar heeft",
  "hooks": [
    { "id": "H1", "tekst": "Wat kost een nieuw plat dak nu eigenlijk? Bereken het in 2 minuten." },
    { "id": "H2", "tekst": "Lekt je plat dak weer na de eerste regen?" }
  ],
  "takes": [
    { "id": "T1", "tekst": "Bij ons begint een nieuw plat dak vanaf ongeveer 85 euro per vierkante meter." },
    { "id": "T3", "tekst": "Daarom hebben wij een gratis online calculator gemaakt." }
  ],
  "feiten": [
    { "tekst": "vanaf ongeveer 85 euro per vierkante meter", "bron": "onboardingcall", "datum": "2026-11-12", "take": "T1" }
  ]
}
```
Geen `montage` en geen `filmen`: het portaal aanvaardt het zonder (dan geldt "alleen de spreker").
