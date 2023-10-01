Laboratorium: Podstawowa SSRF przeciwko lokalnemu serwerowi
Pierwszym krokiem jest zidentyfikowanie gdzie może znajdować się podatność SSRF.
Podatność znajduje się na każdym wybranym nazwijmy to wpisie, poniżej wpisu znajduje się ```Check stock``` i tutaj już się zaczyna nasza przygoda z podatnością SSRF. musimy uzyskać dostęp do interfejsu administratora na http://localhost/adminI usunąć użytkownika carlos.
Pierwszym krokiem jest edytowanie StockApi, StockApi=http://localhost/admin, musimy pamiętać aby zakodować to w URL. Uzyskaliśmy dostęp "do panelu administracyjnego"

![obraz](https://github.com/Anogota/PortSwigger-SSRF/assets/143951834/60ee3066-bff0-4769-9c94-efa156c00543)

Dzięki temu wiemy, że znajduje się tutaj na 100% podatność SSRF. Teraz musimy usunąć carlosa.
```stockApi=http%3a//localhost/admin/delete%3fusername%3dcarlos```
Dzięki temu możemy usunąć carlos i uda nam się rozwiązać zadanie.

Laboratorium: Podstawowy SSRF przeciwko innemu systemowi zaplecza
Proces indetyfikacji podatności wygląda jak powyżej. Ale napotykamy tutaj coś ciekawego, musimy zeskanować adres IP aby dowiedzieć się na jakim lokalnym porcie działa ten panel administracyjny.
Pierwszym krokiem jest przechwycenie pakietu i wrzucanie go do intrudera, w intruderze musimy to wyglądać następująco.
```
stockApi=http://192.168.0.§X§:8080/admin
```
I musimy w payload ustawić, payload type number from 0 to 256 step 1.
Dzięki temu uzyskaliśmy adres IP 
 
