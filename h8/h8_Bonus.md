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

![Add file: Upload](h8_kuvat/k1.png)

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

![Add file: Upload](h8_kuvat/k2.png)

### Sama käyttäen Saltia 11.12.2024 11:15-
Aloitin kopioimalla Saltia käyttäen juuri luodut tiedostot test.conf ja index.html salt-moduuliin. Tein ensin moduulikansion ja tein sinne tiedoston, jonka tilan ajoin. Näin sain tiedostot kopioitua Saltia käyttäen moduulikansioon.

    sudo mkdir -p /srv/salt/apache2
    cd /srv/salt/apache2

    sudoedit init.sls

    #init.sls

    apache2:
      pkg.installed

    /srv/salt/apache2/test.conf:
      file.managed:
        - source: "/etc/apache2/sites-available/test.conf"

    /srv/salt/apache2/index.html:
      file.managed:
        - source: "/home/bassi/publicweb/index.html"

Sitten ajoin moduulin. Kuvakaappauksessa lopputulema idempotenttina

    sudo salt-call --local -l debug state.apply apache2

tähän k3

Tämän jälkeen muokkasin init.sls tiedostoa niin, että sen sisältö asentaisi apachen minioneille, ja siirtäisi tiedostot oikeisiin paikkoihin luoden hakemistopolut, mikäli niitä ei ole. Lisäksi tein käyttäjän, joka jatkossa hallinnoi palvelinta. Tila on kuitenkin tässä tehtävässä ajettu lokaalisti.

    #init.sls

    apacheuser:
      user.present

    apache2:
      pkg.installed

    /etc/apache2/sites-available/test.conf:
      file.managed:
        - source: "salt://apache2/test.conf"

    /home/apacheuser/publicweb/index.html:
      file.managed:
        - source: "salt://apache2/index.html"
        - makedirs: True

Homma onnistui tällä yrittämällä.

    sudo salt-call --local -l debug state.apply apache2
    
k4

## Lähteet
- Karvinen, T. 2018. Nabe based virtual host. https://terokarvinen.com/2018/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/?fromSearch=virtual%20host
- Karvinen, T. 2024. Tehtävä h2: i. https://terokarvinen.com/palvelinten-hallinta/#h2-infra-as-code
