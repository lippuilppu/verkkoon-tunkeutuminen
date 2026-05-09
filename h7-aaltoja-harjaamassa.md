  # H7 – Aaltoja harjaamassa

Tehtävänanto: https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/#tehtavanannot

## x) Tiivistelmät

### Universal Radio Hacker SDR Tutorial on 433 MHz radio plugs

Lähde: https://www.youtube.com/watch?v=sbqMqb6FVMY&t=199s

- Ohjeet Universal Radio Hackerin käyttöön.

- Läpikäydyt asiat: taajuuden tarkistus, lähetyksen äänitys ja tallentaminen sekä tulkinta, asetukset esim.modulaatio ja parametrit sekä yksittäisten pakettien tulkinta.

### Decode 433.92 MHz weather station data

Lähde: https://www.onetransistor.eu/2022/01/decode-433mhz-ask-signal.html

- Ohje siitä, miten käyttää RTL-SDR:rää ja URH:ta analysoimaan ja tulkitsemaan RF-signaaleja sääasemalta.

- rtl_433 ja urh ovat työkaluja, joilla voidaan analysoida signaaleja.

## a) Lähteet ja läppä

Tehty.

## b) rtl_433

Asensin rtl_433:n virtuaalikoneelle seuraavalla komennolla:

    sudo apt install rtl-433    

<img width="798" height="397" alt="Näyttökuva 2026-05-09 230006" src="https://github.com/user-attachments/assets/9590a1e8-7474-41f0-9c65-0809e0f04582" />


Tarkistin, että oli oikea versio.

    rtl_433

<img width="798" height="78" alt="Näyttökuva 2026-05-09 230052" src="https://github.com/user-attachments/assets/e2a8224f-0751-42f4-970e-d5b45545de09" />


## c) Automaattinen analyysi.

Asensin wget-komennon.

    Sudo apt install wget

Latasin wget-komennon avulla analysoitavan tiedoston.

    Wget https://terokarvinen.com/2025/verkkoon-tunkeutuminen-ja-tiedustelu--ici013as3a-3001--2025p4/samples/Converted_433.92M_2000k.cs8

<img width="798" height="298" alt="Näyttökuva 2026-05-09 231219" src="https://github.com/user-attachments/assets/d86fd2f0-e66b-4e11-b6ec-378b06f681d2" />


Avasin tiedoston rt_433-komennon avulla.

    rtl_433 -r Converted_433.92M_2000k.cs8

<img width="801" height="264" alt="Näyttökuva 2026-05-09 231331" src="https://github.com/user-attachments/assets/7e545680-74f7-4029-ae99-060c8a36d0f1" />


- KlikAanKlikUit-kytkin lähettää signaaleja ja nexa-Security ja Proove-Security vastaavat.
- Ainoa id joka näkyy on 8785315.

## d) Too compex 16?

Latasin näytteen wget komennolla.

    wget https://terokarvinen.com/2025/verkkoon-tunkeutuminen-ja-tiedustelu--ici013as3a-3001--2025p4/samples/Recorded-HackRF-20250411_183354-433_92MHz-2MSps-2MHz.complex16s

Vinkeissä sanotaan, että tiedoston saa muunnettua yhteensopivaan muotoon muuttamalla tiedoston nimi.

Piti katsoa, mikä olisi helpoin tapa vaihtaa nimi ja käytin mv-komentoa tähän.

Lähde: https://askubuntu.com/questions/280768/how-to-rename-a-file-in-terminal

    mv Recorded-HackRF-20250411_183354-433_92MHz-2MSps-2MHz.complex16s Recorded_433.92M_1000k.cs8

Tein tämän kahdesti kirjoitusvirheen takia. Sitten avasin näytteen.

    rtl_433 -r Recorded_433.92M_1000k.cs8

En saanut analyysiä näkyviin ja luin läpikävelyä, jospa sieltä löytyisi jonkinlaista vinkkiä. Kävi ilmi, että nimesin näytteen taajuuden väärin. Korjasin tämän ja sain näytteen auki. Kyseessä oli sama näyte kuin aikaisemmassa tehtävässä. Analyysi löytyy osasta c.

<img width="968" height="136" alt="Näyttökuva 2026-05-09 235632" src="https://github.com/user-attachments/assets/4c71c299-ba44-4100-a8d2-8c3d5ef666ae" />

<img width="1005" height="584" alt="Näyttökuva 2026-05-10 000406" src="https://github.com/user-attachments/assets/4e78569e-ef7d-42e2-924e-c47c20d014d0" />


## e) Ultimate

Asensin URH:n seuraavilla komennoilla.

    sudo apt-get -y install pipx

    pipx install urh

    pipx ensurepath

<img width="968" height="379" alt="Näyttökuva 2026-05-09 233836" src="https://github.com/user-attachments/assets/2cd5349e-f59f-4495-be3c-41293d5a836a" />

Aika loppui kesken, niin jätin tehtävät tähän.
