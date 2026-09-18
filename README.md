# Kalkulator kosztów wody

Narzędzie porównujące realny koszt wody w firmie w trzech wariantach: woda butelkowana 1,5 L, galony 18,9 L i dystrybutor podłączony do sieci wodociągowej. Dla HoReCa liczy dodatkowo próg opłacalności na sprzedaży karafek.

**https://bartolek1983.github.io/kalkulator-wody/**

Jedna strona bez serwera i bez bazy danych. Wszystko liczy się w przeglądarce, żadne dane nie opuszczają urządzenia użytkownika. Każde założenie jest polem edytowalnym, a wynik przelicza się natychmiast.

---

## Metodologia

Wszystkie trzy warianty dostają **tę samą ilość wody**, wyliczoną z jednego pola. Liczba butelek i galonów wynika z tej ilości, nie odwrotnie. To jedyny sposób, żeby porównanie miało sens.

```
litry        = osoby × zużycie na osobę × dni
butelek      = ⌈ litry ÷ pojemność butelki ⌉
galonów      = ⌈ litry ÷ pojemność galonu ⌉

butelki      = butelek × cena + logistyka + obsługa
galony       = galonów × cena + logistyka + wynajem + serwis + obsługa
dystrybutor  = litry × cena wody z sieci + (abonament + serwis) × liczba urządzeń
```

Każda pozycja wchodząca do sumy ma swój widoczny wiersz w wyniku. Suma kolumny zawsze zgadza się z tym, co widać nad nią.

### Trzy decyzje, które kształtują wynik

**Kaucje są poza kosztem miesięcznym.** Kaucja jest zwrotna, więc naliczanie jej co miesiąc zawyżałoby koszt butelek i galonów. Pokazujemy ją osobno, jako kapitał zamrożony w opakowaniach będących w obiegu.

**VAT albo wszędzie, albo nigdzie.** Jeden przełącznik przelicza wszystkie trzy warianty naraz. Domyślnie netto, ponieważ dla firm rozliczających VAT jest on przelewaniem z kieszeni do kieszeni.

**Czas pracy jest domyślnie wyłączony.** Noszenie, magazynowanie i przyjmowanie dostaw kosztują, ale niełatwo przypisać im kwotę, której nikt nie podważy. Wynik podstawowy opiera się więc wyłącznie na kosztach twardych. Po włączeniu czas liczy się w każdym wariancie tak samo.

---

## Sekcja HoReCa

Otwiera się po wybraniu presetu Hotel lub Restauracja. Nie prognozuje przychodu lokalu, bo tego nie da się oszacować z zewnątrz. Liczy **próg opłacalności**: ile sztuk danej pozycji z karty musi zejść w miesiącu, żeby urządzenie kosztowało zero.

```
marża na sztuce = cena w karcie − koszt składników − woda z sieci − CO2
próg            = ⌈ koszt urządzeń ÷ marża ⌉
```

Trzy pozycje liczone niezależnie: karafka wody, karafka lemoniady i herbata z wrzątku. Sekcja podaje też liczbę butelek, które w skali roku nie powstaną, oraz koszt krańcowy karafki po przekroczeniu progu.

---

## Techniczne

Jeden plik `index.html`: struktura, style i skrypt w jednym, logo osadzone jako dane. Bez zależności, bez procesu budowania, bez frameworka.

Hosting: GitHub Pages, gałąź `main`, katalog główny. Wdrożenie następuje automatycznie po każdym commicie do `main`.

Stan wszystkich pól zapisuje się w adresie strony, więc wyliczenie można przesłać linkiem. Obsługuje jasny i ciemny motyw systemowy, układ mobilny od 360 px wzwyż oraz wydruk do PDF.

---

## Kontakt

Bartosz Rudnik, Water Point System
bartosz.rudnik@grupaliberta.pl
