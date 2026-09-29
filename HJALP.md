# Hjälp när något inte fungerar

- Spara filen och kör programmet från repots mapp. Läs felmeddelandets sista rad och kontrollera fil och radnummer.
- Kör ett steg i taget. Om du precis flyttat kod, kontrollera att `packing.py` ligger i samma mapp som `trip_planner.py`.
- Skriv ut värden med `print(value, type(value))` när du är osäker på typen eller värdet.
- Om en funktion ger `None`: kontrollera att du använder `return` där ett värde ska skickas tillbaka.
- Om en funktion ger fel antal argument: jämför funktionsdefinitionens `parameters` med värdena i anropet.
- Om du får `NameError`: kontrollera stavning, `scope` och eventuella `import`-rader.
- Prova små testvärden: en sak i listan, sedan två, sedan en tom lista. Kontrollera gränsen för maxvikten.
- Skriv i `REFLECTION.md` vad du provat om du fastnar. Du kan fortfarande göra en `commit` av fungerande delar.

## Git efter ett steg

```bash
git status
git add trip_planner.py REFLECTION.md
git commit -m "Describe completed step"
git push
```

När du har skapat `packing.py` måste du lägga till den också: `git add packing.py`. Du kan välja bara filer du faktiskt ändrat.
