# {{PROJECT_NAME}} — Instrukcje dla Claude Code

> **⚙️ Rozwijasz sam framework DUDeK (a nie używasz go w projekcie)?** → przeczytaj
> [`meta/MAINTAINING.md`](meta/MAINTAINING.md) i pomiń routing konsumenta poniżej. Sekcje „Krok 0",
> „Warstwa 0 — Discovery" i „zainicjuj kit" dotyczą projektów *zbudowanych z* DUDeK, nie rozwoju samego DUDeK.

## Krok 0 — rozpoznaj swoją rolę (WYKONAJ PRZED CZYMKOLWIEK INNYM)

Sprawdź w sekcji Environment swojego kontekstu, jakim modelem jesteś (linia typu „You are powered by the model named ...").

- **Opus (`claude-opus-*`)** → jesteś ARCHITEKTEM. Przeczytaj [docs/workflow/ARCHITECT.md](docs/workflow/ARCHITECT.md) i dalej trzymaj się tych reguł.
- **Sonnet / Haiku (`claude-sonnet-*` / `claude-haiku-*`)** → jesteś IMPLEMENTEREM. Przeczytaj [docs/workflow/IMPLEMENTER.md](docs/workflow/IMPLEMENTER.md) i dalej trzymaj się tych reguł.

Jeśli masz wątpliwość co do swojej roli — zapytaj użytkownika ZANIM wykonasz jakąkolwiek akcję modyfikującą stan repo.

Recenzent (np. Google Jules, Gemini) ma osobne instrukcje w [REVIEWER.md](REVIEWER.md). Recenzent NIE modyfikuje kodu ani dokumentów — ocenia **dwa razy**: (a) folder zmiany OpenSpec / ADR przed implementacją, (b) kod w PR przed merge.

## Warstwa 0 — Discovery (nowy projekt)

Na starcie nowego projektu architekt (Opus) przeprowadza wywiad wg [`docs/workflow/DISCOVERY.md`](docs/workflow/DISCOVERY.md)
i wypełnia `docs/PRODUCT_BRIEF.md`. Wyzwalacz: właściciel pisze **„odkryjmy projekt"**.
Brief jest wejściem do `zainicjuj kit` i pierwszych specs.

## Skills (superpowers) a ten workflow — zasada nadrzędna

Jeśli w środowisku są dostępne skille (brainstorming, writing-plans, test-driven-development, code-review itd.) — używaj ich jako **narzędzi do tego, JAK pracować w danej fazie**. Ale **artefakty i ich miejsce definiuje ten kit, nie skille**: dla design / spec / plan kanoniczny jest `openspec/changes/<slug>/` (format kitu), `PROGRESS.md` i ADR — NIE `docs/superpowers/specs/`. Szczegóły i mapa faz→skills: [docs/workflow/ARCHITECT.md](docs/workflow/ARCHITECT.md).

## O projekcie

**{{PROJECT_NAME}}** — {{PROJECT_DESCRIPTION}}.

**Stack:** {{STACK}}.

**Workflow:** {{WORKFLOW_SUMMARY}}.

## Komendy

{{COMMANDS_SECTION}}

## Konwencja commitów (Conventional Commits)

Format: `typ(zakres): opis po polsku`

**Typy:**
- `feat(scope):` — nowa funkcjonalność
- `fix(scope):` — naprawa buga
- `refactor(scope):` — zmiana kodu bez zmiany zachowania
- `docs(scope):` — tylko dokumentacja
- `perf(scope):` — optymalizacja wydajności
- `test(scope):` — dodanie/zmiana testów
- `chore(scope):` — infrastruktura, config, CI

**Zakresy (scope):** {{COMMIT_SCOPES}}

**Przykłady:**
```
feat(<scope>): <krótki opis>
fix(<scope>): <krótki opis>
docs(workflow): <slug> — propozycja zmiany
docs(workflow): <zmiana w workflow>
```

## Konwencja branchy

Format: `task/<slug>`
Bazowy branch: `main` (zmień na `master` jeśli repo używa starej nazwy)

**Przykłady:**
```
task/<slug-zmiany>
fix/hotfix-<slug>
```

## Zasady edycji kodu (wspólne dla wszystkich ról)

1. Po każdej zmianie w plikach źródłowych → `{{VALIDATION_COMMAND}}`
2. Nie przechowuj haseł/kluczy w kodzie — używaj plików z `.gitignore` lub zmiennych środowiskowych
3. Klucze API NIGDY w localStorage (jeśli aplikacja frontowa) — tylko zmienna sesyjna JS
4. Przestrzegaj reguł ogólnych: nie dodawaj fallbacków dla scenariuszy niemożliwych, nie refaktoryzuj bez polecenia, jedna zmiana = jeden zakres.
<!-- OPTIONAL:DEPLOY_START -->
5. **Deploy aplikacji:** {{DEPLOY_INFO}}
<!-- OPTIONAL:DEPLOY_END -->

## Gdzie szukać informacji

| Potrzebujesz | Plik |
|---|---|
| Zasady dla architekta (Opus) | `docs/workflow/ARCHITECT.md` |
| Zasady dla implementera (Sonnet/Haiku) | `docs/workflow/IMPLEMENTER.md` |
| Zasady dla recenzenta | `REVIEWER.md` |
| Historia projektu, stan zadań | `PROGRESS.md` |
| Stan bieżący systemu (specs) | `openspec/specs/` |
| Zmiany w toku | `openspec/changes/` (aktywne) i `openspec/changes/archive/` (ukończone) |
| Specyfikacja bieżącej zmiany | `openspec/changes/<slug>/` |
| Decyzje architektoniczne (bieżące) | `docs/architecture/ADR_INDEX.md` → konkretne `ADR_*.md` |
| Dokumentacja użytkownika | `README.md` |
| Szablony TASK (legacy, bez OpenSpec) | `docs/tasks/legacy/` |

## Kontekst użytkownika

- **Właściciel** — {{USER_CONTEXT}}
- **System:** [Twój OS, jeśli istotny dla projektu]
<!-- OPTIONAL:REPO_START -->
- **Repo:** {{REPO_URL}}
<!-- OPTIONAL:REPO_END -->
<!-- OPTIONAL:APP_START -->
- **Aplikacja:** {{APP_URL}}
<!-- OPTIONAL:APP_END -->
