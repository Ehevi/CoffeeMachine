# Automatyczny ekspres do kawy
## Opis modelowanego systemu
### Przyjęte definicje
1. __`Podstawowe składniki`__, czyli `ziarna kawy`, `mleko`, `woda`. Żeby przygotować napój, użytkownik najpierw musi nimi uzupełnić odpowiednie pojemniki. O braku podstawowych składników użytkownik jest informowany za pomocą wyświetlacza.
2. __`Składniki`__, czyli `espresso`, `woda`, `mleko`, `spienione mleko`. Baza do przygotowania napojów - są to podstawowe składniki po poddaniu ich opowiedniej obróbce, tzn. podgrzaniu do określonej temperatury oraz wykonaniu różnych innych czynności, w zależności od potrzeb (zmienielenie kawy, zaparzenie kawy, spienienie mleka).
3. __`Instrukcja przygotowania napoju`__ - składniki ułożone w ciąg w kolejności, w której powinny znaleźć się w szklance. Bazowe porcje składników są stałe, ale w danym ciągu mogą występować wielokrotnie (np. podwójne espresso).
4. __`Napój`__ - efekt końcowy wykonania przez ekspres odpowiedniej instrukcji. Przykłady:
```
    Espresso: espresso
    Double espresso: espresso, espresso
    Americano: espresso, woda
    Cortado: espresso, mleko
    Flat white: espresso, spienione mleko
    Caffè latte: espresso, mleko, spienione mleko
    Latte macchiato: mleko, espresso, spienione mleko
    Cappuccino: espresso, spienione mleko, spienione mleko
```
### Scenariusz użytkowania systemu:
1. Użytkownik naciskając odpowiedni guzik wybiera program przygotowujący pożądany napój.
2. Ekspres analizuje dane z czujników w pojemnikach w celu sprawdzenia, czy znajduje się tam wystarczająco dużo podstawowych składników. Jeżeli nie, informuje o tym użytkownika i zawiesza dalsze działanie do czasu ich uzupełnienia.
3. Ekspres przygotowuje wybrany napój na podstawie zaprogramowanej sekwencji. Podsystem odpowiedzialny za przygotowanie kawy na bieżąco przygotowuje składniki napoju i wlewa je do szklanki.
4. Ekspres informuje użytkownika o zakończeniu przygotowywania napoju.

### Model środowiska i interakcji użytkownika z systemem
![system_env](https://user-images.githubusercontent.com/48785655/174123763-712a8071-8c97-4cb1-90e6-071942e80cae.png)

## Spis komponentów wraz z komentarzem
## Model - rysunek
## Proponowane metody analizy - dostępne w Osate
## Inne informacje zależne od tematu
