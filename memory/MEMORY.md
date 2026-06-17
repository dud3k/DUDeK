# Memory Index

<!--
Ten plik jest indeksem auto-memory Claude Code. Każda linia to jedno-linijkowy wpis
z linkiem do pliku memory_*.md w tym samym katalogu.

Zasady:
- Każdy wpis max ~150 znaków (plik ucina po 200 linii)
- Sortuj tematycznie, nie chronologicznie
- NIE wklejaj tu treści memory — tylko link + hook
- Format: `- [Tytuł](plik.md) — jednolinkowy hook`

Jak ten plik trafia do projektu:
- Claude Code automatycznie ładuje go z katalogu: `~/.claude/projects/<slug>/memory/MEMORY.md`
- Skopiuj wpisy z poniższych sekcji (lub pozostaw puste)
-->

## Uniwersalne (polecamy skopiować dla każdego nowego projektu)

- [PowerShell command syntax](feedback_powershell.md) — Use `&` and `Get-Content |` in PowerShell, never `!` prefix or `< file` redirection
- [Git push — nie proś o ręczne komendy](feedback_git_push.md) — Wywołaj git push jako narzędzie, użytkownik zatwierdza przez prompt
- [Workflow architect/implementer](reference_workflow.md) — Opus = plan + openspec/changes/<slug>/, Sonnet = implementacja; zmiany identyfikowane slugiem, `/opsx:archive` przed PR

## Specyficzne dla projektu (dodaj po starcie)

<!-- Przykłady rzeczy które warto zapisać gdy się pojawią:
- [Cel projektu](project_context.md) — Co użytkownik osiąga tym systemem (NIE kod — cel biznesowy)
- [Deploy pipeline](reference_deployment.md) — Gdzie deploy, jakim workflow, czego NIE kopiować ręcznie
- [Preferencje testowe](feedback_tests.md) — np. "integracyjne testy muszą uderzać w prawdziwą DB, nie mocki"
- [Faza 0 / sonda](feedback_probe.md) — Dla ryzykownych integracji: mikro-sonda na 3-5 przypadkach przed pełnym specem
-->
