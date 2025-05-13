1. Aplikacja została napisana w języku Go. Po uruchomieniu:
  - W logach zapisuje datę, imię i nazwisko autora oraz port TCP (8080).
  - Udostępnia interfejs webowy, który umożliwia wybór kraju i miasta z listy.
  - Pobiera dane pogodowe z serwisu OpenWeatherMap na podstawie wprowadzonych       danych.
    Kod aplikacji znajduję się w pliku app.go

2. Plik Dockerfile tworzy obraz umożliwiający uruchomienie aplikacji opracowanej w punkcie 1 jako kontener Docker.
   
3. Użyte polecenia:
   
   a) Budowanie obrazu kontenera
   
     docker build -t app_pogoda .

   b) Uruchomienie kontenera
   
     docker run -d -p 8080:8080 --name pogoda_app -e OPENWEATHER_API_KEY=           <tutaj_klucz_API> app_pogoda
   
   c) Pobranie logów z aplikacji
   
     docker logs pogoda_app
   
   d) Sprawdzenie liczby warstw i rozmiaru obrazu
   
     docker image inspect app_pogoda --format='{{len .RootFS.Layers}} layers'
   
     docker image inspect app_pogoda --format='{{.Size}} bytes'

