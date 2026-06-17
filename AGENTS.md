# AGENTS.md

Ten plik jest uniwersalnym punktem wejścia dla agentów AI działających na tym repozytorium. Rozpoznaj swoją rolę na podstawie tego, jakim agentem jesteś:

## Recenzent (np. Google Jules, Gemini w trybie review) → RECENZENT

Jesteś **recenzentem**. Twoje pełne instrukcje znajdują się w [REVIEWER.md](REVIEWER.md). Stosuj je w całości.

**W skrócie (ale i tak przeczytaj REVIEWER.md):**
- Oceniasz **zmiany OpenSpec / ADR** (TYP A) oraz **kod w PR** (TYP B).
- NIE modyfikujesz plików, NIE commitujesz, NIE mergeujesz PR, NIE approve'ujesz przez `gh pr review`.
- Zwracasz recenzję w ustrukturyzowanym formacie — właściciel sam decyduje co zrobić.

## Claude Code → ARCHITEKT / IMPLEMENTER

Przeczytaj [CLAUDE.md](CLAUDE.md) § „Krok 0" i rozpoznaj rolę na podstawie identyfikatora modelu:

- **Opus** (`claude-opus-*`) → ARCHITEKT, reguły w [docs/workflow/ARCHITECT.md](docs/workflow/ARCHITECT.md).
- **Sonnet / Haiku** (`claude-sonnet-*`, `claude-haiku-*`) → IMPLEMENTER, reguły w [docs/workflow/IMPLEMENTER.md](docs/workflow/IMPLEMENTER.md).

## Inny agent (nie wymieniony wyżej)

1. Przeczytaj [CLAUDE.md](CLAUDE.md) — opis projektu i konwencje.
2. Przeczytaj [REVIEWER.md](REVIEWER.md) — reguły dla trybu tylko-do-odczytu.
3. **Zapytaj właściciela**, którą rolę pełnisz (architekt / implementer / recenzent), zanim wykonasz jakąkolwiek akcję modyfikującą stan repo.

## Workflow OpenSpec — szybkie przypomnienie

```
Opus (architekt)  → /opsx:propose → openspec/changes/<slug>/ → commit na main
Recenzent [TYP A] → openspec show <slug> → recenzja ręczna → docs/reviews/
Sonnet (impl.)    → git pull → branch task/<slug> → implementacja wg tasks.md
Sonnet (finisz)   → /opsx:archive + wpis PROGRESS.md → push → PR
Recenzent [TYP B] → ręczna recenzja diffu PR (kod ORAZ zaktualizowane openspec/specs/)
Właściciel        → merge PR do main (kod i specyfikacja trafiają na main spójnie)
```

## Warstwa 0 — Discovery (nowy projekt)

Na starcie nowego projektu architekt przeprowadza wywiad wg [`docs/workflow/DISCOVERY.md`](docs/workflow/DISCOVERY.md)
i wypełnia `docs/PRODUCT_BRIEF.md`. Wyzwalacz: właściciel pisze **„odkryjmy projekt"**.
Discovery jest jednorazowe i poprzedza `zainicjuj kit`.

## Zasady wspólne dla wszystkich agentów

- Tajemnice / klucze API / tokeny — NIGDY nie commituj, NIGDY nie loguj w plaintexcie.
- Nie modyfikuj `.github/workflows/` bez wyraźnej zgody właściciela.
- Nie używaj `--no-verify`, `--force`, `--amend` na cudzych commitach bez zgody.
- Konwencja commitów: Conventional Commits po polsku (szczegóły w [CLAUDE.md](CLAUDE.md)).
- Branch bazowy: `main`.
