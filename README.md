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
5. Uzytkownik zabiera przygotowany napój.

### Model środowiska i interakcji użytkownika z systemem
![1-environment](https://user-images.githubusercontent.com/48785655/174969015-23564e8a-232c-4719-a57b-365e4fbcaf4f.png)

## Spis komponentów wraz z komentarzem
## Model
### System `Coffee machine`
![2-cofmachine](https://user-images.githubusercontent.com/48785655/174969239-2457ee37-a893-48b3-85cb-ea43e6e5d142.png)
### Podsystem `Coffee maker`
![3-coffee_maker](https://user-images.githubusercontent.com/48785655/174969283-255fef1c-89cc-4def-905b-6a7662f9aa71.png)



## Proponowane metody analizy - dostępne w Osate
## Inne informacje zależne od tematu
