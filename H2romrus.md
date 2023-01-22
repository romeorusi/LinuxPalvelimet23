### H2 tehtävä

# Aloitustilanne
- Virtualisoitu VirtualBox 7.0.4
- Käyttöjärjestelmänä Debian GNU/Linux 11 (bullseye) x86-64 arkkitehtuuri 
- Tietokoneessa OS Win 10 pro 
- Aloitetaan 18:55 22/01/2023

# Tiivistelmä  
Ensimmäinen tehtävä on tiivistää https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited sivun sisältö muutamalla
ranskalaisella viivalla.

- Komentoriviä on käytetty jo ennen internetiä ja se on olennainen sekä käytännöllinen osa linuxin käyttöä
- Yleisesti ottaen komentoja ajettaessa varoituksia ei tule, mikäli mitään ei "näy" tapahtuvan, komento on todennäköisesti ajettu onnistuneesti.
- Lähtökohtaisesti kaikki komennot ajetaan vähimmillä oikeuksilla, kirjoitettaessa "sudo" komennon eteen ajetaan komento täysillä oikeuksilla.
- Ohjelmat asennetaan komentoriviä käyttäen valmiina paketteina, toisin kuin esim windowsissa.
- Muuta tietoa ja komentoja voi tarvittaessa tarkastella aikaisemmasta linkistä tai etsimällä netistä.


# H2

19:30 Aloitin asentamalla micro:n kirjoittamalla "sudo apt-get install micro" ja kirjoittamalla "y" pyydettäessä. Annoin asennuksen hoitaa itsensä loppuun ja kirjoitin komentoriville "micro", varmistin näin että asennus on onnistunut ja ohjelma toimii. 

19:33 Koitin listata koneen raudan komennolla "sudo lshw -short -sanitize", tämä ei toiminut sillä lshw ei ollut asennettuna, asensin sen komennolla "sudo apt-get install lshw"
