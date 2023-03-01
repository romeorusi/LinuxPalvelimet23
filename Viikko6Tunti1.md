# H10

### Sisällysluettelo
- [Aloitustilanne](#Aloitustilanne) 
- [Tuotantoasennus](#Tuotantoasennus)
- [Lähteet](#lähteet)



# Aloitustilanne

- Aloitetaan 12:55 1/3/2023

### Virtualisointi
- Virtualisoitu VirtualBox 7.0.4
- Käyttöjärjestelmänä Debian GNU/Linux 11 (bullseye) x86-64 arkkitehtuuri 
- 8GB RAM
- 60GB dynaamista muistia (NVMe SSD)
- 2 Corea Ryzen 5 3600 6-core

### "Host" kone
- Win 10 pro x64
- Ryzen 5 3600 6-core
- RTX 3060
- Ram 16GB
- SSD 1 NVMe (~500GB)
- SSD 2 SATA (~500GB)


![add file: upload](V6Kuvat1/v6t1k1.jpg)

# Tuotantoasennus

Tehtävän tarkoituksena on tehdä Djangoon tuotantoasennus. Poistin aikasemmin tekemäni testitiedoston jotta pystyin ohjeiden mukaan tekemään kaiken oikein alusta loppuun. Ensimmäisenä päivitin kaikki paketit ```sudo apt-get update``` ja asensin microon bashin ```sudo apt-get -y install micro bash-completion``` ja laitoin micron pääasialliseksi tekstieditoriksi komennolla ```export EDITOR=micro```. Apache oli valmiina asennettuna, joten sen asennusta en tässä raportissa käy läpi. Tiedettäköön siitä kuitenkin sen verran, että olen aikaisemmin muokannut ```var/www/html/index.html``` kohtaan itselleni sivun, joten tarvittaessa tunnistan onnistuuko vai ei.

Komennolla ```echo "Jotain asiaa"|tee publicwsgi/rtesti/static/index.html``` loin yksinkertaista sisältöä juuri luotuun index.html tiedostoon. Tarkistin onnistuiko komento kirjoittamalla "cat alt + ." joka kopioi aikaisemman tiedostokohteen suoraan komentoriville. Kuten kuvasta huomaa tieto on tallentunut.

![add file: upload](V6Kuvat1/v6t1k1.jpg)


Komennolla ```sudoedit /etc/apache2/sites-available/rtesti.conf``` loin ja pääsin muokkaamaan tiedostoa. Muokkasin tiedosta niin, että sen sisältö vastasi seuraavaa:

    <VirtualHost *:80>
      Alias /static/ /home/rome/publicwsgi/rtesti/static/
      <Directory /home/rome/publicwsgi/rtesti/static/>
        Require all granted
      </Directory>
    </VirtualHost>

Editoidessa tiedostoa huomasin alareunassa seuraavanlaisen polun, joka johtaa temp-tiedostoon. En ole varma koituuko tästä myöhemmin ongelmia, mutta en muista aikaisemmin nähneeni vastaavaa. En myöskään ole täysin varma mitä microon lisätty bash tekee, joten en lähtenyt suoraan selvittämään tätä.

![add file: upload](V6Kuvat1/v6t1k2.jpg)


Seuraavaksi komennoilla

    sudo a2ensite rtesti.conf
    sudo a2dissite frontpage.conf
    sudo systemctl restart apache2

Laitoin oikean sivun päälle ja uudelleenkäynnistin apachen jotta sain asiat päivitettyä.

Seuraavaksi tarkistin toimiiko kaikki tähän asti, komennolla ```/sbin/apache2ctl configtest``` kuten ohjeissakin oli mainittu, mikäli palaute oli pelkästään ongelma AH00558:n kanssa hommat ovat tähän asti oikein. Sain pelkästään tuon "virheilmoituksen" joten kaikki oli ok.

![add file: upload](V6Kuvat1/v6t1k3.jpg)


Tarkistin ```curl http://localhost/static/``` onko kaikki ok tähän asti ja sain palautteeksi aikaisemmin index.html tiedostoon tallentamani "Jotain asiaa". Kaikki siis tässäkin tähän asti ok.

![add file: upload](V6Kuvat1/v6t1k4.jpg)



### Virtualenv

Nyt asentamaan virtualenv. Ajoin kuvassa näkyvät komennot ja ohjeistuksen perusteella tämä luo directoryn kohtaan /home/rome/publicwsgi/env/ promptistakin näkee tuon tiedostosijainnin mainittaneen.

![add file: upload](V6Kuvat1/v6t1k5.jpg)

Tämän jälkeen ajoin komennon ```source env/bin/activate``` joka aktivoi virtualenvin ja muuttaa promptiin jälleen (env) "prefixin". Tarkistin vielä missä olen komennolla ```which pip``` ja sain halutun tulosteen: ```/home/rome/publicwsgi/env/bin/pip```. Loin microlla tiedoston requirements.txt kuten aikaseimmin ja pääsin jälleen ajamaan komennon jota **EI** saa ajaa sudona tai virtualenvin ulkopuolella turvallisuusuhkien vuoksi. Lopuksi tarkistin kuvastakin löytyvällä komennolla ```django-admin --version``` onnistumiseni, jälleen, kaikki etenee halutusti ja ohjeiden mukaan.

![add file: upload](V6Kuvat1/v6t1k6.jpg)

Projektia en alkanut luomaan koska sellainen löytyi jo ja pääsin tehtävän vaikeimpaan osaan. Aloitin menemällä komennolla ```sudoedit /etc/apache2/sites-available/rtesti.conf``` oikeaan paikkaan ja kopioimalla ohjeistuksen mukaan sisällön tiedostolle. Muutin kopioituun sisältöön oikeat muuttujat ja sijainnit vastaamaan omaa projektiani ja asettamiani nimiä. 

![add file: upload](V6Kuvat1/v6t1k7.jpg)

Seuraavaksi asensin apacheen WSGI moduulin komennolla ```sudo apt-get -y install libapache2-mod-wsgi-py3``` ja tarkistin syntaxin uudelleen komennolla. Sain jälleen vain "AH00558"-virheilmoituksen joten kaikki on oletettavasti hyvin. Käynnistin apachen uudelleen komennolla ```sudo systemctl restart apache2``` ja tarkistin toimiiko kaikki komennolla ```curl -s localhost|grep title``` sain vastaukseksi ```<title>403 Forbidden</title>``` joten jokin ei toimi, aloin tarkistelemaan missä vika voisi olla ja aloin epäilemään ettei wsgi.py tiedostoa olisi. Kävin tarkistamassa apachen error logit varmuudeksi, ja sieltä löytyvä tieto lisäsi epäilystäni wsgi.py tiedoston puutteesta, löysin sieltä seuraavanlaisen promptin: ```[Wed Mar 01 13:48:43.141917 2023] [authz_core:error] [pid 4604:tid 140004804884224] [client ::1:54552] AH01630: client denied by server configuration: /home/rome/publicwsgi/rtesti/rtesti```. 

Koitin tunnilla annetun ohjeen mukaan etsiä tiedoston sijaintia komennolla find | grep mutta en valitettavasti täältäkään sitä löytänyt. Googlailin miten ongelman saisi selvitettyä mutta en valitettavasti löytänyt mistä se voisi johtua. Edellisellä tunnilla olin luonut projektin nimeltä "testi" jonka poistin, en osaa sanoa liittyykö tämä siihe, ymmärtääkseni wsgi.py tiedoston tulisi generoitua itsestään. 

![add file: upload](V6Kuvat1/v6t1k8.jpg)

# Lähteet
- https://terokarvinen.com/2022/deploy-django/
