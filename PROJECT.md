# PROJECT.md — jedno źródło prawdy konfiguracji kitu

Wypełnij tę tabelę **raz**, przy zakładaniu nowego projektu. Potem powiedz Claude Code:
**„zainicjuj kit"** — Claude podmieni wszystkie `{{PLACEHOLDER}}` w plikach kitu wartościami z tej
tabeli (literalny replace, bez przepisywania plików) i usunie nieużywane sekcje opcjonalne.

Ten plik **zostaje** w repo po inicjalizacji jako trwały rejestr wartości konfiguracyjnych.

---

## Wartości obowiązkowe (~7)

| Placeholder | Wartość (wpisz tutaj) | Co to | Przykład |
|---|---|---|---|
| `{{PROJECT_NAME}}` | | Nazwa projektu | `Mój Tracker Wydatków` |
| `{{PROJECT_DESCRIPTION}}` | | 1–2 zdania opisu | `aplikacja webowa do śledzenia wydatków z importem CSV` |
| `{{STACK}}` | | Runtime + kluczowe biblioteki | `Python 3.12, FastAPI, SQLite, React` |
| `{{WORKFLOW_SUMMARY}}` | | Jednolinkowy przepływ danych | `CSV → parser → DB → REST API → React UI` |
| `{{COMMANDS_SECTION}}` | | Najważniejsze komendy CLI (markdown, code blocks) | patrz przykład pod tabelą |
| `{{VALIDATION_COMMAND}}` | | Komenda walidacji składni | `python -m py_compile <plik>` / `node --check <plik>` / `tsc --noEmit` |
| `{{TEST_COMMAND}}` | | Komenda testów | `pytest` / `npm test` |
| `{{COMMIT_SCOPES}}` | | Dopuszczalne scope w Conventional Commits | `api, ui, db, parser, ci, docs` |
| `{{USER_CONTEXT}}` | | Krótko: co robisz z projektem | `prowadzę budżet domowy, automatyzuję import z banku` |

**Przykład `{{COMMANDS_SECTION}}`** (wklej gotowy markdown w kolumnie wartości lub tutaj):
```markdown
### Uruchomienie
\`\`\`bash
uvicorn app:main --reload      # serwer dev
pytest                          # testy
\`\`\`
```

---

## Wartości opcjonalne (usuwane przy init, jeśli puste)

Zostaw puste, jeśli nie dotyczą — Claude usunie odpowiednią sekcję `<!-- OPTIONAL:... -->` z plików.

| Placeholder | Wartość | Co to |
|---|---|---|
| `{{DEPLOY_INFO}}` | | Jak/gdzie deploy (np. `GitHub Pages po merge do main`) |
| `{{REPO_URL}}` | | URL repo GitHub (np. `https://github.com/dud3k/nazwa`) |
| `{{APP_URL}}` | | URL działającej aplikacji |

---

## Defaulty (zmień tylko jeśli inaczej — NIE są placeholderami)

Te wartości są już wpisane na stałe w plikach kitu. Edytuj ręcznie tylko w razie odstępstwa:

| Ustawienie | Default | Gdzie zmienić jeśli inaczej |
|---|---|---|
| Branch bazowy | `main` | znajdź/zamień `main` → `master` we wszystkich plikach |
| Język commitów | `polski` | `CLAUDE.md`, `AGENTS.md`, `REVIEWER.md` |
| Właściciel | `(Twój nick / imię)` | `CLAUDE.md` § Kontekst użytkownika |
| System | `(Twój OS)` | `CLAUDE.md` § Kontekst użytkownika |
| Tryb pracy | `team` (GitHub + PR) | — (solo poza standardem; zleć ad hoc gdy potrzeba) |
| Warstwa zmian | `OpenSpec` | `docs/tasks/legacy/` — szablony TASK_NNN dla projektów świadomie rezygnujących z OpenSpec |
