---
name: Git push — nie proś o ręczne komendy
description: Użytkownik chce sam zatwierdzać push przez prompt narzędzia, nie wpisywać komend ręcznie
type: feedback
---

Nie proś użytkownika o ręczne wpisywanie `git push` ani innych komend git w terminalu. Zamiast tego sam wywołaj Bash z git push — użytkownik zatwierdzi lub odrzuci przez standardowy prompt narzędzia.

**Why:** Użytkownik woli klikać „akceptuj" przy tool use niż kopiować komendy do terminala.

**How to apply:** Przy każdym push/commit do GitHub — od razu wywołaj `git add`, `git commit`, `git push` jako narzędzia i poczekaj na akceptację.
