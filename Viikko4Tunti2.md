### Sisällysluettelo
- [Aloitustilanne](#Aloitustilanne) 
- [Domainnimi](#Domainnimi)
- [Lähteet](#lähteet)

![add file: upload](V4Kuvat2/v4t2k1.jpg)


# Aloitustilanne

- Aloitetaan 13:05 12/2/2023

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


# Domainnimi

Tämän viikon tehtävänä oli vuokrata domainnimi ja asettaa se tietylle sivulle. Aloitin menemällä namecheap.comiin ja luomalla käyttäjän. Käyttäjän luonnin jälkeen kirjoitin 
"domain search" hakukenttään haluamani domainin. Päädyin tunnillakin esitettyyn esimerkkiin "romeorusi.com". Hintaa hankkinnalle ei paljoa tullut, kun miettii että 
kyseessä on tosiaan vuosittainen menoerä.

![add file: upload](V4Kuvat2/v4t2k1.jpg)

Mentyäni ostoprosessissa eteenpäin niin, että osto onnistui, navigoin namecheap.comissa käyttäjän dashboardiin ja siellä "advanced dns" sivulle. Sivulla lisäsin kaksi
"A-record" tyyppistä yhteyttä ja ohjasin molemmat oman palvelimen IP-osoitteeseen. Toisen "host" kohtaan kirjoitin @, ja toiseen www. Tämä tarkoittaa, että romeorusi.com
sekä www.romeorusi.com vievät molemmat sivulle tuolla IP-osoitteella


![add file: upload](V4Kuvat2/v4t2k2.jpg)

Äsken kuvaillun osan jälkeen tarkistin välittömästi romeorusi.com sivua, joka ei vielä toiminut. Otin lasin vettä ja sen jälkeen sivu toimi suoraan. Kaikki ei kuitenkaan
ollut vielä valmista. Huomasin, että vain www.romeorusi.com toimii, romeorusi.com ei palauttanut mitään.

www.romeorusi.com

![add file: upload](V4Kuvat2/v4t2k3.jpg)

romeorusi.com 

![add file: upload](V4Kuvat2/v4t2k4.jpg)

Kokeilin myös chromella, mutta valitettavasti tulos on sama. Curlasin sivun linuxilla ja sain palautteeksi (ilman www prefixia) sivun oikean koodin. Sivu ei kuitenkaan
toiminut millään selaimella. Googlasin mistä asia voisi riippua ja sain vastaukseksi, että muutokset voivat viedä hetken aikaa.

![add file: upload](V4Kuvat2/v4t2k5.jpg)

Pidin noin ~10 minuutin tauon enkä tehnyt kirjaimellisesti mitään tuohon aikaan, ja sivu alkoi itsestään toimimaan. 

![add file: upload](V4Kuvat2/v4t2k6.jpg)

Oletettavaa siis on, että jokin osa prosessista saattaa kestää pidempää. Lopputulos on kuitenkin se, että www.romeorusi.com sekä romeorusi.com toimivat. Kaikki viimein
ok.


Seuraavaksi tutkin host ja dig komentoja. En ollut varma mitä host tekee, joten aloitin kirjoittamalla 




# Lähteet
- https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/#h8-say-my-name
