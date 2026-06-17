# TASK_NNN: [Tytuł zadania]

## Cel

[2–4 zdania: CO robimy i DLACZEGO. Nie opisuj rozwiązania — opisz problem i pożądany efekt z perspektywy użytkownika.]

## Zakres zmian

**Modyfikowane pliki:**
- `<plik/ścieżka/do/pliku.ext>`

**NIE modyfikujemy** (explicit wykluczenie — chroni przed scope creep):
- `<inny/plik.ext>`

## Specyfikacja

Podziel na części A/B/C lub etapy 1/2/3 — tak, żeby każda była małą osobną zmianą.

### 1. [Nazwa pierwszej zmiany]

[Opis TECHNICZNY: co dokładnie ma powstać, jak nazwać funkcję/komponent, co ma w środku.]

- Lokalizacja: `<plik:linia>` (jeśli modyfikacja istniejącego kodu)
- Reuse: użyj istniejącej `<funkcjaX()>` z `<plik:linia>` zamiast pisać nową
- Sygnatura (przykład, nie gotowy kod do wklejenia):

```javascript
function nowaFunkcja(param1, param2) {
  // 1. Walidacja
  // 2. Transformacja
  // 3. Zapis
}
```

### 2. [Druga zmiana]

[...]

### 3. [Trzecia zmiana]

[...]

## Testy

Kroki weryfikacji — każdy WYKONYWALNY. Zakaz „przetestuj manualnie" bez konkretów.

1. Walidacja składni: `{{VALIDATION_COMMAND}}` — brak błędów.
2. Testy jednostkowe: `{{TEST_COMMAND}}` — N passed, 0 failed.
3. Smoke test funkcjonalny:
   - [Krok 1 — jakie wejście]
   - [Krok 2 — jaka oczekiwana reakcja]
4. Przypadek brzegowy 1: [opis + oczekiwany rezultat]
5. Przypadek brzegowy 2: [opis + oczekiwany rezultat]
6. Regresja: istniejąca funkcja X dalej działa ([jak sprawdzić]).

## Uwagi

- [Zależności między zmianami — co musi być pierwsze]
- [Migracje danych jeśli potrzebne]
- [Decyzje do potwierdzenia przez architekta jeśli coś zaskoczy implementera]
- [Linki do ADR jeśli decyzja jest tam uzasadniona]

## Rozbicie na commity (sugerowane)

Każdy commit powinien być logicznie zamknięty i przechodzić testy.

1. `<typ>(<scope>): <krótki opis zmiany 1>`
2. `<typ>(<scope>): <krótki opis zmiany 2>`
3. `<typ>(<scope>): <krótki opis zmiany 3>`
4. `docs: aktualizacja PROGRESS.md`

## Pliki źródłowe

Whitelist dla implementera — tylko te pliki mogą być modyfikowane.

- `<plik1.ext>` — [krótki opis zmiany]
- `<plik2.ext>` — [krótki opis zmiany]
- `PROGRESS.md` — aktualizacja po zakończeniu TASK (obowiązkowe)
