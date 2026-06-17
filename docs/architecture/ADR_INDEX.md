# Indeks ADR — bieżące decyzje wg obszaru

Ten plik daje architektowi **szybki widok „co obowiązuje teraz"**, bez czytania zastąpionych ADR-ów.

<!--
ZASADY:
- Architekt czyta TYLKO aktualne ADR-y z kolumny "Aktualny ADR".
- ADR-y są NIEMUTOWALNE: gdy decyzja się zmienia, powstaje NOWY ADR zastępujący stary.
  Stary NIE jest kasowany — dostaje status "Zastąpione przez ADR_MMM" i ląduje w kolumnie "Zastąpione".
  Historia ("dlaczego zmieniliśmy") jest celowo zachowana — chroni przed powrotem do odrzuconych opcji.
- Po każdym nowym / zastępującym ADR architekt aktualizuje tę tabelę.
- Jeden wiersz = jeden obszar. Jeśli pojawia się nowy obszar — dodaj wiersz.
-->

| Obszar | Aktualny ADR | Status | Zastąpione |
|---|---|---|---|
| [Backend / runtime] | ADR_NNN | Zaakceptowano | — |
| [Frontend] | ADR_NNN | Zaakceptowano | — |
| [Sync / transport] | ADR_NNN | Zaakceptowano | — |
| [CI/CD] | — | — | — |
| [Dane / model] | — | — | — |

<!-- Przykład wypełnionego wiersza (z KA Scraper):
| Sync / transport | ADR_004 | Zaakceptowano | ADR_002 |
-->
