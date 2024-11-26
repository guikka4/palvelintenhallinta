# h4 Puolikas
Tarkoituksenani on viritellä pieni virtuaaliympäristö, jossa luon Vagrantin avulla uusia virtuaalikoneita. Koneet käyttävät Debian 12 Bookwormia. Eri koneille asennellaan eri käyttöön tarkoitettavia palvelimia, sekä määritellään niille käyttäjät sekä käyttäjille kotihakemistot. Olin ajatellut asennettaville palvelinkoneille ainakin Apachea sekä PostgreSQL:ää. Kaikki asennukset sekä käyttäjien luonti tapahtuu käyttäen keskitetyn hallinnan ohjelmistoa, SaltStackia. Yhdestä virtuaalikoneesta tulee siis master, josta valutetaan käskyt minion koneille. Lisäksi jokaiselle virtuaalikoneelle luodaan vielä SSH-varayhteys määrittäen uusi avoin tcp portti.

Raportin kirjoittamisen alkuhetki on 26.11.2024 klo 17:15. Sisältö voi muuttua lennosta olennaisestikin, riippuen siitä, miten työ edistyy. Jokainen työvaihe on tarkoitus raportoida, kaikki toimet tehdä ensin käsin, jonka jälkeen automatisoida. Testeistä raportoidaan.

Raportin kirjoittamisessa käytän selainta HostOS:n puolella. HostOS on Windows 11, ja käytettävä rauta on kevyeen pelikäyttöön tarkoitettu kannettava tietokone. Vagrant ssh:n operoinnissa (virtuaalikoneet) käytän Windows PowerShelliä.

Tehtävänanto https://terokarvinen.com/palvelinten-hallinta/#h4-puolikas.

## HostOS
- Asus Tuf Gaming A15 FA506QM kannettava tietokone
- Käyttöjärjestelmä: Windows 11 Home
- Prosessori: AMD Ryzen 7 5800H, 8 ydintä 3200GHz
- Muisti: 16 Gt
- Näytönohjain NVIDIA GeForce RTX 3060 laptop, 6144Mt omalla muistilla

# Virtuaaliympäristö pystyyn



# SaltStack asennus



## Apache2



## PostgreSQL



## Työpöytä

## Lähteet
- Karvinen, T. 2024. Tehtävänanto https://terokarvinen.com/palvelinten-hallinta/#h4-puolikas. Luettavissa 26.11.2024
