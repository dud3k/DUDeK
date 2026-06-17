# DUDeK — Disciplined Universal DEvelopment Kit

> Inżynieryjne „szelki" na agenta AI — od Jobs-To-Be-Done do działającego kodu, bez halucynacji
> i scope creepu. Uniwersalny, stack-agnostyczny workflow dla Claude Code.

Uniwersalny, stack-agnostyczny starter workflow **architekt / implementer / recenzent** dla
Claude Code. Zacznij od discovery („odkryjmy projekt" → PRODUCT_BRIEF), potem wypełnij jeden plik
i powiedz „zainicjuj kit" — masz sprawdzoną dyscyplinę spec-driven development z OpenSpec, ADR,
PROGRESS i memory w dowolnym projekcie (Node, Python, Go, cokolwiek).

**DUDeK** — framework łączący discovery (JTBD + Cztery Siły) z dyscypliną OpenSpec, od
Jobs-To-Be-Done do job done.

Zawiera tylko **lekki rdzeń dokumentacyjny** — bez ciężkiej automatyzacji (orchestratora).

---

## Dlaczego DUDeK (wartość)

Praca z agentami AI ma trzy powracające bolączki: **halucynacje**, **samowolne rozszerzanie zakresu**
(scope creep) i **gubienie kontekstu architektonicznego** w czasie. DUDeK zamyka je systemowo —
nakłada na AI inżynieryjne szelki:

- **Sztywny podział ról.** Architekt (Opus) projektuje, Implementer (Sonnet/Haiku) koduje, Recenzent
  ocenia — nigdy w jednej sesji. Twarde blokady implementera („nie zaczynaj bez specu", „nie wychodź
  poza zakres", „nie refaktoryzuj bez polecenia") kończą z agentem, który „naprawia jedno, psując pięć".
- **Faza 0 — mikro-sondy przed specem.** Założenia (kształt API, struktura DOM, format pliku)
  sprawdzasz empirycznie na 3–5 realnych przypadkach, ZANIM powstanie duży spec. Koniec z planami
  budowanymi na domysłach.
- **Discovery na wejściu (JTBD + Cztery Siły).** Zanim powstanie kod, ustalasz realny problem głównej
  persony (Gwiazda Północna). Budujesz produkt rozwiązujący ból — nie „kod, bo tak ktoś wymyślił".
- **ADR — pamięć decyzji.** Decyzje architektoniczne w plikach `.md` z jawnym statusem, niemutowalne.
  LLM nie debatuje w kółko tych samych wyborów ani nie wraca do odrzuconych opcji.
- **Spec jako źródło prawdy (OpenSpec).** Żywa specyfikacja zachowania + zmiany jako delty; podwójna
  bramka recenzji — plan przed implementacją (TYP A), kod przed merge (TYP B).
- **Narzędzia vs artefakty.** Skille (superpowers) dyktują JAK pracujesz w danej fazie; DUDeK dyktuje
  CO powstaje i GDZIE ląduje. Metoda nie miesza się z dokumentacją projektu.

---

## Jak zacząć

👉 **[SETUP.md](SETUP.md)** — instrukcja od zera: utwórz repo z szablonu → discovery → wypełnij
`PROJECT.md` → „zainicjuj kit" → `openspec init`. Krok po kroku, decyzyjnie domknięta.

**Wymagania wstępne:** Node.js, GitHub CLI (`gh`), Claude Code + zalecany plugin **superpowers**
— szczegóły w [SETUP.md](SETUP.md). Kit działa też bez superpowers (graceful degradation).

W skrócie:
1. Utwórz repo z szablonu: `gh repo create nazwa --template dud3k/DUDeK --private --clone`
2. Powiedz **„odkryjmy projekt"** → wywiad JTBD → `docs/PRODUCT_BRIEF.md` (Warstwa 0).
3. Wypełnij **[PROJECT.md](PROJECT.md)** (jedno źródło prawdy, ~7 pól).
4. W Claude Code: „zainicjuj kit" → podmiana placeholderów, propozycja pierwszej zmiany OpenSpec.
5. `openspec init --tools claude` → warstwa zmian gotowa.

---

## Co jest w środku

| Plik / Folder | Rola |
|---|---|
| `PROJECT.md` | **Jedno źródło prawdy** — wypełniasz raz, Claude rozwija placeholdery |
| `SETUP.md` | Instrukcja zakładania projektu z szablonu + kroki openspec init |
| `CLAUDE.md` | Punkt wejścia Claude Code — routing ról (Opus/Sonnet/Haiku) + komendy + konwencje |
| `AGENTS.md` | Uniwersalne wejście dla dowolnego agenta AI — rozpoznanie roli |
| `REVIEWER.md` | Reguły recenzenta — TYP A (folder zmiany OpenSpec / ADR) + TYP B (kod w PR) |
| `PROGRESS.md` | Log wykonanych zadań, aktualizowany po każdej zmianie |
| `docs/workflow/DISCOVERY.md` | Protokół wywiadu JTBD — Warstwa 0, prowadzony przez Opus przed `zainicjuj kit` |
| `docs/PRODUCT_BRIEF_template.md` | Szablon briefu produktowego (persony, joby, Cztery Siły, zakres MVP) |
| `docs/workflow/ARCHITECT.md` | Reguły dla Opus — prowadzenie zmian OpenSpec, Faza 0, ADR, mapa skills |
| `docs/workflow/IMPLEMENTER.md` | Reguły dla Sonnet/Haiku — git, branch, testy, PR, /opsx:archive |
| `docs/tasks/legacy/` | Szablony TASK_NNN (legacy fallback — gdy projekt świadomie rezygnuje z OpenSpec) |
| `docs/architecture/ADR_template.md` + `_example.md` | Szablon i przykład ADR |
| `docs/architecture/ADR_INDEX.md` | Indeks bieżących decyzji wg obszaru |
| `docs/reviews/` | Recenzje (`review_*.md`, zapisywane przez recenzenta) + sondy Faza 0 (`probe_*.md`) |
| `memory/` | 3 uniwersalne wpisy auto-memory (do skopiowania do `~/.claude/projects/<slug>/memory/`) |
| `openspec/` | **Tworzone przez `openspec init` w projekcie** — nie w kicie; `specs/` + `changes/` |

---

## Zasady, których kit uczy

0. **Warstwa 0 — discovery na wejściu nowego projektu.** Przed ADR i specs: wywiad JTBD
   (`docs/workflow/DISCOVERY.md`) → `docs/PRODUCT_BRIEF.md`. Joby z briefu są wejściem do
   pierwszych specs. Wyzwalacz: **„odkryjmy projekt"**.
1. **Trzy role, jedna sesja na rolę.** Opus planuje, Sonnet koduje, recenzent ocenia. Nigdy nie łącz ról.
2. **Recenzent ocenia dwa razy:** (A) folder zmiany OpenSpec / ADR przed implementacją, (B) kod w PR przed merge.
3. **Jedna zmiana = jeden branch = jeden PR.** Nie rozrastaj zakresu poza `proposal.md`.
4. **Folder zmiany commitowany na `main` ZANIM implementer zacznie.** Inaczej `git pull` nie pokaże specyfikacji.
5. **Sonnet NIE mergeuje własnego PR.** Po utworzeniu PR czeka na recenzję i decyzję właściciela.
6. **PROGRESS.md + /opsx:archive są obowiązkową częścią ukończenia zmiany.** Najnowsze wpisy na górze; delty scalane do `openspec/specs/`.
7. **Test po każdej zmianie** (walidacja składni + testy + smoke test).
8. **Zero przedwczesnych abstrakcji.** Bez fallbacków dla scenariuszy niemożliwych.
9. **Nie wykraczaj poza scope zmiany.** Widzisz buga? Zgłoś — nie naprawiaj samodzielnie.
10. **Faza 0 dla niepewności.** Decyzja oparta na niezweryfikowanym zewnętrznym zachowaniu → najpierw sonda na 3–5 przypadkach, potem spec.

## Skills (superpowers) a kit

Skille definiują **JAK** pracować w danej fazie (brainstorming, writing-plans, TDD, code-review);
kit definiuje **CO** powstaje i **GDZIE** ląduje. Przy konflikcie ścieżki artefaktu wygrywa format
kitu (`openspec/changes/<slug>/`, `PROGRESS.md`, ADR) — nie `docs/superpowers/specs/`. Szczegóły w `ARCHITECT.md`.

## Cykl projektu

```
[Warstwa 0 — jednorazowo na starcie]
„odkryjmy projekt" → wywiad JTBD (DISCOVERY.md) → PRODUCT_BRIEF.md → akceptacja właściciela
        ↓
[Cykl zadań — powtarzany dla każdej zmiany]
Opus (architekt)  → /opsx:propose → openspec/changes/<slug>/ → commit na main
Recenzent [TYP A] → ręcznie: pakiet z `openspec show <slug>` → recenzja → docs/reviews/
Sonnet (impl.)    → git pull → branch task/<slug> → implementacja wg tasks.md
Sonnet (finisz)   → /opsx:archive (delty → openspec/specs/) + wpis PROGRESS.md → push → PR
Recenzent [TYP B] → ręcznie: recenzja diffu PR (kod ORAZ zaktualizowane openspec/specs/)
Właściciel        → merge PR do main (kod i specyfikacja trafiają na main spójnie)
```

---

## Czego kit świadomie NIE zawiera

- **Orchestrator** (automatyczny Gemini review + dispatch Sonneta + monitor UI). Jeśli projekt
  jest na Node + GitHub i chcesz automatyzacji — podpinasz osobno.
  Kit celowo zostaje lekki i niezależny od stacku.
- **Pliki tool-specyficzne** (`JULES.md`, `GEMINI.md`). Recenzję czyta dowolny agent z `REVIEWER.md`.
  Jeśli konkretne narzędzie wymaga własnego pliku-wskaźnika — dodaj 1-liniowy pointer do `REVIEWER.md`.
- **Automatyzacja recenzji** (odłożona decyzją właściciela 2026-06-12: Jules działa za wolno; wracamy,
  gdy ręczny proces zacznie boleć). Recenzja ręczna jest pełnoprawnym trybem standardowym kitu.

## Tryb pracy

Kit zakłada **team**: GitHub + branch + PR + recenzja + merge. Praca czysto lokalna bez remote to
wyjątek — zlecasz ad hoc, gdy zajdzie potrzeba. Standard pozostaje jednoznaczny.
