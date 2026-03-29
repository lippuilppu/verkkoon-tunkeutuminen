# H1 - Sniff

## x) Tiivistelmät

### Wireshark-Getting Started

Tero Karvisen artikkeli, johon tämä tiivistelmä perustuu: https://terokarvinen.com/wireshark-getting-started/

Wiresharkin avulla pystyy tallentamaan ja analysoimaan tietoliikennettä pakettien avulla. Artikkelissa ohjeistetaan sen käyttöä virtuaalikoneessa.

Kaapattuja paketteja voi tallentaa ja ladata. Statistics Menussa näkyy kaappauksen yleiskatsaus. Filttereiden avulla kappauksien tallennettuja tietoja voi suodattaa.

### Network Interface Names on Linux

Tero Karvisen artikkeli, johon tämä tiivistelmä perustuu: https://terokarvinen.com/network-interface-linux/ 

Network Interface on kuin verkkokortti, mutta ei välttämättä fyysinen kortti.

Nimen alku viittaa kortin tyyppiin, esim. wl tarkoittaa WLAN:ia. Esimerkki wl-tyyppisestä verkkokortista on wlp4s0.

## a) Debianin asennus.

Virtualboxin asennus onnistui ongelmitta. Debianin asennus alkoi hyvin, mutta se ei millään antanut kirjautua sisään käyttäjällä ja salasanalla, jotka valitsin konfiguroinnin aikana.

Kokeilin uudellen tehdä virtuaalikoneen, se ei auttanut. Kokeilin uudelleen asentaa Debianin, jospa salasana oli oikeasti väärin, ei onnistunut. Kokeilin Googlen kautta löytää ratkaisua. Siellä ehdotettiin vboxuser, changeme, debian jne. Nämä eivät auttaneet.


## b) Ei voi kalastaa

Tätä en tehnyt.


## c) Wireshark

Asensin wiresharkin virtuaalikoneen sijaan omalle läppärille ja tein tehtävät siinä.

Liitteenä zip-kansio, jossa on tiedostoon tallennettu siepattu liikenne.

[ilonas-example.zip](https://github.com/user-attachments/files/26326790/ilonas-example.zip)


## d) Oikeesti TCI/IP

TCP/IP-mallissa on neljä kerrosta, jotka ovat sovelluskerros (Application layer), kuljetuskerros (Transport layer), verkkokerros (Internet layer) ja peruskerros (Link layer).

Sovellus: NetBIOS Datagram Service

Kuljetus: User Datagram Protocol (UDP)

Verkko: Internet Protocol Version 4 (IPv4) 

Perus: Null/Loopback

Kuvakaappaus siepatusta liikenteestä, jonka tallensin edellisessä tehtävässä.

<img width="1263" height="604" alt="ilona-example" src="https://github.com/user-attachments/assets/9ea15500-837f-4551-916b-3e200807c7fc" />


## e) Mitäs tuli surffattua?

Ensimmäiseksi katsoin kuinka iso ja pitkä kaappaus oli vertaamalla ensimmäistä ja viimeistä framea. Frameja oli yhteensä 283 kaappaus kesti noin 7 sekuntia.

<img width="634" height="171" alt="frame" src="https://github.com/user-attachments/assets/a4e54878-5a1a-49ae-9104-61c981590a3e" />


<img width="624" height="173" alt="framet" src="https://github.com/user-attachments/assets/1343b784-d759-407e-997f-d43e87730738" />


Tätä tehdessä huomasin, että joissan kohdissa luki osoitteet google.com ja terokarvinen.com.


## g) Minkä merkkinen verkkokortti käyttäjällä on?

En löytänyt verkkokortin nimeä framesta.


## h) Millä weppipalvelimella käyttäjä on surffaillut?

Sain komennolla dns.qry.name esiin palvelinten nimet joihin kuuluu esimerkiksi terokarinen.com, google.com ja goatcounter.com.


## i) Analyysi

Hyppäsin randomisti sivulta sivulle ja siirryin Wiresharkiin, josta sain tämänlaisen sieppauksen.

<img width="1260" height="535" alt="esimerkki" src="https://github.com/user-attachments/assets/e8b88aff-2ceb-41e6-9d19-c640e455e3bf" />

Ensimmäiseksi huomaan verkkokortin, jonka löysin tällä kertaa heti: ZyxelCommuni. Toiseksi huomasin HomePlug Av Protokollan, jota en ole nähnyt aikaisemmin. Se on Power-line communication, eli datasiirtoon liittyvä protokolla.

Frameja oli yhteensä 21 ja sieppaus kesti noin 9 sekuntia.
