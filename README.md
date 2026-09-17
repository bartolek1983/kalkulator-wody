# Kalkulator kosztów wody

Narzędzie porównujące realny koszt wody w firmie w trzech wariantach: woda butelkowana 1,5 L, galony 18,9 L i dystrybutor podłączony do sieci wodociągowej. Dla gastronomii i hoteli pokazuje dodatkowo, ile karafek trzeba sprzedać, żeby urządzenie pokryło swój abonament.

**Działa pod adresem:** https://bartolek1983.github.io/kalkulator-wody/

Jedna strona, bez serwera i bez bazy danych. Wszystko liczy się w przeglądarce, żadne dane nie są nigdzie wysyłane ani zapisywane.

---

## Jak zaktualizować stronę

1. Skasuj stary `index.html` z folderu Pobrane
2. Pobierz nową wersję pliku
3. W tym repozytorium: **Add file → Upload files**
4. Przeciągnij `index.html` i kliknij **Commit changes**
5. Po minucie strona sama się przebuduje, adres zostaje ten sam

**Uwaga, pułapka.** Jeśli w Pobranych leży już plik o nazwie `index.html`, przeglądarka zapisze nowy jako `index_1.html`. GitHub doda go wtedy obok starego zamiast podmienić, a strona dalej będzie pokazywać poprzednią wersję i **nic nie zasygnalizuje błędu**. Dlatego krok pierwszy jest krokiem pierwszym.

Jeśli mimo wszystko wgrasz plik pod złą nazwą: otwórz go w repozytorium, kliknij ikonę edycji, zmień nazwę w polu na górze na `index.html` i zatwierdź. Stary plik trzeba wcześniej usunąć.

---

## Jak to liczy

Wszystkie trzy warianty dostają **tę samą ilość wody**, wyliczoną z jednego pola: liczba osób razy zużycie na osobę razy dni w miesiącu. Liczba butelek i galonów wynika z tej ilości, nie odwrotnie.

```
litry           = osoby × zużycie na osobę × dni
butelek         = zaokrąglenie w górę (litry ÷ pojemność butelki)
galonów         = zaokrąglenie w górę (litry ÷ pojemność galonu)

butelki         = butelek × cena + logistyka + obsługa
galony          = galonów × cena + logistyka + wynajem + serwis + obsługa
dystrybutor     = litry × cena wody z sieci + abonament + serwis
```

Każda pozycja, która wchodzi do sumy, ma swój widoczny wiersz w wyniku. Suma kolumny zawsze zgadza się z tym, co widać nad nią.

### Trzy decyzje, które warto znać

**Kaucje są poza kosztem miesięcznym.** Są zwrotne, więc liczenie ich co miesiąc zawyżałoby koszt butelek i galonów. Pokazujemy je osobno, jako kapitał zamrożony w opakowaniach będących w obiegu.

**VAT albo wszędzie, albo nigdzie.** Jeden przełącznik na górze strony przelicza wszystkie trzy warianty naraz. Domyślnie netto, bo dla firm rozliczających VAT jest on przelewaniem z kieszeni do kieszeni.

**Czas pracy jest domyślnie wyłączony.** Noszenie, magazynowanie i przyjmowanie dostaw kosztują, ale wielu firmom trudno przypisać temu kwotę. Wynik opiera się więc wyłącznie na twardych kosztach, a czas ludzi można dołączyć jednym kliknięciem. Po włączeniu liczy się w każdym wariancie tak samo, według podanej stawki godzinowej.

---

## Sekcja dla gastronomii i hoteli

Zwinięta, otwiera się po kliknięciu presetu **Hotel**.

Nie prognozuje przychodu, bo sprzedaż lokalu to nie jest coś, co da się przewidzieć z zewnątrz. Zamiast tego liczy **próg opłacalności**: ile sztuk danej pozycji z karty musi zejść w miesiącu, żeby urządzenie kosztowało zero.

```
marża na sztuce = cena w karcie − koszt dodatków − woda z sieci − CO2
próg            = zaokrąglenie w górę (abonament + serwis) ÷ marża
```

Trzy pozycje liczone osobno: karafka wody, karafka lemoniady i herbata z wrzątku. CO2 doliczane jest do wody i lemoniady, herbata go nie potrzebuje. Wydajność butli CO2 i cena wymiany są polami do edycji, więc widać, ile dokładnie kosztuje jedna karafka gazowana.

Sekcja pokazuje też liczbę butelek, które w skali roku nie powstaną, oraz koszt krańcowy karafki po przekroczeniu progu.

---

## Wartości domyślne

To są **szacunki rynkowe, nie oferta**. Każde pole można podmienić, a wynik przelicza się natychmiast. Wartości dobrane ostrożnie, tak żeby wynik nie zależał od optymistycznych założeń.

| | Domyślnie |
|---|---|
| Butelka 1,5 L | 1,50 zł, kaucja 0,50 zł |
| Galon 18,9 L | 15 zł, kaucja 30 zł, wynajem 40 zł/mies. |
| Dystrybutor | abonament od 280 zł, serwis 10 zł |
| Woda z sieci | 0,01 zł/L |
| Stawka godzinowa | 45 zł |
| Karafka w karcie | woda 12 zł, lemoniada 20 zł, herbata 12 zł |
| Butla CO2 | 100 zł na 850 L wody gazowanej |

---

## Wysyłanie klientowi konkretnego wyliczenia

Każda zmiana pola zapisuje się w adresie strony. Ustaw parametry pod dany obiekt, kliknij **Skopiuj link z tym wyliczeniem** i wyślij. Klient otworzy stronę ze swoimi liczbami, nie domyślnymi.

Strona jest przygotowana do druku i zapisu do PDF, więc wyliczenie można przekazać dalej w organizacji.

---

## Kontakt

Bartosz Rudnik, Water Point System
bartosz.rudnik@grupaliberta.pl
