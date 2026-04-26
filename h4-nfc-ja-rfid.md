# H4 - NFC ja RFID

Mokasin tämän tehtävän kanssa jo ennen, kun aloitin. Kolmatta oppituntia ei ollut pyhän takia ja menin annettujen tehtävien kanssa sekaisin. Luulin, että neljännellä oppitunnilla ei ollut kotitehtäviä ja jätin tämän vahingossa tekemättä. Kun tajusin, mitä oli tapahtunut, päätin priorisoida seuraavaa tehtävää, ettei molemmat ole myöhässä. Töissä on ollut kiireistä tällä viikolla, jonka takia aikaa kouluhommiin oli vähemmän.

Tässä pieni muistutus siitä, mitä RFID on, etten vahingossa keksi jotain omasta päästä:

”RFID-teknologia perustuu radioaaltoihin ja induktioon, jossa lukija lukee tunnisteen sisältämät tiedot tunnisteen tultua lukualueelle.”

Lähde: https://idesco.fi/fi/tietoa-meista/mita-rfid-teknologia-on/

Tehtävänannot katsoin Moodlesta.

## a) RFID-tuotteet

RFID-tuotteita, joita itselläni on käytössä, on ainakin puhelin, maksukortit ja kulkulätkä, jolla pääsen liikkumaan työtilojen sisällä ja niistä ulos. En ole aikaisemmin ollut huolestunut turvallisuudesta näiden suhteen ja en ole vieläkään kohdannut tilanteita, jossa urkintaa olisi ollut. En osaa sanoa suojauksen laadusta, että onko kyse vain onnesta vai hyvin valmistetuista tuotteista, mutta koen olevani suojassa urkinnalta.

## b) APDU-komennon rakenne

APDU-komennoista suora lainaus: ”APDU (Application Protocol Data Unit) is the message format for all communication between a smart card and its host. Defined in ISO 7816-4, APDUs are the lingua franca of smart card programming: whether you are talking to a banking chip, an identity card, or a JavaCard applet, all commands and responses follow the same structure”. 

APDU-komennoilla on neljätavuinen header ja valinnainen body. Headeriin kuuluu CLA, INS, P1, P2, Lc, Data ja Le. Vastaus koostuu valinnaisesta datakentästä ja pakollisesta kahden tavun ”status word”:istä. 

<img width="641" height="315" alt="Näyttökuva 2026-04-26 202807" src="https://github.com/user-attachments/assets/b52b06be-7b5c-4491-9fd5-39ec60c8db7c" />

Lähde: https://smartcardfyi.com/guide/apdu-command-reference/

## c) RFID-hakkerointi uutinen

Valitsin kyseisen artikkelin: https://thehackernews.com/2018/04/hacking-hotel-master-key.html

### Swati Khandelwal 2018. Hackers build a 'Master Key' that unlocks millions of Hotel rooms. The Hacker News.

F-Secure tutkijat Tomi Tuominen ja Timo Hirvonen rakensivat pääavaimen Vision by VingCard digital lock technology:n avulla, jolla pääsee mihin tahansa huoneeseen jälkiä jättämättä. Kyseisessä sähkölukkosysteemissä oli kriittinen alttius, jota hyväksikäyttämällä datatiedot pystyttiin helposti kopioimaan toiselle kortille.

Tutkijat raportoivat löydöistä Assa Abloylle huhtikuussa 2017 ja yhdessä he kehittivät ratkaisun ongelmaan. Assa Abloy julkaisi ohjelmistokorjaukset helmikuussa 2018.
