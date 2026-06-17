# PROGRESS — Historia i stan projektu {{PROJECT_NAME}}

Nowe wpisy dodawaj NA GÓRZE (najnowsze pierwsze).
Ten plik jest aktualizowany po każdej ukończonej zmianie OpenSpec. Służy jako pamięć projektu między sesjami LLM.

---

## {{YYYY-MM-DD}} — <slug>: [Tytuł zmiany]

- [Krótki bullet — co dokładnie zmieniono w pliku/module X]
- [Kolejny bullet — konkretny artefakt: funkcja, endpoint, kolumna DB, nowy przycisk UI]
- [Jeśli był fix: „Naprawiono: opis buga → przyczyna → fix"]
- [Testy: `N testów, wszystkie przechodzą` lub `brak testów — smoke test OK`]
- `/opsx:archive` wykonany — delty scalone do `openspec/specs/`
- Branch: `task/<slug>`

## {{YYYY-MM-DD}} — pierwsza-zmiana: [Pierwszy setup — zwykle struktura kodu]

- Utworzono: strukturę katalogów projektu
- Utworzono: {{PROJECT_NAME}}
- Dodano: początkową konfigurację ({{STACK}})
- `/opsx:archive` wykonany
- Branch: `task/pierwsza-zmiana`

## {{YYYY-MM-DD}} — kit-init: Infrastruktura workflow architect/implementer

- Utworzono: `CLAUDE.md`, `docs/workflow/ARCHITECT.md`, `docs/workflow/IMPLEMENTER.md`, `REVIEWER.md`
- Utworzono: szablony legacy w `docs/tasks/legacy/`, `docs/architecture/ADR_template.md`, `ADR_INDEX.md`
- Utworzono: `PROGRESS.md` (ten plik)
- Wykonano: `openspec init --tools claude` — warstwa zmian gotowa
- Konwencja: Conventional Commits (`feat(scope):`) od tego momentu
- Branch: `task/kit-init`

---

## Obecny stan projektu

[Jedno-dwa zdania opisu gdzie jest projekt w cyklu życia.]

**Znane problemy (do rozwiązania):**
- [Bug lub ograniczenie — link do zmiany OpenSpec jeśli jest zaplanowana]

---

## Zaplanowane zmiany (backlog)

Zmiany czekające na konwersję do `openspec/changes/<slug>/` (architekt przy każdej iteracji sprawdza co następne).

| Slug | Zmiana | Priorytet | Status |
|---|---|---|---|
| `<slug>` | [Opis] | Wysoki / Średni / Niski | Zaplanowane |

---

## Jak czytać ten plik

- **Najnowsze na górze.** Każda zmiana = jedna sekcja z datą (ISO: YYYY-MM-DD) i slugiem.
- **Bullety** — konkretne zmiany: plik, funkcja, komponenty UI. Unikaj ogólników typu „poprawki".
- **Fix-y poza zmianą** (hotfixy, małe poprawki) też trafiają tutaj — bez sluga, z prefiksem typu commita (`fix(scope):`).
- **Obecny stan projektu** — aktualizuj co kilka zmian, kiedy zmienia się „big picture".
- **Backlog** — przenoś pozycje do sekcji historycznych gdy zostają skonwertowane do folderu zmiany OpenSpec i ukończone.
