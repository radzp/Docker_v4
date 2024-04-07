# Docker_v4

### Index.html file: 
<img width="1438" alt="screenshot" src="https://github.com/radzp/Docker_v4/assets/98003017/fdb5e58d-9111-4535-a029-59e8993f2e22">

## Użyte polecenia- opis:
### 1. 
### ``` $ docker build -t local/web100 . ```
Polecenie służy do budowania obrazu Docker na podstawie pliku Dockerfile znajdującego się w bieżącym katalogu (katalog: sprawozdanie4).

<img width="1010" alt="Zrzut ekranu 2024-04-7 o 20 26 48" src="https://github.com/radzp/Docker_v4/assets/98003017/f97ee151-5f82-44d8-9788-f62f1b375c59">

### 2.

### ``` % docker run -d --name lab4 -p 8080:80 local/web100 ```
Polecenie uruchamia kontener Docker na podstawie zbudowanego obrazu local/web100. Po wykonaniu tego polecenia, kontener zostanie uruchomiony w tle. Serwer Apache będzie działał i nasłuchiwał na porcie 80 w kontenerze, a port 8080 hosta będzie przekierowany na ten port. 

<img width="1281" alt="Zrzut ekranu 2024-04-7 o 20 34 08" src="https://github.com/radzp/Docker_v4/assets/98003017/6e554a4c-7c39-4a30-91ed-e3eb4791b7ba">

### 3. 
### ``` % docker history local/web100 ```
Użycie tego polecenia sprawi, że zostanie wyświetlona lista warstw obrazu Docker local/web100, wraz z informacjami o każdej z tych warstw (4).

<img width="1275" alt="Zrzut ekranu 2024-04-7 o 20 39 27" src="https://github.com/radzp/Docker_v4/assets/98003017/9ab61f2f-f622-43c3-bfcd-4987a5c07520">

## Dockerfile- wyjaśnienie poleceń:

<img width="1159" alt="Zrzut ekranu 2024-04-7 o 20 46 58" src="https://github.com/radzp/Docker_v4/assets/98003017/653c70b0-0681-4a01-bfb0-78e6ef167051">

## Opis
#### Określenie obrazu bazowego, z którego będę budować obraz Docker. Tutaj używam najnowszej dostępnej wersji obrazu Ubuntu "latest".
* ``` FROM ubuntu:latest ```

#### Dodanie informacji dotyczących obrazu, informacje o autorze: imię, nazwisko oraz adres e-mail.
* ``` LABEL org.opencontainers.image.authors="Anna Paczesna <anne.paczesna@gmail.com>" ```

#### Aktualizacja i uaktualnienie pakietów systemowych wewnątrz obrazu Ubuntu.
* ``` RUN apt-get update && apt-get upgrade -y ```

#### Instalacja serwera Apache
* ``` RUN apt-get install -y apache2 ```

#### Skopiowanie pliku index.html do katalogu serwera WWW
* ``` COPY index.html /var/www/html/index.html ```

#### Expose portu 8080, na którym będzie działać serwer Apache, nasłuchiwanie na porcie 8080.
* ``` EXPOSE 8080 ```

#### Uruchomienie serwera Apache w trybie FOREGROUND.
* ``` CMD ["apachectl", "-D", "FOREGROUND"] ```


