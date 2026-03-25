# Lokalizacja punktu w przestrzeni 2D

## Algorytm Kirkpatricka (Point Location)

Projekt przedstawia implementację oraz wizualizację algorytmu **Kirkpatricka** służącego do efektywnej lokalizacji punktu w podziale triangulowanym.


## Opis problemu

Dany jest podział płaszczyzny na trójkąty (triangulacja). Celem jest szybkie określenie, w którym trójkącie znajduje się zadany punkt.


## Algorytm Kirkpatricka – idea

Algorytm działa w dwóch etapach:

### 1. Preprocessing (budowa hierarchii)

* Wejściem jest triangulacja
* Tworzona jest hierarchia triangulacji:
* Każda kolejna triangulacja:

  * ma mniej wierzchołków
  * jest „grubszym” przybliżeniem poprzedniej
* Proces kończy się na pojedynczym trójkącie obejmującym całość

#### Kluczowe kroki:

* wybór zbioru niezależnego wierzchołków
* usunięcie ich z grafu
* ponowna triangulacja powstałych dziur

### 2. Lokalizacja punktu

* Start od najwyższego poziomu
* Schodzenie w dół hierarchii:
  * wybieramy trójkąt zawierający punkt

## Struktura danych

* Hierarchia ma postać DAG (Directed Acyclic Graph)
* Wierzchołki = trójkąty
* Krawędź: jeśli trójkąt niższego poziomu zawiera się w wyższym


## Złożoność

| Operacja                     | Złożoność    |
| ---------------------------- | ------------ |
| Preprocessing (triangulacja) | O(n log n)   |
| Budowa hierarchii            | O(n)         |
| Pamięć                       | O(n)         |
| Lokalizacja punktu           | O(log n) |


##  Lemat o zbiorze niezależnym

Każda triangulacja planarnego grafu zawiera zbiór niezależny:

* rozmiaru ≥ n/18
* o stopniu ≤ 8
* możliwy do znalezienia w czasie O(n)

Dzięki temu:

* w każdym kroku usuwamy stałą część wierzchołków
* liczba poziomów wynosi **O(log n)**


## Wizualizacja

**[Wizualizacja](https://github.com/aghbit/Algorytmy-Geometryczne)**


## Uwagi

* Algorytm jest bardzo wydajny asymptotycznie
* W praktyce posiada dużą stałą → może być mniej efektywny dla małych danych
* Wymaga triangulacji jako danych wejściowych


## Źródła

**[Kirkpatrick](https://ics.uci.edu/~goodrich/teach/geom/notes/Kirkpatrick.pdf)**


## Autorzy

* Bartłomiej Prus
* Mateusz Szwagierczak

