# Bakcyl programowania 2022
---
# Test grupa zaawansowana

## Test składa się z czterech zadań.

Czytaj ze zrozumieniem, każde słowo ma znaczenie :)

Wyślij tyle, ile udało Ci się zrobić.

Nie zrobiłeś wszystkich zadań? Nie przejmuj się I wyślij nam to co masz :)


## Na co zwracamy uwagę ?
- wysłanie zadanie zgodnie z podaną wyżej instrukcją
- kod pisany w języku angielskim
- zachowanie zasad clean code (nie wiesz co to? Wygoogluj :-) )
- odpowienie używanie słów kluczowych takich jak public, private, protected, const itp.
- poprawność rozwiązania

## Wysyłanie rozwiązań

- Każde rozwiązanie musi znajdować się w katalogu zawierającym numera zadania.
- Wszystkie rozwiązania muszą być spakowane w archiwum nazwane imieniem oraz nazwiskiem autora
- Archiwum musi zostać dodane do maila, którego tytuł wygląda następująco
    - [Bakcyl2022][TEST_ZAAWANSOWANA][Imię i nazwisko]
    - za "Imię i nazwisko" podstaw swoje dane!
    - Maile z innym tytułem trafią prwadopodbnie do spamu i nie zostaną ocenione.
    - Jeśli wysłałeś maila ze złym tytułem nie przejmuj się I wyślij go jeszcze raz, tym razem poprawnie :)

- Maila należy wysłać na podane adresy:  
    - patryk.kaczmarek@nokia.com
    - wozniak1008@gmail.com
- Rozwiązania zadań należy wysłać do 24:00 19.10.2022 (tj. na rozwiązanie przewidziane jest 7 godzin)
- Rozwiązania przesłane później lub zawierające niepoprawny tytuł nie będą oceniane.

# POWODZENIA :)

---
## Zadania


### 1. Zaproponuj rozwiązanie problemu [konwersji liczby z systemu binarnego na dziesiętny](https://www.wikihow.com/Convert-from-Binary-to-Decimal)

Prototyp funkcji:
```c
std::uint32_t convert(std::string input)
```

Funkcja powinna rozpoznawać nieprawidłowy format danych wejściowych i rzucać wyjątkiem w tym przypadku.
Za nieprawidłowy format uznajemy ciąg znaków składający się ze znaków innych niż `0` i `1` oraz ciąg dłuższy niż `32` znaki.

#### Przykłady:

1. `convert("01")` => 1
2. `convert("010011001")` => 153
3. `convert("10011001")` => 153
4. `convert("")` => error
5. `convert("110011001100110011001100110011001")` => error
6. `convert("Ala ma kota")` => error
7. `convert("12345")` => error

### 2. Implementacja wirtualnej klasy `Language`

Stwórz abstrakcyjną klasę bazową `Language`. Klasa powinna
dostarczać interfejs składający sie z czterech metod:
```C
- std::string getLanguage()
- bool addTranslation(std::string inputToTranslationInPolish, std::string translatedInput)
- bool updateTranslation(std::string inputToTranslationInPolish, std::string translatedInput)
- std::string getTranslation(std::string)
```
Następnie stwórz klasy `German` oraz `English`. Klasy te mają dziedziczyć po klasie `Language`.

Metoda `getLanguage()` powinna zwracać nazwę języka.

Metoda `addTranslation(std::string inputToTranslationInPolish, std::string translatedInput)` ma dodawać do klasy tłumaczenie
i przechowywać je w obiekcie `std::map<string, string>`, gdzie klucz to słowo w języku polskim, a wartość tłumaczenie w języku obcym.

Metoda ta ma zwracać wartość `true` lub `false`, w zależności czy udało dodać się obiekt do mapy (Dodanie istniejącego już tłumaczenia, powinno zwrócić wartość `false`)

