# h8 Bonus
Tämä raportti sisältää Palvelinten hallinta -kurssin (2024syksy) vapaaehtoiset tehtävät. Tehtävissä on lyhyet tehtävänkuvaukset, sekä linkit tehtävänantoihin.

Työskentely tapahtuu kotioloissa. HostOS on Windows 11 Home (64), joka pyörii kevyeen pelikäyttöön tarkoitetulla kannettavalla tietokoneella. GuestOS VirtualBox ja Debian12 Bookworm(64). 

## a) Vapaaehtoiset tehtävät
Tästä löytyy vapaaehtoiset Bonus-tehtävät

### h2 infra as a code: tehtävä i) Asenna ja konfiguroi Apache. 11.12.2024 10:25-11:00
Tehtävässä on tarkoitus asentaa Apache web-palvelin, ja korvata sen etusivu näyttämään web-sivua. Web-sivun tulee olla muokattavissa ilman sudo-oikeuksia.
[Tehtävänanto](https://terokarvinen.com/palvelinten-hallinta/#h2-infra-as-code). [Vinkit](https://terokarvinen.com/2018/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/?fromSearch=virtual%20host) tehtävän tekoon.

Lähtötilanteessa Apachea ei ole asennettu. Tämän totesin `sudo systemctl status apache2` komennolla. Vastaus oli "Unit apache2.service could not be found".
Sitten asennus.

    sudo apt-get update
    sudo apt-get -y install apache2

    sudo systemctl status apache2 #näyttää asennetun statuksen.
    curl localhost # näyttää apache2 palvelimen oletussivun

Asennus onnistui.
tähän k1

Tämän jälkeen oli vuorossa konfig-tiedoston tekeminen

    sudoedit /etc/apache2/sites-available/test.conf

    #test.conf sisältö
    
    <VirtualHost *:80>
      ServerName test.com
      ServerAlias www.test.com

              DocumentRoot /home/bassi/publicweb/
              <Directory /home/bassi/publicweb/>

                      Require all granted

              </Directory>
    </Virtualhost>

Web sivun teko

    mkdir -p /home/bassi/publicweb/
    echo testing > /home/bassi/publicweb/index.html
    micro /home/bassi/publicweb/index.html

    #index.html sisältö
    
    <!doctype html>

      <html lang="fi">
        <head>
        <meta charset="UTF-8">
        <title>Etusivun korvaus</title>
        </head>

    <body>

      <h1>Otsikkotaso</h1>

      <p>Korvasin etusivun</p>

    </body>
    </html>

Korvasin käytössä olleen apachen default-sivun

    sudo a2dissite 000-default.conf
    sudo a2ensite test.conf
    
Käynnistin palvelimen uudelleen ja tarkistin lopputuloksen

    sudo systemctl restart apache2
    curl localhost

tähän k2


## Lähteet
- Karvinen, T. 2024. Tehtävä h2: i. https://terokarvinen.com/palvelinten-hallinta/#h2-infra-as-code
