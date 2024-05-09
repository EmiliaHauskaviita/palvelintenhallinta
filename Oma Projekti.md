# Oma moduli 

Emilia Hauskaviita

Käyttämäni lisenssi on GNU General Public License. 

Koneena minulla toimii MacBook Air, jossa on prosessorina Intel Core i3.


### Tietoa tehtävään liittyen

Tero karvisen Palvelinten hallinta kurssi kevät 2024 alkaa olemaan loppu suoralla. Viimeisenä tehtävänä oli tehdä oma moduli. Modulin tarkoituksena oli ratkaista joku "oikea" ongelma. 
Minun modulin tarkoitus oli käyttää yhtä master konetta ja kahta sen orja konetta joille lataan erilaisia paketteja. Toiselle orja koneelle lataan paketteja joita aloitteleva graafinen suunnittelija tarvitsee uudelle koneelleen ottaessaan sen käyttöön.
Toiselle koneelle taas lataan yleisiä paketteja, joita käyttäjä tarvitsee koneellaan ottaessaan sen käyttöö. Kuten UFW, micro, tree  ja ssh.
Olen modulia tehdessä käyttänyt Tero Karvisen tekemiä eri ohjeita. Hyödynsin modulin teossa myös aikaisemmin tekemiäni harjoituksia, jotka löytyvät GitHubista. 

Harjoituksessa käytin VirtualBoxia, johon latasin Vagrantin avulla kolme virtuaalikoentta, joihin määritin herra-orja arkkitehtuurin. Tero karvisen sivuilla oli valmiiksi tehty Vagrantfile, 
jossa määritettiin orjat ja herra (https://terokarvinen.com/2023/salt-vagrant/?fromSearch=one%20master%20two%20slaves). Lataan ensin käsin paketit master koneelle ja saltin avulla minion koneille.

### Ladattavat paketit
7Zip

GIMP

Git

Curl

Näiden pakettien lisäksi latasin myös apache2 ja PHP, jolla loin kotisivun käyttäjälle. 

### Salt Master ja Salt Minion

Aloitin tekemällä omalle koneelleni uuden kansion, johon tein Vagrantfile tiedoston, jonka sisällön kopioin Tero Karvisen ohjeista. Tällä tiedostolla loin Kolem uutta konetta, joille 
oli annettu ip-osoitteet ja ladattu salt-minion ja salt-master. Tiedostossa on myös valmiiksi määritetty minion koneille masterin ip-osoite. Käynnistin koneet ensin komennolla 'vagrant up' 
ja otin yhteyden master koneeseen komennolla 'vagrant ssh tmaster'. Master koneelle päästyäni hyväksyin orja koneiden lähettämät avaimet komennolla 'sudo salt-key -A', jonka jälkeen
testasin koneiden yhteyttä. 

<img width="338" alt="Näyttökuva 2024-5-7 kello 11 14 27" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/55e52327-890a-4ea9-bb27-47ae68997d62">

<img width="328" alt="Näyttökuva 2024-5-7 kello 11 16 45" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/6d82b1ba-eb5e-42db-a242-ca54311cb569">

Koska koneiden välinen yhteys oli kunnossa pääsin aloittaamaan seuraavan vaiheen, joka oli Hello tilan luominen. Tällä varmistan vielä että kaikki toimii herra ja orja koneiden välillä.


### Hello tila

Loin tmaster koneelle uuden kansion 'srv/salt', johon loin uuden kansion 'mkdir hello'. Hello kansion sisään loin init.sls tiedoston. Ajoin salt tilan ensin tmaster koneelle ja sitten t001 ja t002 orja koneille. 
Herra ja orja koneiden tilat onnistuivat. 

<img width="712" alt="Näyttökuva 2024-4-30 kello 13 08 00" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/fcce6527-8b9b-4758-9f71-f25a3bd34c5b">

Kuva: orjien tiloista.

### Pakettien lataus

Onnistuneen Hello tilan luomisen jälkeen aloitin perus pakettien asentamisen. Loin tähän suoraan apps tilan jolla sain asennettua halutut paketit. 

### Apache2 asennus ja kotisivujen teko


### PHP asennus

### Palomuuri asetukset




## Lähteet
https://terokarvinen.com/2024/configuration-management-2024-spring/
