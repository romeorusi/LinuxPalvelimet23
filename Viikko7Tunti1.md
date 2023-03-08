# H13

### Sisällysluettelo
- [Aloitustilanne](#Aloitustilanne) 
- [Hello world](#hello-world)
- [Lähteet](#lähteet)

WSGI puuttuu

# Aloitustilanne

- Aloitetaan 16:20 8/3/2023

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
![add file: upload](V7Kuvat2/v7t1k1.jpg) 

# Hello world

Saimme tehtäväksi kääntää "hello world" ohjelman kolmella vapaavalintaisella kielellä. Valitsin Bashin, Pythonin ja Javan.

Asensin kielet komennoilla

    sudo apt-get install bash

    sudo apt-get install python3

    sudo apt-get install default-jdk
    
### Bash
    
Ensin loin bash ohjelman

    micro HelloBash.sh
    
Kirjoitin sisään ```echo "Hello World"```

![add file: upload](V7Kuvat2/v7t1k1.jpg) 


### Python

Loin tiedoston microlla ja kirjoitin sisään ohjeiden mukaan ```print("Hello world")```

    micro HelloWorld.py

Ajoin tiedoston 

    python3 HelloWorld.py

![add file: upload](V7Kuvat2/v7t1k2.jpg)


### Java

Aloitin luomalla tiedoston

    micro HelloWorld.java

Kirjoitin tiedostoon seuraavan ohjeiden mukaan:

    public class HelloWorld
    {
     public static void main(String[] args)
     {
     System.out.println("Hello World!");
     }
    }

Tämän jälkeen tiedosto piti compilaa, tein sen komennolla ```javac HelloWorld.java``` jonka jälkeen yritin ajaa ohjelmaa ```java HelloWorld.java``` sain tässä kuitenkin
errorin, sillä javac luo tiedoston ilman .java päätettä, joka on ajettava. Ajoin tämän jälkeen ```java HelloWorld``` 

![add file: upload](V7Kuvat2/v7t1k3.jpg)

Valmista 16:26

# Lähteet
- https://terokarvinen.com/2018/hello-python3-bash-c-c-go-lua-ruby-java-programming-languages-on-ubuntu-18-04/
- https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/
