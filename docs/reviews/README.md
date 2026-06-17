# docs/reviews/

Folder na artefakty oceny i weryfikacji. Dwa rodzaje plików:

| Plik | Kto pisze | Co zawiera |
|---|---|---|
| `review_<slug>_A.md` | Recenzent (TYP A) | Recenzja folderu zmiany OpenSpec przed implementacją |
| `review_ADR_NNN.md` | Recenzent (TYP A) | Recenzja decyzji architektonicznej |
| `review_<slug>_code.md` | Recenzent (TYP B) | Recenzja kodu z PR przed merge |
| `probe_*.md` | Architekt (Faza 0) | Wynik mikro-sondy: założenie → co sprawdzono → wynik → wniosek do zmiany |

Konwencje i format recenzji: [REVIEWER.md](../../REVIEWER.md).
Faza 0 (sonda): [docs/workflow/ARCHITECT.md](../workflow/ARCHITECT.md).

Recenzent zapisuje swój plik, ale **nie commituje** — git należy do właściciela.
