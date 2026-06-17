# Rozwój DUDeK (maintainer)

> Ten plik jest dla osób, które **rozwijają sam framework DUDeK** — nie dla tych, którzy go *używają*
> w swoim projekcie. Jeśli budujesz aplikację z DUDeK, ten plik Cię nie dotyczy (patrz [SETUP.md](../SETUP.md)).

## Topologia repozytoriów

- **`dud3k/DUDeK`** (to repo) — *ciało*: szablon, który klonują użytkownicy. Tu lądują **implementacje**
  zmian, przez branch + PR + recenzję + merge.
- **`dud3k/dudek-dev`** — *mózg*: planowanie rozwoju DUDeK (koncepcje, instrukcje, recenzje, discovery
  dla większych zmian). Tam projektujesz; tutaj implementujesz.

**Reguła (anty-bałagan):** NIE edytuj plików szablonu w `dudek-dev` i nie synchronizuj ich ręcznie tutaj
— to prowadzi do dwóch rozjechanych kopii. `dudek-dev` planuje, `DUDeK` dostaje PR.

## Co dogfooduje rozwój DUDeK, a co nie

DUDeK to **dokumentacja**, nie software z runtime'em. Dlatego:

- ✅ **Stosuj w pełni:** podział ról (architekt / implementer / recenzent), discovery-style projektowanie
  większych zmian, PR + podwójna recenzja (TYP A planu, TYP B diffu), Conventional Commits, branch `task/<slug>`.
- ⛔ **Nie wciskaj na siłę:** OpenSpec *behavioral specs* i TDD — markdown nie ma „zachowania" do
  specyfikowania. Rozwój DUDeK to **zmiany dokumentacji przez PR**, nie `/opsx:*` ani testy jednostkowe.

## Cykl zmiany w DUDeK

```
[w dudek-dev] projekt zmiany: koncepcja / instrukcja → akceptacja właściciela
        ↓
[w DUDeK] branch task/<slug> → edycje plików szablonu → push → PR
        ↓
recenzja (TYP B, ręczna) → właściciel mergeuje do master
```

## Uwagi

- `assets/dudek-slide.svg` — grafika brandu; zapis „DUDEK" w niej zostaje świadomie (nie zmieniaj na DUDeK).
- Placeholdery `{{...}}` w plikach szablonu są celowe (mechanizm „zainicjuj kit" u konsumenta) —
  nie wypełniaj ich w tym repo.
- Po renamie repo (`claude-workflow-kit` → `DUDeK`) referencje wskazują `dud3k/DUDeK`; stary URL przekierowuje.
