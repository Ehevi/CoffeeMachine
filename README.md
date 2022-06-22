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

## System `CoffeeMachine`
### Komponenty główne
- `CoffeeMachineSystem`: główny komponent reprezentujący ekspres do kawy, który łączy pomniejsze komponenty w spójną całość
- `main_controller`: procesor główny odpowiedzialny za zarządzanie procesami obsługującymi interakcję systemu z użytkownikiem, a więc wybór napoju (`drink_selection_process`) oraz kontrolę ilości składników potrzebnych do przygotowania wybranego napoju (`supplies_process`)
- `gpio_bus`: połączenia umożliwiające komunikację urządzeń z procesorem

### Komponenty wykonujące
- `butttons`: urządzenie przyjmujące od użytkownika wybór napoju
- `signalizer`: urządzenie sygnalizujące użytkownikowi konieczność uzupełnienia składników podstawowych lub zakończenie procesu przygotowywania napoju

#### Czujniki
- `water_container_sensor`: monitoruje ilość wody w pojemniku
- `coffee_bean_container_sensor`: monitoruje ilość ziaren kawy w pojemniku
- `milk_container_sensor`: monitoruje ilość mleka w pojemniku
### Komponenty programowe
- `drink_selection_process`: proces przetwarzający wybór użytkownika na instrukcję przygotowania napoju dla podsystemu `CoffeeMaker` - kolejność, w której powinny zostać uruchamiane poszczególne urządzenia tego podsystemu
- `supplies_process`: proces sprawdzający, czy w pojemnikach znajduje się wystarczająco dużo składników, aby przygotować wybrany napój. Jeżeli nie, informacja o tym jest przekazywana do `signalizera` odpowiedzialnego za poinformowanie o tym użytkownika, a dalsze działanie systemu zostaje zawieszone.
### Model
![2-cofmachine](https://user-images.githubusercontent.com/48785655/174969239-2457ee37-a893-48b3-85cb-ea43e6e5d142.png)

## System `CoffeeMaker`
### Komponenty główne
- `CoffeeMakerSystem`: podsystem odpowiedzialny za przygotowanie napoju oraz dostarczenie go użytkownikowi
- `coffee_controller`: procesor zarządzający pracą urządzeń podsystemu

### Komponenty sprzętowe
- `analyzer`: urządzenie przetwarzające sygnały przychodzące z zewnątrz na rozkazy przekazywane do określonego urządzenia. Właściwie fukcjonalność ta równie dobrze mogłaby być realizowana przez procesor i zawierać się w procesie `coffe_making_process`, jednak przypisanie jej osobnego komponentu rozjaśnia schemat przepływu danych na narysowanym modelu.
- `heater`: urządzenie odpowiedzialne za podgrzewanie wody / mleka
- `grinder`: młynek do ziaren kawy. Mielenie kawy odbywa się zawsze bezpośrednio przed jej zaparzeniem i przygotowywana jest dokładnie jedna porcja.
- `press`: urządzenie odpowiedzialne za przelewowe zaparzenie zmielonej kawy. Jednorazowo przygotowuje jedną porcję espresso.
- `foamer`: speniacz do mleka
- `pourer`: urządzenie odpowiedzialne za dostarczenie składników do szklanki
#### Czujniki
- `temp_sensor`: monitoruje temperaturę wody i mleka
### Komponenty programowe
- `coffee_making_process`: proces odpowiedzialny za przygotowanie kawy. Odczytuje instrukcje przygotowania napoju i na ich podstawie zarządza poszczególnymi wątkami przypisanymi do urządzeń.
### Model
![3-coffee_maker](https://user-images.githubusercontent.com/48785655/174969283-255fef1c-89cc-4def-905b-6a7662f9aa71.png)

## Proponowane metody analizy - dostępne w Osate
