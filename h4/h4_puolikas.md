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
Lähtötilanne: Vagrant on asennettuna HostOS:lle.

tähän h4_1

Tarkoitus on ladata Debian12 Bookworm kuva HostOS:n käyttäjäni hakemistoon ja luoda sinne Vagrantfile joka käynnistettäessä tekee viisi virtuaalikonetta, joista yksi toimii masterina ja neljä minionina. Vagrantfilessä on scripti, joka asentaa salt-master ja salt-minion demonit oikeille koneille. Vinkit https://terokarvinen.com/2023/salt-vagrant/?fromSearch=salt%20vagrant%20automati.

Alla olevat komennot tapahtuvat siis HostOS:n puolella.

    mkdir moduleproject
    cd moduleproject

    vagrant init debian/bookworm64

tähän h4_2

Vagrantfile

    

## Apache2



## PostgreSQL



## Työpöytä

## Lähteet
- Karvinen, T. 2023. Salt Vagrant - automatically provision one master and two slaves. https://terokarvinen.com/2023/salt-vagrant/?fromSearch=salt%20vagrant%20automati. Luettavissa 26.11.2024
- Karvinen, T. 2024. Tehtävänanto. https://terokarvinen.com/palvelinten-hallinta/#h4-puolikas. Luettavissa 26.11.2024
- 
