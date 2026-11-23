# Scriptformaat

Hoe een script eruitziet: in de chat, in het portaal (klant en team) en voor de videobot. Gebaseerd op het montageprofiel
van de videobot (repo creatieve-motor, `VIDEO AGENT/06_MONTAGEPROFIEL.md`, hierna MP) en het scriptsjabloon
(`templates/video_project/01_SCRIPT.md`). Bronontwerp: repo AI-Weekend, `01-scriptbot/SCRIPTFORMAAT.md`.

## 1. Wat níet in het script staat: dat doet de videobot altijd zelf

Het script beschrijft alleen **inhoudelijke keuzes**. Techniek en de vaste afwerking liggen in het montageprofiel en komen
nooit in het script, zodat het kort blijft en de bot niets tegenstrijdigs voorschrijft:

| Altijd automatisch | Waar |
| --- | --- |
| Captions (hoofdletters, gezegd woord in accentkleur, vaste plek) | `03_CAPTIONS.md` |
| Zooms en beweging (push-in, zoomsprong op het nadrukwoord) | MP §3 |
| Cuts, overgangen (hook → body, naar en uit de CTA) | MP §2, §6 |
| Kleur per take en één look | MP §7 |
| Geluid: loudness, geluidseffecten (spaarzaam); muziek alleen als de klant het vraagt | MP §9 |
| Eindkaart na het laatste woord bij elke CTA | MP §10 |
| Huisstijl van de klant (kleuren, fonts, vormen) | MP §11, klantbrein |

## 2. Opbouw van een script

```
Script S<n> · <titel>
Invalshoek · onderwerp · locatie · in beeld (klant / acteur) · richtduur

Hooks         H1, H2 …   elke hook = een volledige video met dezelfde body en hetzelfde einde
Takes         T1, T2 …   body en einde, in volgorde
Feiten        elk gebruikt feit met bron en datum
```

### Hook (per hook)
- **Tekst**: de gesproken opening (±2,5–6,5 s, MP §1).
- **Visuele hook** (verplicht bij elke video, MP §4.1): *kicker* (begin van de hookzin), *grote woorden* met het gesproken
  woord waarop ze wisselen, eventueel *regel eronder*. Dit is de enige vaste toevoeging; zonder geluid moet de hook werken.
- **Filmen**: zoals bij een take.

### Take
| Veld | Inhoud |
| --- | --- |
| **Tekst** | wat er gezegd wordt (één gedachte per take) |
| **Filmen** | *kader* (wijd / medium / close-up), *plek* op de locatie, *actie* van de spreker (stapt naar de camera, wijst, houdt iets vast), en eventueel *extra beeld*: wat de videograaf los filmt voor deze take (±3-5 s per shot) |
| **Montage** | één naam uit de woordenlijst (§3) + **waarom** in één regel. Standaard `geen`. |

Richtduur (MP §1, beslist 22/11): standaard ±35 s in totaal (hook ±2,5–6,5 s, body ±15–30 s, CTA-module ±10 s, afsluiter
±2–6 s). Vraagt de gebruiker een andere lengte ("maak het 60 seconden"), dan volgt de bot die en zet hij ze in de kop.

### Feiten
Per feit: *wat* (letterlijk zoals in het script), *bron* (gesprek of mail in Client Check + datum), *take*. Een feit zonder
bron komt niet in het script. Bedragen met "vanaf" of "ongeveer"; een promotie alleen met einddatum.

## 3. Woordenlijst montage

**Standaard is `geen`**: spreker in beeld, en de automatische afwerking uit §1 doet de rest. Een toevoeging alleen als ze de
boodschap sterker of duidelijker maakt, altijd met een reden. Richtwaarde: in een gewoon script hebben de meeste takes `geen`.

