# h2 Infra as code 7.11.2024 14:50-
Tämä on palvelinten hallinta -kurssin toisen viikkotehtävän raportti. Raportti koostuu kuudesta tehtävästä (x-i) ja niiden ratkaisuista. Tehtävänanto löytyy https://terokarvinen.com/palvelinten-hallinta/#h2-infra-as-code. Työskentely tapahtuu kotona omalla kannettavalla, joka on kevyeen pelikäyttöön tarkoitettu. Käyttöjärjestelmänä Windows 11 Home, ja tehtävien tekemiseen VirtualBoxin kautta asennettu Linux Debian Bookworm. Vagrant tehtäviin käytössä Windowsin komentorivi.

## x) Lue ja tiivistä
Raportissa on tiivistetty artikkelien keskeiset sisällöt

### Two Machine Virtual Network With Debian 11 Bullseye and Vagrant
- Artikkelissa on ohjeet kahden virtuaalikoneen asentamiseen ja yhteydenottoon Vagrantilla
- Jokaiselle Vagrantille perustetaan oma "projekti" hakemistoon omalla nimellään, ja sinne luodaan Vagrant-tiedosto, joka sisältää virtuaalikoneiden starttitiedot
- Vagrant toimii käytännössä kaikilla Host-OS:llä
(Karvinen, T. 2021. https://terokarvinen.com/2021/two-machine-virtual-network-with-debian-11-bullseye-and-vagrant/)

### Salt Quickstart – Salt Stack Master and Slave on Ubuntu Linux
- Tiivistelmä ja lähdetiedot https://github.com/guikka4/palvelintenhallinta/blob/main/h1/h1_Viisikko.md

### Hello Salt Infra-as-Code
- Artikkelissa on kerrottu esimerkillä infraa koodina- idea Saltin avulla
- Jokaiseen Saltin "moduuliin" on syytä luoda oma hakemistokansionsa, josta eri tilakomentoja ajetaan
(Karvinen, T. 2024. https://terokarvinen.com/2024/hello-salt-infra-as-code/)

### Salt Vagrant - automatically provision one master and two slaves
- Saltin hakemistoon luotuun moduulikansioon luodaan init.sls tiedosto. Sillä ajetaan moduulikohtaiset tilat
- Saltin hakemiston "ylätasolla", eli moduulikansioiden yläpuolelle luodaan top.sls tiedosto. Siihen määritellään, mitkä orjat tekevät mitäkin.
(Karvinen, T. 2023. https://terokarvinen.com/2023/salt-vagrant/#infra-as-code---your-wishes-as-a-text-file)

### Salt Overview (YAML)
- YAML on koodikieli, jota käytetään Saltissa. Se ikäänkuin "muuntaa" koodinsa python-kielelle
- YAML:ssa oma kirjoitustyylinsä, ja esimerkiksi tabulaattoria ei käytetä ollenkaan. Koodi toimii avain-arvo -parina
- YAML:ssa on kolme pääelementtiä: mappaus (avain : arvo), listat ja hakemistot. Kaikki toimivat kylläkin avain : arvo periaatteella.
- YAML on hyvin jäsennelty, lohkomainen koodauskieli. Siinä sisennetään jokainen oma "lohkonsa". Yleinen sisennystapa on 2 välilyöntiä.
(Saltproject. https://docs.saltproject.io/salt/user-guide/en/latest/topics/overview.html#rules-of-yaml)

## a) Hello Vagrant! 7.11.2024 15:40
Vagrant on asennettu aiemmin hostOS:lle. Komento Powershellistä
`vagrant --version`

tähän kuva h2_1

## b) Linux Vagrant
Tehtävänosassa luodaan Vagrantilla uusi virtuaalikone
`mkdir firstbookworm` uusi kansio virtuaalikoneprojektia ja vagrantfileä varten. Olen siis HostOS:n omassa käyttäjähakemistossa
`vagrant init debian/bookworm64` lataa uusimman debian-version imagen luotuun kansioon

tänän kuva h2_2

    vagrant up
luodaan uusi kone. Tässä kohtaa powershellissä näkyy tekstiä, kun uuden koneen asennus etenee








## Lähteet
- Hartikainen, P. 2024. https://github.com/guikka4/palvelintenhallinta/blob/main/h1/h1_Viisikko.md. Luettavissa 7.11.2024
- Karvinen, T. 2021. https://terokarvinen.com/2021/two-machine-virtual-network-with-debian-11-bullseye-and-vagrant/. Luettavissa 7.11.2024
- Karvinen, T. 2023. https://terokarvinen.com/2023/salt-vagrant/#infra-as-code---your-wishes-as-a-text-file. Luettavissa 7.11.2024
- Karvinen, T. 2024. https://terokarvinen.com/2024/hello-salt-infra-as-code/.Luettavissa 7.11.2024
- Saltproject. https://docs.saltproject.io/salt/user-guide/en/latest/topics/overview.html#rules-of-yaml. Luettavissa 7.11.2024
