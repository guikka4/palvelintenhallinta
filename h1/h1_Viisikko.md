# h1 Viisikko
Tämä on palvelinten hallinta -kurssin ensimmäisen viikkotehtävän raportti. Raportti koostuu kuudesta tehtävästä (x-e) ja niiden ratkaisuista. Tehtävänanto löytyy https://terokarvinen.com/palvelinten-hallinta/#h1-viisikko.
Työskentely tapahtuu kotona omalla kannettavalla, joka on kevyeen pelikäyttöön tarkoitettu. Käyttöjärjestelmänä Windows 11 Home, ja tehtävien tekemiseen VirtualBoxin kautta asennettu Linux Debian Bookworm.

## x) Lue ja tiivistä
Raportissa on tiivistettynä artikkelien keskeinen sisältö.
### Run Salt Command Locally
- Salt komentoja voi ajaa paikallisesti, mutta yleensä sitä käytettään ison määrän "orja"koneiden hallitsemiseen.
- Tärkeimmät keskitetyn hallinnan tilafunktiot ovat pkg, file, service, user ja cmd
- Ärtikkeli esittelee komennot edellisten tilafunktioiden ajamiseen
(Karvinen, T. 2021. https://terokarvinen.com/2021/salt-run-command-locally/)
### Salt Quickstart – Salt Stack Master and Slave on Ubuntu Linux
- Artikkeli esittelee Saltin masterin ja orjan asennuksen sekä komentoja, joilla orjia voi käskeä
- Orjatietokoneet voivat olla missä päin verkkoa tahansa: muutetussa IP-osoitteessa, palomuurin takana ja tuntemattomassa osoitteessa ja niitä pystyy silti hallitsemaan
- Ainoastaan master-palvelimella pitää olla julkinen palvelin sekä tunnettu osoite
(Karvinen, T.2018. https://terokarvinen.com/2018/03/28/salt-quickstart-salt-stack-master-and-slave-on-ubuntu-linux/)
### Raportin kirjoittaminen
- Raporttia tulee kirjoittaa samalla kun työskentelee
- Raportti toimii samalla muistiinpanoina
- Varsinkin vikatilanteissa raportin tekeminen on tärkeää
- Raportin tulisi olla täsmällinen, kaikkine polkuineen, tapahtumineen, kellonaikoineen sekä ympäristöineen jossa tehtäviä suoritetaan
- Raportissa tulisi olla siisti ulkoasu, jotta sen lukeminen helpottuu
(Karvinen, T. 2006. https://terokarvinen.com/2006/06/04/raportin-kirjoittaminen-4/)

## a) Debian 12 Bookwormin asennus virtuaalikoneeseen 28.10.2024 17:10-17:40
Asennus toimii. Ohjeet https://terokarvinen.com/2021/install-debian-on-virtualbox/
Asennuksen jälkeen päivitys, uprgradet, palomuuri sekä palomuurin päälle laittaminen. Komennot alla
'sudo apt-get update'
'sudo apt-get -y dist-upgrade'
'sudo apt-get -y install ufw'
'sudo ufw enable'

## b) Saltin asennus virtuaalikoneelle


## c) Viisi tärkeintä tilafunktiota


## d) Idempotentti


## e) Herra-orja arkkitehtuuri


## Lähteet
- Karvinen, T. 2006. https://terokarvinen.com/2006/06/04/raportin-kirjoittaminen-4/. Luettavissa 26.10.2024
- Karvinen, T. 2018. https://terokarvinen.com/2018/03/28/salt-quickstart-salt-stack-master-and-slave-on-ubuntu-linux/. Luettavissa 26.10.2024
- Karvinen, T. 2021. https://terokarvinen.com/2021/install-debian-on-virtualbox/. Luettavissa 28.10.2024
- Karvinen, T. 2021. https://terokarvinen.com/2021/salt-run-command-locally/. Luettavissa 26.10.2024

