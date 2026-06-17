# TASK_019: Ręczne dodawanie pozycji („z palca")

> **To jest PRZYKŁAD wypełnionego TASK** — skopiowany z rzeczywistego projektu (KA Scraper) jako referencja stylu pisania. Po stworzeniu `TASK_001` w nowym projekcie można ten plik usunąć.

## Cel

Dodać do aplikacji możliwość ręcznego dodania nowej pozycji, bez dociągania historii ze scrapera. Użycie: pozycje zakupione dawno temu, dla których nie ma sensu skanować rozmów — user chce szybko wprowadzić podstawowe dane do ewidencji.

Domyślny status nowej pozycji: `received` (odebrane) — zakłada zakończoną transakcję i sprzęt w rękach.

## Zakres zmian

**Jedyny modyfikowany plik:** `app/ka-asystent.html`

Zmian NIE robimy w: `scraper.js`, `config.js`, `gdrive-sync.js`, `analyze.js`.

## Specyfikacja

### 1. Floating button „+" na ekranie kanban

Na ekranie `screen-kanban` (`app/ka-asystent.html:383`) dodać floating action button (FAB) w prawym dolnym rogu:

- Pozycja: `position: fixed; right: 16px; bottom: 16px`
- Rozmiar: ok. 56×56 px, okrągły, tło w kolorze akcentu (`AC`), ikona „+"
- Cień: lekki drop-shadow
- `z-index` wyższy niż bottom-nav
- Klik → `showScreen('add-item')`

### 2. Formularz „Dodaj pozycję"

Nowy ekran `screen-add-item` z polami:

| Pole | Typ | Wymagane | Domyślna wartość |
|---|---|---|---|
| `title` | text | **tak** | — |
| `finalPrice` (EUR) | number step=0.01 | nie | — |
| `finalPricePLN` (PLN, **pomocnicze**) | number step=0.01 | nie | — |
| `createdAt` (data zakupu) | date | nie | dzisiaj |
| `notes` | textarea | nie | — |
| Status (dropdown) | select | nie | `received` |

**Przeliczanie EUR ↔ PLN (automatyczne):**
- Użyj istniejącego kursu: `settings.exchangeRate` (domyślnie 4.30, `app/ka-asystent.html:604`).
- Gdy user wpisze `finalPrice` (EUR) i pole PLN jest puste → wylicz PLN `= EUR * rate`.
- Zapisujemy do itemu **tylko `finalPrice` w EUR**. Pole PLN to helper UI, nie nowe pole w modelu.

**Walidacja submit:**
- `title` nie może być pusty → alert „Tytuł jest wymagany".

### 3. Funkcja tworzenia itemu

```javascript
function saveNewItem() {
  const title = document.getElementById('add-title').value.trim();
  if (!title) { alert('Tytuł jest wymagany'); return; }

  const item = {
    id: genId(),
    title,
    status: document.getElementById('add-status').value || 'received',
    finalPrice: parseFloat(document.getElementById('add-price-eur').value) || null,
    notes: document.getElementById('add-notes').value.trim() || '',
    createdAt: new Date().toISOString(),
    updatedAt: new Date().toISOString(),
    source: 'manual',
  };

  items.unshift(item);
  saveItems();
  showScreen('kanban');
  renderKanban();
}
```

**Flag `source: 'manual'`** — żeby odróżnić ręcznie dodane pozycje od scraperowych.

## Testy

1. Wyciąg `<script>` → `node --check` → brak błędów.
2. Ręczny test w przeglądarce:
   - Kliknij FAB „+" na ekranie kanban → otwiera się formularz.
   - Wpisz tylko tytuł, kliknij Zapisz → pozycja pojawia się w kolumnie „received" na kanbanie.
   - Wpisz tytuł + cenę EUR → pole PLN się wylicza w locie.
   - Wpisz tytuł + datę zakupu z zeszłego roku → `createdAt` w itemie ma tę datę.
   - Próba zapisu bez tytułu → alert, nic nie zapisane.
3. Reload strony → nowy item przetrwał w localStorage.

## Uwagi

- Aplikacja jest single-file HTML — wszystko w `app/ka-asystent.html`.
- NIE twórz nowego pola `finalPricePLN` w modelu itemu — to tylko UI helper.
- Deploy automatyczny przez `deploy-pages.yml` po merge do main.

## Rozbicie na commity (sugerowane)

1. `feat(app): ekran screen-add-item + formularz`
2. `feat(app): FAB "+" na ekranie kanban`
3. `feat(app): przeliczanie EUR↔PLN + walidacja + saveNewItem`
4. `docs: aktualizacja PROGRESS.md`

## Pliki źródłowe

- `app/ka-asystent.html` — jedyny modyfikowany plik
- `PROGRESS.md` — aktualizacja po zakończeniu TASK (obowiązkowe)
