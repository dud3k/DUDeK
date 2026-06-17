---
name: Workflow architect/implementer (OpenSpec)
description: Opus = architect (plan + openspec/changes/<slug>/), Sonnet = implementer. Zmiany w openspec/changes/<slug>/, identyfikowane slugiem.
type: reference
---
## Podział ról
- **Opus (architect)**: rozmowa z użytkownikiem, plan, folder `openspec/changes/<slug>/` w repo (przez `/opsx:propose`). NIE implementuje kodu.
- **Sonnet / Haiku (implementer)**: `git pull`, branch `task/<slug>` od `main`, zmiany w kodzie, `/opsx:archive` + PROGRESS.md (ostatni commit PRZED utworzeniem PR), PR. Szczegóły: `docs/workflow/IMPLEMENTER.md` w repo.
- **Recenzent**: tylko ocenia, nie modyfikuje repo. Szczegóły: `REVIEWER.md`.

## Format folderu zmiany OpenSpec
- Ścieżka: `openspec/changes/<slug>/`
- Pliki: `proposal.md` (cel + zakres), `design.md` (decyzje techniczne), `tasks.md` (checklist commitów), `specs/` (delty)
- Tworzony przez: `/opsx:propose` (w sesji Claude Code po `openspec init`)
- Archiwizowany przez: `/opsx:archive` jako ostatni commit w PR, PRZED merge (delty scalane do `openspec/specs/`; kod i spec trafiają na main razem)

## Ważne
- W plan mode Opus NIE może utworzyć fizycznego folderu zmiany — robi to PO ExitPlanMode, ZANIM odda pałeczkę Sonnetowi.
- Folder zmiany musi być zacommitowany na `main` ZANIM Sonnet zrobi `git pull` — inaczej nie zobaczy specyfikacji.
- Stan bieżący systemu: `openspec/specs/` (aktualizowany przez `/opsx:archive`).
- Rozpoznanie roli: `CLAUDE.md` § „Krok 0" na podstawie identyfikatora modelu.
- ADR (decyzje architektoniczne): `docs/architecture/`, indeks bieżących w `ADR_INDEX.md`. Niemutowalne — zmiana = nowy ADR zastępujący stary.
- Legacy fallback (bez OpenSpec): szablony TASK_NNN w `docs/tasks/legacy/`.
