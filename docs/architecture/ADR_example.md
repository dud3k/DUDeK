# ADR 004: GitHub Gist jako transport synchronizacji

> **To jest PRZYKŁAD wypełnionego ADR** — skopiowany z projektu KA Scraper jako referencja stylu. Po stworzeniu pierwszego własnego ADR można ten plik usunąć.

## Status

Zaakceptowano (kwiecień 2026, rekonstrukcja)

## Obszar

Sync / transport

## Kontekst

Aplikacja potrzebuje synchronizacji danych między urządzeniami (telefon, PC). Rozważane opcje: Firebase Firestore, Supabase, PouchDB+CouchDB, Cloudflare Workers KV, GitHub Gist. Priorytet: zero kosztów, zero infrastruktury serwerowej.

- **Firebase / Supabase** — pełnowartościowe BaaS, ale dodają konto usługi do utrzymania i kwestie fakturowania w razie przekroczenia free tier.
- **PouchDB + CouchDB** — wymaga serwera CouchDB (własnego lub managed).
- **Cloudflare Workers KV** — najniższy narzut, ale wymaga CF account + deploymentu workera.
- **GitHub Gist** — użytkownik już ma konto GitHub (repo aplikacji), PAT z uprawnieniem `gist` wystarcza, zero infrastruktury.

## Decyzja

Używamy **GitHub Gist** jako key-value file storage. Pliki w Gist:
- `ka-data.json` — pełna tablica itemów + metadata
- `ka-patch.json` — patch od Gemini (importowany i usuwany)
- `ka-status.json` — status workflow GitHub Actions

Auto-poll co 60s, debounce zapisu 3s, force-push przez długi klik na ☁️.

## Konsekwencje

**Dobre:**
- Zero kosztów, zero infrastruktury
- Użytkownik ma już konto GitHub (infra projektu)
- Pliki są wersjonowane (historia Gist)

**Złe / ograniczenia:**
- Wymaga `GIST_TOKEN` (GitHub PAT z uprawnieniem `gist`)
- Limit: 100MB per Gist (wystarczający dla ~500+ itemów, ale przy skali zdjęć w base64 rośnie szybko)
- Brak atomowych operacji — merge per-item trzeba zrobić po stronie klienta
- Znany bug: merge na poziomie całej tablicy (last-write-wins) przy oryginalnej implementacji — wymaga osobnego TASK

**Wymaga monitorowania:**
- Jeśli rozmiar Gist przekroczy 50MB → rozważyć split na wiele Gistów lub migrację do Firebase Firestore (wtedy nowy ADR).
- Jeśli rate limity GitHub okażą się problemem przy auto-poll co 60s × wiele urządzeń → zwiększyć interwał lub użyć webhooków.
