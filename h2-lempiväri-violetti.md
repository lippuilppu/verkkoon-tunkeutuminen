  # H2 - Lempiväri violetti

Tehtävänanto: https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/#h2-lempivari-violetti

## x) Tiivistelmät

### Pyramid of Pain

Lähde: https://detect-respond.blogspot.com/2013/03/the-pyramid-of-pain.html

Tuskan pyramidi näyttää suhteet indikaattorien välillä, joiden avulla voidaan havaita vastustajan toimintaa ja paljon ”kipua” indikaattorien kieltäminen aiheuttaa heille. Ne on jaettu seitsemään ryhmään, joista kaksi on kaaviossa samassa kategoriassa. 

### Diamond Model

Lähde: https://www.threatintel.academy/wp-content/uploads/2020/07/diamond-model.pdf

Timanttimalli havainnollistaa tunkeutumisen pääpiirteet ja niiden väliset suhteet. Sen avulla voidaan kehittää ja löytää uutta tietoa pahanaikeisesta toiminnasta.

## a) Apache log

Päivitin virtuaalikoneen ja asensin apache2:n. Se ei ole kovin tuttu, joten ohjeiden mukaisesti avasin virtuaalikoneen oletussivun http://localhost ja apache2 näytti toimivan kuin piti. 

    sudo apt-get update

    sudo apt-get install apache2

    sudo systemctl start apache2

Apachen lokeja en melkein saanut näkyviin, mutta localhost-sivulla vierailemisen jälkeen tajusin, että unohdin sudon komennosta.

    sudo tail -f /var/log/apache2/access.log

Esimerkki lokirivi: 127.0.0.1 - - [03/Apr/2026:17:54:45 +0300] ”GET / http/1.1” 200 3383 ”-” ”Mozilla/5.0 (X11; Linux x86:64; rv:140.0) Gecko/20100101 Firefox/140.0”

<img width="1110" height="171" alt="Näyttökuva 2026-04-03 175849" src="https://github.com/user-attachments/assets/b3457ce9-6711-4ae2-819c-ae9a40763483" />

127.0.0.1 = Palvelimen IP-osoite, joka teki pyynnön serverille.

[03/Apr/2026:17:54:45 +0300] = Pyynnön pvm.

”GET / http/1.1” = Tehty pyyntö, jonka serveri sai.

200 = Status koodi, joka lähetetään takaisin palvelimelle.

3383 = Palautetun määrä.

”-” = - viittaa tietoon, jota ei ole saatavilla.

”Mozilla/5.0 (X11; Linux x86:64; rv:140.0) Gecko/20100101 Firefox/140.0” = "The User-Agent HTTP request header", itsensä määrittelevä tieto, jonka serveri antaa.

## b) Nmapped

Katkaisin yhteyden ja kokeilin molempia annettuja komentoja.

    sudo nmap -A localhost

    sudo nmap -T4 -vv -A -p 80 localhost

<img width="1148" height="493" alt="Näyttökuva 2026-04-11 094937" src="https://github.com/user-attachments/assets/5e09de7e-9b39-4ff4-a4ef-f9eb5a7e2d67" />

ja

<img width="1149" height="153" alt="Näyttökuva 2026-04-11 095043" src="https://github.com/user-attachments/assets/3e7faa06-47f4-4d1c-ba06-269a033d3eb2" />

Porttiskannaus antoi tiedot esimerkiksi nmap-versiosta, tehdyn pyynnön ajan, avoimet portit ja niiden tiedot, koneen ja käyttöjärjestelmän tiedot sekä kuinka monta IP-osoitetta skannattiin ja kauan skannaus kesti.

## c) Skriptit

Skannauksen aikana päällä olevat skriptit olivat:

http-server-header

http-title

http-server-header

http-title

## d) Jäljet lokissa

Päätin ensimmäiseksi kokeilla apache log-komentoa, jota käytettiin aikaisemmassa tehtävässä.

    sudo tail -F 7var/log/apache2/access.log

<img width="890" height="382" alt="Näyttökuva 2026-04-11 221450" src="https://github.com/user-attachments/assets/1d1a04fc-071c-43fd-bcb6-a2fee946490b" />

Lokeissa näkyy esim. IP-osoite, päiväys, pyyntö sekä se tieto, että Nmap Scripting Engine-skriptiä on käytetty.

