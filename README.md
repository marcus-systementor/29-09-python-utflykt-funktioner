# Utflyktsplaneraren – repetera funktioner i Python

Du bygger ett litet terminalprogram för att planera en utflykt. Börja med en enda sak att packa. Efter hand samlar du upprepade kodstycken i `functions`, skickar in `parameters`, använder `return`, arbetar med `scope` och delar till sist upp programmet i två filer (`modules`). Du skriver själv koden. Ingen `class` eller externa paket behövs.

**Detta är självstudier, inte examination.** Arbeta uppifrån och ned. Varje steg avslutas med en kontroll och en egen `commit`. Om du kör fast: läs [HJALP.md](HJALP.md), spara din fråga i [REFLECTION.md](REFLECTION.md) och fortsätt med det du kan.

## Starta

1. Öppna lärarens publika GitHub-template. Välj **Use this template → Create a new repository** och skapa ett eget **private** repo.
2. Klona ditt eget repo, öppna mappen i VS Code och börja i `trip_planner.py`.
3. Kör `python trip_planner.py` (eller `python3`/`py` beroende på dator). Den tomma startfilen ska köras utan fel.
4. Efter varje steg: kör programmet, kontrollera output och gör en `commit`. `push` före lunch och i slutet av dagen.

## Förslag till dagsplan, 09:00–16:00

| Tid | Aktivitet |
| --- | --- |
| 09:00–09:20 | Klona repo, läs instruktionerna och kör filen. |
| 09:20–10:05 | Steg 1: variabler och en enkel utskrift. |
| 10:05–10:20 | Rast. |
| 10:20–11:00 | Steg 2: första funktionen och funktionsanrop. |
| 11:00–11:40 | Steg 3: `parameters` och `return`. |
| 11:40–12:40 | Lunch. |
| 12:40–13:20 | Steg 4: flera saker och en loop. |
| 13:20–14:05 | Steg 5: summera med en funktion; upplev `scope`. |
| 14:05–14:20 | Rast. |
| 14:20–15:00 | Steg 6: `if` och återanvändbara kontroller. |
| 15:00–15:35 | Steg 7: dela upp i `modules` och kör igen. |
| 15:35–16:00 | Skriv reflektion, `commit`, `push`. |

Om du behöver mer tid, prioritera förståelsen av steg 1–5. Steg 7 är ett bra mål för den som hunnit längre.

## Steg 1 – En sak att packa

Planera en utflykt med ett namn, till exempel `Skogsutflykt`. Skapa variabler för utflyktens namn, en sak att packa (`item_name = "Water bottle"`), dess vikt i gram (`item_weight = 500`) och antalet (`quantity = 2`). Skriv ut utflyktens namn och en tydlig rad som visar saken, antal och total vikt. Räkna med `*`; skriv inte in totalen för hand.

**Kontroll:** Två flaskor på 500 gram vardera ger 1000 gram. Ändra antalet till 3 och kontrollera att vikten blir 1500 gram utan att du ändrar beräkningen.

**Commit:** `Add first packing item`

## Steg 2 – Din första function

Skriv en function `show_heading()` som skriver ut en rubrik för utflykten. Anropa funktionen från programmet. Kör det och prova sedan att tillfälligt ta bort anropet: körs koden i funktionen ändå? Sätt tillbaka anropet. Funktionen kan använda en fast rubrik som `Packing list` just nu.

**Kontroll:** Rubriken skrivs ut exakt en gång när funktionen anropas. Förklara för dig själv skillnaden mellan att *definiera* och att *anropa* en function.

**Commit:** `Add heading function`

## Steg 3 – Parameters och return

Ändra rubrikfunktionen så att den tar utflyktens namn som `parameter`, exempelvis `show_heading(trip_name)`. Anropa den med minst två olika namn, ett i taget, och se att rubriken ändras.

Skriv sedan `calculate_item_weight(weight_grams, quantity)` som **returnerar** total vikt. Låt kod utanför funktionen skriva ut resultatet. Jämför med en variant som bara använder `print` inne i funktionen: kan du använda det utskrivna värdet i en ny beräkning?

**Kontroll:** `calculate_item_weight(500, 2)` ger talet `1000`, och `calculate_item_weight(200, 3)` ger `600`. Funktionen ska inte själv fråga efter input eller skriva ut totalen.

