# [Nazwa projektu] — Brief produktowy

> Dokument discovery. Utrwala **persony**, **joby (JTBD)** i **zakres MVP** wypracowane w wywiadzie
> prowadzonym przez architekta (protokół: `docs/workflow/DISCOVERY.md`). Jest wejściem do
> `PROJECT.md`, ADR-ów i pierwszych `openspec/specs/`.
> Data: [RRRR-MM-DD].

---

## 1. Problem i kontekst

<!-- jak wypełnić: opisz sytuację BEZ rozwiązania. Co dziś boli? Jak ludzie radzą sobie bez Twojego
     produktu (obecna alternatywa — zeszyt, Excel, telefon, nic)? Czym to skutkuje? Jaka jest
     skala (ilu użytkowników, jak często)? -->

**[Krótki opis projektu]** — [1–2 zdania czym jest projekt i dla kogo].

**Mechanika domenowa** *(jeśli istotna)*: [opcjonalnie — jak działa dziedzina, o ile to nieoczywiste;
pomiń, jeśli projekt nie ma specyficznej domeny].

**Obecny stan (problem):** [jak użytkownicy radzą sobie bez rozwiązania; co jest uciążliwe].

---

## 2. Persony

<!-- jak wypełnić: persona główna pierwsza, oznaczona jako gwiazda północna. Każda decyzja
     projektowa jest optymalizowana pod personę główną — jeśli coś jest dla niej za trudne,
     jest za trudne. Persony drugorzędne krótko — 1–3 zdania. Poza MVP na końcu. -->

### [Imię, wiek] — [rola] *(persona główna — gwiazda północna)*
- [Jeden do trzech bulletów: biegłość z technologią, granica cierpliwości, realny ból dziś.]
- **Każda decyzja projektowa jest optymalizowana pod tę personę.**

### [Imię, wiek] — [rola] *(persona drugorzędna)*
- [1–3 zdania: kontekst, motywacja, jak różni się od persony głównej.]

### [Rola] *(poza MVP)*
- [Jednolinijkowa notka dlaczego poza MVP.]

---

## 3. Joby (Jobs To Be Done)

<!-- jak wypełnić: zdania w formule „Kiedy [okoliczności], chcę [postęp], żeby [efekt]".
     Zdania UKŁADA ARCHITEKT z odpowiedzi wywiadu — nie wymagaj ich od właściciela.
     Grupuj per persona. Bez nazywania rozwiązania w jobie (job = postęp, nie funkcja apki). -->

**[Persona główna]:**
- Kiedy **[konkretna sytuacja/wyzwalacz]**, chcę [postęp — co osiągnąć], żeby [efekt — dlaczego to ważne].
- Kiedy **[sytuacja 2]**, chcę [postęp 2], żeby [efekt 2].

**[Persona drugorzędna]:**
- Kiedy **[sytuacja]**, chcę [postęp], żeby [efekt].

---

## 4. Analiza Czterech Sił *(persona główna)*

<!-- jak wypełnić: cztery siły dla persony głównej (gwiazda północna).
     Persony drugorzędne — pomiń lub zostaw jednolinijkową notkę.
     Wniosek projektowy formułuje architekt na podstawie sił. -->

| Siła | Opis |
|---|---|
| **Push** (frustracja obecnym sposobem) | [co boli, co popycha ku zmianie] |
| **Pull** (atrakcja nowego) | [co w nowym rozwiązaniu przyciąga] |
| **Nawyk** (inercja starego) | [co trzyma przy obecnym sposobie — „jakoś działa"] |
| **Lęk** (tarcie przy zmianie) | [czego się boi przy przejściu — „coś zepsuje", „za trudne"] |

**Wniosek projektowy:** MVP musi **podbić Push + Pull** (usunąć ból, pokazać przyciąganie)
i **zbić Nawyk + Lęk** (obniżyć inercję i tarcie). Decyzje projektowe niespełniające tego
kryterium odkładamy poza MVP.

---

## 5. Zakres MVP

<!-- jak wypełnić: tabela — co MUSI być w pierwszej wersji (✅), a co świadomie odkładasz (⏳).
     Kolumna „Dla kogo" — persona lub „system". Bądź restrykcyjny: im mniej w MVP, tym szybciej
     dostarczysz wartość personie głównej i weryfikujesz joby. -->

| Funkcja | Dla kogo | MVP? |
|---|---|---|
| [funkcja 1 — krytyczna dla joba persony głównej] | [persona główna] | ✅ |
| [funkcja 2] | [persona] | ✅ |
| [funkcja 3 — ważna, ale nie blokująca] | [persona drugorzędna] | ⏳ poza MVP |
| [funkcja 4 — future] | [rola] | ⏳ poza MVP |

---

## 6. Kluczowe decyzje produktowe

<!-- jak wypełnić: numerowana lista — co zdecydowałeś i DLACZEGO. Decyzje, które nie są oczywiste
     lub mogłyby być inaczej. To jest „pamięć projektowa" — chroni przed ponownym debatowaniem
     tych samych wyborów. -->

1. **[Decyzja 1]** — [uzasadnienie; co byłoby alternatywą i dlaczego jej nie wybrałeś].
2. **[Decyzja 2]** — [uzasadnienie].

---

## 7. Ryzyka i otwarte kwestie

<!-- jak wypełnić: co może pójść nie tak lub czego jeszcze nie wiesz. Podaj świadome kompromisy
     (np. odkładasz RODO na później — to ryzyko do zarejestrowania, nie do pominięcia).
     Otwarte kwestie to pytania, na które odpowiedź przyjdzie w trakcie budowania. -->

- **[Ryzyko 1]** — [opis; dlaczego jest to ryzyko; jak planujesz je zaadresować lub kiedy].
- **[Otwarta kwestia]** — [pytanie, które rozstrzygniemy przy [TASK / ADR / warunkach]].

---

## Powiązane dokumenty

<!-- jak wypełnić: linki do ADR-ów, prototypu, recenzji — po ich powstaniu. Poniżej placeholder. -->

- Decyzja o stacku: `docs/architecture/ADR_NNN_*.md` *(do wypełnienia po discovery)*
- Prototyp UX: *(do dodania jeśli powstanie)*
- Konfiguracja projektu: [`PROJECT.md`](../PROJECT.md)