Hakua voi rajata helposti grep-komennollaa, jos haluaa nähdä hakuja, joissa näkyy vain tietyt tiedot.

    Grep -ir

## e) Wire sharking

Kun yritin avata wiresharkia, sain tämänlaisen ilmoituksen:

<img width="800" height="76" alt="Näyttökuva 2026-04-11 234129" src="https://github.com/user-attachments/assets/39bc1dcb-e040-43fc-89c9-6be08ff127ed" />

Googlaamalla löysin vastauksen ongelmaan: https://askubuntu.com/questions/748941/im-not-able-to-use-wireshark-couldnt-run-usr-bin-dumpcap-in-child-process

<img width="767" height="491" alt="Näyttökuva 2026-04-11 234359" src="https://github.com/user-attachments/assets/12b186f2-24d2-4455-9048-b8372060d1a8" />

Tämä ei kuitenkaan korjannut ongelmaa ja itse wireshark antoi ratkaisun:

<img width="801" height="300" alt="Näyttökuva 2026-04-11 234921" src="https://github.com/user-attachments/assets/a3bf6fbc-b582-49ec-8b44-2cf43cb265e2" />

    sudo dpkg-reconfigure wireshark-common

    sudo usermod -a -G wireshark ilona

Sain tämän jälkeen wiresharkin auki ja toimimaan.

Sieppasin verkkoliikennettä samalla, kun tein porttiskannauksen. Myönnän, että tässä meni hetki, kun en tajunnut heti, että terminaaliin saa useamman välilehden kerralla auki.

    sudo nmap -A localhost

<img width="973" height="264" alt="Näyttökuva 2026-04-12 002218" src="https://github.com/user-attachments/assets/5c446e26-5137-44ff-92a9-84588566c9b2" />

Zip-tiedostossa pcap-tallennus:
[nmap.zip](https://github.com/user-attachments/files/26648835/nmap.zip)

## f) Net grep

Asensin ngrepin.

    sudo apt-get install ngrep

Ja testasin toimiiko se.

<img width="799" height="107" alt="Näyttökuva 2026-04-12 001742" src="https://github.com/user-attachments/assets/7743dcdb-27d7-411a-87f2-f5b94dce02f0" />

Tämän jälkeen syötin vihjeissä annetun komennon.

    sudo ngrep -d lo -i nmap

  <img width="801" height="397" alt="Näyttökuva 2026-04-12 003325" src="https://github.com/user-attachments/assets/40e986d0-09e2-4672-980d-26ca37d95cf8" />

## g) Agentti

Tässä en osannut korjata komentoa siten, että saisin user.agentin vaihdettua.

    nmap --script-args http.useragent="BSD experimental on XBox350 alpha (emulated on Nokia 3110)"

<img width="800" height="113" alt="Näyttökuva 2026-04-12 014422" src="https://github.com/user-attachments/assets/4bda3292-6271-41fd-897b-acbd67c374bc" />

## h) Pienemmät

<img width="798" height="404" alt="Näyttökuva 2026-04-12 004801" src="https://github.com/user-attachments/assets/ec7ef011-f9e4-4c8f-a8cf-7b3219be0c46" />

<img width="800" height="382" alt="Näyttökuva 2026-04-12 004910" src="https://github.com/user-attachments/assets/e5c81abd-d3f0-4ef4-b72e-20b59d57130e" />

## i) LoWeR ChEcK

    sudo ngrep -d lo -i

<img width="798" height="402" alt="Näyttökuva 2026-04-12 013243" src="https://github.com/user-attachments/assets/0d55eaea-c480-4b16-bec0-2a8dcd5304ce" />

<img width="798" height="57" alt="Näyttökuva 2026-04-12 014131" src="https://github.com/user-attachments/assets/b20945a5-5b96-48e8-87dc-8f706f005339" />

## j) FCC ID

Hain googlen kautta oman puhelimen ICCID:n ja vastaan tuli tämä sivu: https://fccid.io/

<img width="1154" height="439" alt="Näyttökuva 2026-04-12 014005" src="https://github.com/user-attachments/assets/93c945e8-b47b-48c5-a6c4-d292e9d8d6ba" />

## Lähteet

https://httpd.apache.org/docs/2.4/logs.html

https://www.geeksforgeeks.org/linux-unix/ngrep-network-packet-analyzer-for-linux/