| Naam | Wat de videobot doet | Wanneer wel | Basis |
| --- | --- | --- | --- |
| `geen` | spreker in beeld | standaard | MP §1 |
| `beeld` | schermvullend beeld over de stem dat het gezegde meteen toont | een eigenschap, claim of onzichtbaar probleem ("waterdicht", "warmteverlies"), of een resultaat dat je moet zien | MP §5 |
| `beeld_achter_spreker` | spreker vrijgesneden, beeld als paneel erachter | een concrete plaats of context ("in Gent", "op deze werf") | MP §5, §8 |
| `opsomming` | één beeld per punt, wisselt op het woord | 3 of meer punten die je kunt tonen | MP §5 |
| `overlay` | korte tekst in beeld die geen ondertitel is (bv. `STAP 1/3` bovenaan, of `15 JAAR GARANTIE` naast de spreker) | spaarzaam: alleen als die de structuur verduidelijkt; nooit als herhaling van de captions | MP §10b |
| `cta_module` | de tool van de klant (bv. de calculator) nagebouwd en geanimeerd, naast de spreker; prijs altijd als vork | de CTA verwijst naar de tool of website van de klant | MP §10 |
| `vrij` | idee buiten de lijst, in gewone woorden | alleen als niets uit de lijst past; de videobot vraagt het na in plaats van te gokken | |