Metoda `updateTranslation(std::string inputToTranslationInPolish, std::string translatedInput)` ma aktualizować tłumaczenie.
Jeśli tłumaczenie nie istnieje, metoda powinna zwrócić wartość `false`.

Metoda `getTranslation` powinna zwracać frazę przetłumaczoną na język obcy lub pusty `std::string`, jeśli tłumaczenie nie zostało dodane.


Klasa `German` może przechowywać maksymalnie 2 tłumaczenia, natomiast klasa `English` 5.


Po stworzeniu tych trzech klas w funkcji głównej main() stwórz:

- wektor, w którym będzie można przetrzymywać jednocześnie obiekty klas `German` oraz `English` (polimorfizm)
- obiekt klasy `German` oraz obiekt klasy `English`
- dodaj po jednym tłumaczeniu do klasy `German` oraz `English` dla tego samego zwrotu/słowa w języku polskim
- umieść obiekt klasy `German` oraz obiekt klasy `English` w stworzonym wcześniej wektorze
- z użyciem pętli, wykonaj iterację przez wektor i na każdym przechowywanym w nim obiekcie
wywołaj metodę `getLanguage()` oraz pobierz tłumaczenie wcześniej dodanej frazy 



### 3. Zaproponuj rozwiązanie problemu kodowania/dekodowania wiadomości przy pomocy [szyfru Cezara](https://en.wikipedia.org/wiki/Caesar_cipher)

#### Prototyp klasy: 
```c
class CaesarCipher {
public:
    CaesarCipher(const int shift);
    std::string encrypt(const std::string& message);
    std::string decrypt(const std::string& encryptedMessage);
};
```

Dla uproszczenia rozwiązania w zadaniu rozważamy alfabet angielski tj. [ A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z]

Dozwolone są zarówno wielkie jak i małe litery. Wielkość liter powinna zostać niezmienna.

Wszystkie znaki inne niż znaki alfabetu powinny pozostać bez zmian.


### 4. Zaproponuj rozwiązanie problemu poszukiwania maksymalnej sumy elementów w ciągu/tablicy

#### Prototyp funkcji: 
```c
Result maxSubarraySum(const std::vector<int>& numbers)
```
#### Struktura Result: 
```c
struct Result {
    std::vector<int>::const_iterator start;
    std::vector<int>::const_iterator end;
    int sum;
};
```

#### Przykłady[ **pogrubione elementy maksymalnej sumy**] :

1.  [**1, 2, 3, 5**] => 11
2.	[-2, 1, -3, **4, -1, 2, 1,** -5, 4] => 6
3.	[] => 0
4.	[-2, -3, -5] => 0

#### Przypadki testowe: 

1.	[7, 4, 11, -11, 39, 36, 10, -6, 37, -10, -32, 44, -26, -34, 43, 43] => 155
2.	[-22, -15, -7, -11, 10, -2, -17, 21, 21, 27, 21, -8, -17, 21, 1, -28, -1, -15, -29, -1, -20, -18, 25, -20, 13, 7, 7, 7, -19, 24, -13, -8, -22, 12, 11, 19, -19, 26, 9, -29, 22, -1, -4, -24, -9, 27, -21, 20, -17, -20] => 90
3.	[-19, -6, 7, -2, 3, 9, 14, -20, 20, 20, 29, -10, 22, -27, 2, -14, -28, -6, -2, -21, 24, 5, 4, -19, 0, -22, 13, -9, -23, -15, 12, -10, 11, -9, 19, -16, -29, 4, -4, 21, -7, -3, -20, -15, 2, 15, 3, 4, -20, -29] => 92
4.	[6, 28, 10, 19, 12, 28, -15, 26, -6, -6, -18, 21, 8, 16, -19, 6, 18, 3, 17, -28, 7, -15, -2, -24, 9, -19, 20, -29, 18, 20, 15, -7, 18, -3, -17, 1, -6, -2, -4, 20, 22, 11, 12, 2, -2, 23, -21, -15, -4, 26] => 194

