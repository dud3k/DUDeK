# SETUP — nowy projekt od zera

Zakładanie nowego projektu na bazie tego szablonu. Wykonaj kroki po kolei.

---

## Wymagania wstępne

Zanim zaczniesz, miej zainstalowane:

| Narzędzie | Po co | Wymagane? |
|---|---|---|
| **Claude Code** | środowisko pracy z agentem | ✅ wymagane |
| **GitHub CLI (`gh`)** | tworzenie repo z szablonu, PR-y | ✅ wymagane (ścieżka rekomendowana) |
| **Node.js (z npm)** | OpenSpec CLI (`npx @fission-ai/openspec`) | ✅ wymagane do warstwy zmian |
| **superpowers** (plugin Claude Code) | skille metody: brainstorming, writing-plans, test-driven-development, code-review | 🟡 mocno zalecane |

**Instalacja superpowers:** w Claude Code uruchom `/plugin`, dodaj marketplace `claude-plugins-official`
i zainstaluj `superpowers`. Kit wykorzystuje te skille jako *metodę* (JAK pracować w danej fazie) —
np. `brainstorming` w discovery, `test-driven-development` przy implementacji.

> **Graceful degradation:** kit jest zaprojektowany tak, że **działa też bez superpowers** — reguły ról,
> OpenSpec, ADR i recenzje są samowystarczalne. Bez skilli tracisz wspomaganie metodą, nie sam workflow.

---

## TL;DR — utworzenie projektu z szablonu

Repozytorium jest opublikowane jako **GitHub template**. Jedno polecenie tworzy nowe repo z czystą
historią (bez commitów szablonu) i klonuje je lokalnie:

```bash
gh repo create <nazwa-projektu> --template dud3k/DUDeK --private --clone
cd <nazwa-projektu>
```

> `gh` nieautoryzowane? `gh auth login`.

Repo `github.com/<user>/<nazwa-projektu>` jest utworzone, sklonowane, `origin` ustawiony — gotowe.

### Alternatywa offline (bez dostępu do szablonu)

Pobierz/rozpakuj zawartość szablonu do nowego katalogu projektu, wejdź do niego i:

```bash
git init
git add .
git commit -m "chore: init workflow kit"
gh repo create <nazwa-projektu> --private --source=. --remote=origin --push
```

---

## Pierwsze uruchomienie

### Krok 0 — Discovery (jednorazowe, na starcie projektu)

Zanim wypełnisz PROJECT.md i zainicjujesz kit, powiedz architektowi (Opus):

```
Odkryjmy projekt
```

Architekt przeprowadzi wywiad (protokół: `docs/workflow/DISCOVERY.md`), ułoży joby JTBD i wypełni
`docs/PRODUCT_BRIEF.md`. Brief zaakceptowany przez Ciebie jest wejściem do następnych kroków.

> Discovery to krok jednorazowy — nie powtarzasz go przy każdym zadaniu, tylko na początku projektu.

---

### Krok 1 — Inicjalizacja kitu

1. Otwórz [PROJECT.md](PROJECT.md) i wypełnij tabelę wartości obowiązkowych (~7 pól).
   Opcjonalne zostaw puste, jeśli nie dotyczą.
2. Otwórz Claude Code w tym workspace i napisz dokładnie:

   ```
   Zainicjuj kit: przeczytaj PROJECT.md i podmień wszystkie {{PLACEHOLDER}} w plikach
   kitu wartościami z tabeli. Używaj wyłącznie literalnego znajdź-zastąp na ciągach
   {{...}} (nie przepisuj plików od nowa). Sekcje opcjonalne <!-- OPTIONAL:X --> usuń
   w całości, jeśli dana wartość w PROJECT.md jest pusta. Na koniec wypisz, które pliki
   zmieniłeś i czy zostały jakieś nierozwinięte {{...}}.
   ```

3. Claude (Opus = architekt) podmieni placeholdery i zaproponuje pierwszą zmianę OpenSpec
   (zwykle setup struktury kodu).
4. Skopiuj folder `memory/` z kitu do pamięci Claude Code na tym komputerze:
   `~/.claude/projects/<slug-projektu>/memory/` (slug wynika z pełnej ścieżki workspace — Claude Code go zna).
5. Pierwszy commit po init: `docs(workflow): inicjalizacja kitu` (Claude zrobi to jako narzędzie, Ty zatwierdzasz).

---

## Krok OpenSpec — inicjalizacja warstwy zmian

Po inicjalizacji kitu wykonaj jednorazowo w katalogu projektu:

```bash
# Zalecane: instalacja globalna
npm install -g @fission-ai/openspec@latest
openspec init --tools claude

# Alternatywa: npx (bez instalacji globalnej)
npx @fission-ai/openspec@latest init --tools claude
```

> **⚠️ Instalacja globalna jest zalecana**, bo skille `/opsx:*` i dokumentacja workflow
> (`openspec show <slug>`, `openspec list --json`) wołają gołe polecenie `openspec` — bez
> instalacji globalnej te wywołania kończą się `command not found`, a agent traci czas na
> szukanie binarki. Jeśli wybierasz npx, każde wywołanie CLI musi mieć prefiks
> `npx @fission-ai/openspec@latest`.

**Co robi `openspec init --tools claude`:**
- Tworzy `openspec/specs/` — stan bieżący systemu (source of truth, początkowo pusty)
- Tworzy `openspec/changes/` — folder aktywnych zmian i archiwum
- Instaluje komendy `/opsx:*` do Claude Code (`.claude/skills/`)
- ⓘ W trybie nieinteraktywnym (`--tools`) POMIJA `openspec/config.yaml` („Config: skipped") —
  to opcjonalna konfiguracja, można ją uzupełnić później; nie blokuje pracy

**Flaga `--tools claude`** uruchamia init nieinteraktywnie dla Claude Code. Jeśli chcesz też Cursor:
`--tools claude,cursor`.

> **⚠️ WYMAGA ZAINSTALOWANEGO Node.js (z npm).** Bez Node polecenia `npm`/`npx` nie istnieją
> (`npm: command not found`) — dotyczy to też deweloperów Pythona/Go, u których npm nie jest
> oczywistością. OpenSpec używa Node wyłącznie jako narzędzia deweloperskiego CLI — nie zmienia to
> stack-agnostyczności projektu (projekt może być w Pythonie, Go, czy czymkolwiek innym).

Po `openspec init` masz dostęp do komend `/opsx:propose`, `/opsx:apply`, `/opsx:archive` i innych
w sesji Claude Code.

---

## Cykl projektu (przypomnienie)

```
[Warstwa 0 — jednorazowo na starcie]
„odkryjmy projekt" → wywiad JTBD (DISCOVERY.md) → PRODUCT_BRIEF.md → akceptacja
        ↓
[Cykl zadań — powtarzany]
Opus (architekt)  → /opsx:propose → openspec/changes/<slug>/ → commit na main
Recenzent [TYP A] → ręcznie: openspec show <slug> → recenzja planu/ADR
Sonnet (impl.)    → git pull → branch task/<slug> → implementacja wg tasks.md
Sonnet (finisz)   → /opsx:archive + wpis PROGRESS.md → push → PR
Recenzent [TYP B] → ręczna recenzja kodu PR (kod ORAZ zaktualizowane openspec/specs/)
Właściciel        → merge PR do main (kod i specyfikacja trafiają na main spójnie)
```

Szczegóły ról: `docs/workflow/ARCHITECT.md`, `docs/workflow/IMPLEMENTER.md`, `REVIEWER.md`.
