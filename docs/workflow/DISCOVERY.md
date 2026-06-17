# Warstwa 0 — Discovery (JTBD + Cztery Siły)

Protokół wywiadu dla ARCHITEKTA (Opus). Wykonywany **przed** `zainicjuj kit`, przed ADR, przed
pierwszą zmianą OpenSpec. Produkt wyjściowy: wypełniony `docs/PRODUCT_BRIEF.md` (z szablonu
`docs/PRODUCT_BRIEF_template.md`), zaakceptowany przez właściciela.

**Wyzwalacz:** właściciel pisze **„odkryjmy projekt"** (alias: „zacznij discovery").

---

## Pięć zasad prowadzenia wywiadu

1. **Naturalne pytania na wejściu, formuła JTBD na wyjściu.** NIE wymagaj od właściciela zdań
   „Kiedy… chcę… żeby…". Pytaj po ludzku (lista bloków poniżej), a zdania JTBD **architekt układa
   sam** z odpowiedzi. Proszenie o gotowy job statement wywołuje racjonalizację — użytkownik podaje
   rozwiązania zamiast opisać realne zdarzenia, a JTBD właśnie przed tym ostrzega.

2. **Pętla potwierdzenia.** Po przetłumaczeniu odpowiedzi na zdanie JTBD odegraj je z powrotem:
   „Czy dobrze rozumiem: kiedy [okoliczności], chcesz [postęp], żeby [efekt]?" Chroni przed cichym
   odjechaniem tłumaczenia od intencji.

3. **Wywiad „wstecz".** Gdzie się da, pytaj o konkretne zdarzenia (co się stało, jak jest dziś),
   nie o „czego potrzebujesz". Przykład: zamiast „co chciałbyś, żeby aplikacja robiła?" → „co teraz
   robisz, kiedy potrzebujesz [X]?".

4. **Bez nazywania rozwiązania w jobie.** Job opisuje postęp użytkownika, nie funkcję apki.
   Złe: „Kiedy…, chcę mieć powiadomienie push…". Dobre: „Kiedy…, chcę wiedzieć bez wysiłku…".

5. **Po jednym pytaniu naraz.** Discovery to rozmowa, nie formularz. Czekaj na odpowiedź, zanim
   zadasz kolejne pytanie.

---

## Zestaw pytań — 5 bloków (~8 pytań)

Architekt zadaje pojedynczo, w tej kolejności. W nawiasach — co z odpowiedzi wyciąga do briefu.

### Blok 1 — Dziś
- Co jest teraz uciążliwe i jak ludzie radzą sobie *bez* Twojego rozwiązania?
  *(okoliczności + obecna alternatywa = to, co zostanie „zwolnione" przez job)*

### Blok 2 — Gwiazda północna
- Dla kogo przede wszystkim to robisz? Opisz jedną realną osobę — wiek, biegłość
  z technologią, granica jej cierpliwości.
  *(persona główna; ta osoba jest „gwiazdą północną" — każda decyzja projektowa jest optymalizowana pod nią)*

### Blok 3 — Postęp
- Co ta osoba chce osiągnąć i kiedy się to zaczyna — co ją uruchamia?
  *(architekt układa job: „Kiedy [sytuacja], chce [postęp], żeby [efekt]" → następnie pętla potwierdzenia)*

### Blok 4 — Cztery Siły (cztery krótkie pytania → jeden wniosek projektowy)
- **Push** — co tę osobę najbardziej frustruje w obecnym sposobie?
  *(siła popychająca ku zmianie)*
- **Pull** — co w nowym rozwiązaniu ma ją przyciągnąć?
  *(siła przyciągająca do nowego)*
- **Nawyk** — co trzyma ją przy starym sposobie (bo „jakoś działa")?
  *(inercja; trzeba ją obniżyć)*
- **Lęk** — czego może się bać przy zmianie (że coś zepsuje, że za trudne)?
  *(tarcie; trzeba je zredukować)*

> **Wniosek projektowy (architekt formułuje):** MVP musi **podbić Push + Pull** i **zbić Nawyk + Lęk**.
> Decyzje projektowe, które nie spełniają tego kryterium, powinny być odłożone.

### Blok 5 — MVP
- Co MUSI być w pierwszej wersji? Co świadomie odkładasz?
  *(wejście do tabeli zakresu MVP w briefie)*

---

## Zakres Czterech Sił

Cztery Siły liczymy **wyłącznie dla persony głównej** (gwiazda północna). Persony drugorzędne:
najwyżej jednolinijkowa notka w briefie, jeśli ich perspektywa jest istotna dla zakresu.
Szczegółowa analiza sił dla wielu person to przerost dla projektów solo/małych.

---

## Po wywiadzie

1. Architekt wypełnia `docs/PRODUCT_BRIEF.md` (kopia szablonu z `docs/PRODUCT_BRIEF_template.md`).
2. Prezentuje wypełniony brief właścicielowi do akceptacji — sekcja po sekcji lub całość.
3. Właściciel akceptuje (lub wnosi poprawki) → brief zatwierdzony.
4. Dopiero wtedy: `zainicjuj kit` → ADR stacku → `/opsx:propose` (pierwsze specs z jobów).

Joby z briefu są naturalnym wejściem do pierwszych `openspec/specs/` — zamykają pętlę
„od Jobs-To-Be-Done do job done".