Voor `beeld`, `beeld_achter_spreker` en `opsomming` staat bij **Filmen → extra beeld** welk beeld de videograaf draait. Lukt dat
niet op de locatie, dan zegt het script waar het beeld vandaan komt (foto's van de klant, website). Nooit stock (MP §5, VAST),
en binnen-/buitenbeeld volgt het onderwerp.

## 4. Drie weergaven van hetzelfde script

| Wie | Ziet |
| --- | --- |
| **Chat** (videograaf, planner) | alles: kop, hooks met visuele hook, takes met filmen en montage, feiten |
| **Portaal: klant** | alleen de tekst: titel, de hooks, daarna de takes als lopende tekst (beslist 22/11: geen locatie, filmen of montage) |
| **Portaal: team en videobot** | alles, ook als JSON (§6) |

Uit alle scripts van één aanvraag maakt de bot ook de **shootlijst per plek** voor de videograaf: wat er op elke plek gefilmd
wordt (spreker-takes en extra beeld), in de volgorde waarin hij filmt en niet in de volgorde van het script.

## 5. Voorbeeld (Dries Test, VERZONNEN feiten, alleen om het formaat te tonen)

> Dries Test heeft geen gesprekken in Client Check; de feiten hieronder zijn verzonnen voor dit voorbeeld en mogen nooit in
> een echt script.

**Aanvraag:** "Schrijf een script voor Dries Test over de renovatie van platte daken; we filmen op een werf in Lier met de
zaakvoerder."

**Feitencheck (wat de bot eerst toont)**

| Feit | Bron | Datum | Oordeel |
| --- | --- | --- | --- |
| Plat dak vanaf ongeveer € 85 per m² | onboardingcall | 12/11 | ✓ |
| 10 jaar garantie op de dichting | onboardingcall | 12/11 | ⚠ in een mail van 19/11 staat "15 jaar": welke klopt? |
| Gratis dakinspectie tot 31/12 | mail | 19/11 | ✓ nog geldig |
| "Snelste dakwerker van de regio" | – | – | ✗ geen bron: niet gebruiken |
| Prijscalculator op de website | onboardingtool | 10/11 | ✓ |

Na "15 jaar klopt" schrijft de bot:

---

**Script S1 · Wat kost een nieuw plat dak?**
Invalshoek: prijsvraag die elke eigenaar heeft · onderwerp: plat dak · locatie: werf Lier · in beeld: zaakvoerder (klant
acteert) · richtduur ±35 s

**H1** "Wat kost een nieuw plat dak in 2027?"
- Visuele hook: kicker `WAT KOST EEN NIEUW` · groot `PLAT` → `DAK` (op "dak") · eronder `IN 2027?`
- Filmen: medium, zaakvoerder op het dak, recht in de lens.

**H2** "Lekt je plat dak weer na de eerste regen?"
- Visuele hook: kicker `LEKT JE` · groot `PLAT` → `DAK` (op "dak") · eronder `WEER?`
- Filmen: medium, zaakvoerder bij de dakrand, wijst naar een oude dakbedekking.

| Take | Tekst | Filmen | Montage |
| --- | --- | --- | --- |
| T1 | "Bij ons begint een nieuw plat dak vanaf ongeveer 85 euro per vierkante meter." | Medium, op het dak | `geen` (het bedrag zit al in de captions) |
| T2 | "Daarin zit alles: de oude laag eraf, isolatie, en een nieuwe dichting." | Close-up handen bij de isolatieplaten; extra beeld: oude laag eraf, isolatie leggen, dichting branden (elk ±3 s) | `opsomming` (drie stappen die je kunt tonen) |
| T3 | "En op die dichting krijg je 15 jaar garantie." | Close-up, recht in de lens | `geen` |
| T4 | "Twijfel je over je dak? Tot eind december komen we gratis kijken." | Medium, stapt naar de camera | `geen` |
| T5 | "Bereken je prijs hieronder in een halve minuut." | Medium, wijst naar onder | `cta_module` (de calculator van de klant; prijs als vork) |

Feiten: "vanaf ongeveer 85 euro per vierkante meter" (onboardingcall 12/11, T1) · "15 jaar garantie" (mail 19/11, bevestigd
in de chat, T3) · "tot eind december gratis" (mail 19/11, geldig t/m 31/12, T4) · calculator (onboardingtool 10/11, T5).

---

**Klant ziet in het portaal:**
> **Wat kost een nieuw plat dak?**
> Opening 1: Wat kost een nieuw plat dak in 2027?
> Opening 2: Lekt je plat dak weer na de eerste regen?
> Bij ons begint een nieuw plat dak vanaf ongeveer 85 euro per vierkante meter. Daarin zit alles: de oude laag eraf,
> isolatie, en een nieuwe dichting. En op die dichting krijg je 15 jaar garantie. Twijfel je over je dak? Tot eind december
> komen we gratis kijken. Bereken je prijs hieronder in een halve minuut.

**Shootlijst videograaf (werf Lier)**
1. Op het dak, medium: H1, T1, T4, T5 · close-up: T3
2. Bij de dakrand, medium: H2
3. Extra beeld: oude laag eraf, isolatieplaten leggen (close-up handen, ook T2), dichting branden

## 6. JSON voor de videobot (zelfde inhoud)

```json
{
  "script": "S1",
  "titel": "Wat kost een nieuw plat dak?",
  "invalshoek": "prijsvraag die elke eigenaar heeft",
  "locatie": "werf Lier",
  "in_beeld": "klant",
  "richtduur_s": 35,
  "hooks": [
    {
      "id": "H1",
      "tekst": "Wat kost een nieuw plat dak in 2027?",
      "visuele_hook": { "kicker": "WAT KOST EEN NIEUW", "woorden": [{ "woord": "PLAT" }, { "woord": "DAK", "op": "dak" }], "eronder": "IN 2027?" },
      "filmen": { "kader": "medium", "plek": "op het dak", "actie": "recht in de lens" }
    }
  ],
  "takes": [
    {
      "id": "T2",
      "tekst": "Daarin zit alles: de oude laag eraf, isolatie, en een nieuwe dichting.",
      "filmen": { "kader": "close-up", "plek": "op het dak", "actie": "handen bij de isolatieplaten",
                  "extra_beeld": ["oude laag eraf", "isolatie leggen", "dichting branden"] },
      "montage": { "soort": "opsomming", "waarom": "drie stappen die je kunt tonen",
                   "items": [{ "op": "oude laag", "beeld": "oude laag eraf" }, { "op": "isolatie", "beeld": "isolatie leggen" }, { "op": "dichting", "beeld": "dichting branden" }] }
    }
  ],
  "feiten": [
    { "tekst": "vanaf ongeveer 85 euro per vierkante meter", "bron": "onboardingcall", "datum": "2026-11-12", "take": "T1" }
  ]
}
```
