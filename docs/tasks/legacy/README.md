# docs/tasks/legacy — Szablony TASK_NNN (legacy)

Szablony w tym folderze zostały **zastąpione przez warstwę OpenSpec** (`openspec/changes/<slug>/`).

Używaj ich, gdy projekt świadomie rezygnuje z OpenSpec (np. bardzo mały projekt, prototyp jednorazowy,
projekt bez Node.js w środowisku deweloperskim). W standardowym nowym projekcie z kitem v2 korzystasz
z komend `/opsx:propose` i `/opsx:archive` zamiast ręcznego tworzenia plików TASK_NNN.md.

## Kiedy można użyć legacy TASK_NNN

- Projekt jest tak mały, że `openspec init` to overkill (np. skrypt jednorazowy <100 linii).
- Środowisko deweloperskie nie ma Node.js i instalacja npm jest niemożliwa lub niepożądana.
- Migracja istniejącego projektu z kitu v1 — można kontynuować z TASK_NNN do momentu, aż projekt
  będzie gotowy na openspec init.

## Zawartość

- `TASK_template.md` — pusty szablon do ręcznego wypełnienia
- `TASK_example.md` — przykład wypełnionego TASK (z projektu KA Scraper)