**Commit:** `Calculate weight with parameters`

## Steg 4 – Flera packade saker

Lägg tre packade saker i en `list`. Varje sak är en `dict` med nycklarna `name`, `weight_grams` och `quantity`. Börja gärna med följande värden:

| Sak | `weight_grams` | `quantity` |
| --- | ---: | ---: |
| `Water bottle` | 500 | 2 |
| `Sandwich` | 200 | 3 |
| `Rain jacket` | 400 | 1 |

Använd en `for`-loop. Visa namn och vikt för varje sak genom att anropa din `calculate_item_weight` i loopen. Använd samma funktion för alla tre sakerna.

**Kontroll:** Radvikterna ska bli 1000, 600 respektive 400 gram. Lägg till en fjärde sak i listan och kontrollera att den visas utan att du lägger till ett nytt `print` för just den saken.

**Commit:** `List packed items`

## Steg 5 – Summera och förstå scope

Skriv `calculate_total_weight(items)` som går igenom listan och **returnerar** den sammanlagda vikten. Skriv ut resultatet efter funktionsanropet. Skapa en lokal variabel `total = 0` **inne i funktionen** och öka den i loopen. Använd `calculate_item_weight()` för varje sak i listan.

När det fungerar: prova tillfälligt att läsa `total` direkt utanför funktionen och kör programmet. Vad händer? Ta sedan bort den raden så att programmet fungerar igen. Lägg i stället funktionens `return`-värde i en variabel utanför funktionen.

**Kontroll:** De tre exempelsakerna väger tillsammans 2000 gram. Funktionen ska ge 0 för en tom lista. Ändra vikten på en sak och kontrollera att summan följer med.

**Commit:** `Calculate total packing weight`

## Steg 6 – Kontrollera maxvikt

Skapa en variabel `weight_limit = 2500`. Skriv `is_within_limit(total_weight, limit)` som returnerar `True` eller `False`. Använd resultatet i ett `if`/`else` för att skriva om packningen ryms inom maxvikten. Lägg till ett meddelande om hur många gram som är kvar om den ryms, annars hur många gram som måste tas bort.

**Kontroll:** 2000 av 2500 gram ger `True` och 500 gram kvar. Exakt 2500 gram ska också vara tillåtet. 2600 gram ger `False` och 100 gram att ta bort. Prova värdena genom att ändra gränsen eller sakernas vikter.

**Commit:** `Check packing weight limit`

## Steg 7 – Dela upp i modules

Skapa en ny fil `packing.py`. Flytta de tre återanvändbara beräkningsfunktionerna `calculate_item_weight`, `calculate_total_weight` och `is_within_limit` till den filen. Låt `trip_planner.py` sköta listan, funktionsanropen och utskrifterna. Använd `from packing import ...` för att importera funktionerna. `show_heading` kan stanna i huvudfilen.

**Kontroll:** Kör `python trip_planner.py` från mappen där båda filerna ligger. Programmet ska ge samma resultat som före flytten. Ändra maxvikten och kontrollera att logiken fortfarande fungerar. Om du får `NameError`, kontrollera stavningen på importerna och att inga anrop försvann.

**Commit:** `Move packing calculations to module`

## Avslut

Svara på [REFLECTION.md](REFLECTION.md). Skriv vilka steg du hann och vilken fråga du vill ta upp med läraren. Kör programmet en sista gång, kontrollera `git status`, gör en `commit` för reflektionen och `push` till ditt repo.

**Commit:** `Reflect on function practice`

## Frivilligt tillägg: filer och JSON

**Bara om du redan gått igenom filhantering eller vill utforska något nytt.** Kursplanen bekräftar inte att detta undervisats före OOP. Spara packlistan till `packing_list.json` med standardmodulen `json` och läs tillbaka den när programmet startar. Börja gärna med en separat fil och fråga läraren innan du kopplar in den i huvudprogrammet. Lägg aldrig personuppgifter eller lösenord i filen.

Ett enklare första steg är att öppna en `.txt`-fil med `with open(..., encoding="utf-8")` och skriva en rad för varje sak. Filformat som XML, YAML och Excel ingår inte i kärnuppgifterna.
