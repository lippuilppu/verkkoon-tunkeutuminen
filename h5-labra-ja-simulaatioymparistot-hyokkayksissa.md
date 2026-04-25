# H5 - Laboratorio- ja simulaatioympäristöt hyökkäyksissä

En ollut kyseisellä oppitunnilla, johon nämä tehtävät perustuvat, sillä olin sairaana. Tiedän, että siellä annettiin tarvittavat ohjeistukset, mutta koitan silti itse saada ne tehdyksi. Tässä tehtävässä seurasin moodlessa olevia kotitehtäviä.

Aloitin ensimmäiseksi mininetin asennuksesta. Latasin mininetin, importtasin sen VirtualBoxiin ja sain sen käyntiin ongelmitta. 

Mininetin latausohjeet: https://mininet.org/vm-setup-notes/

Itse mininetin lataus: https://github.com/mininet/mininet/releases

Mininetin käyttöohjeita: https://mininet.org/walkthrough/

## a) ARP-hyökäys

    sudo apt install python3-ryu

    ryu-manager ryu.app.simple_switch_13

    sudo mn --topo single,3 --mac --switch ovsk --controller remote

En saanut yhteyttä remote controlleriin, enkä tiennyt miten sen saisi korjattua.

<img width="801" height="48" alt="Näyttökuva 2026-04-26 011157" src="https://github.com/user-attachments/assets/2d2eb6a0-7341-48c9-ae1d-78e2c800fec2" />

<img width="492" height="115" alt="Näyttökuva 2026-04-26 010950" src="https://github.com/user-attachments/assets/a35b9a9a-db6f-4453-9784-18dcec881d18" />

## b) ja c)

Oletin, että jotain meni väärin mininetin asennuksessa jne ja kun yritin keksiä ratkaisua, aika loppui kesken, joten en edennyt tehtävissä eteenpäin. Surkeasti meni tämä tehtävä.
