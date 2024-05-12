# Oma moduli 

Emilia Hauskaviita

12.05.2024

Lisenssi: GNU General Public License v3.0. 

Koneena minulla toimii MacBook Air, jossa on prosessorina Intel Core i3.

Luodaan Saltin avulla tila, joka asentaa kuvanmuokkaukseen käytettäviä paketteja valokuvaajalle ja oman nettisivun tälle. 


### Tietoa tehtävään liittyen

Tero karvisen Palvelinten hallinta kurssi kevät 2024 alkaa olemaan loppu suoralla. Viimeisenä tehtävänä oli tehdä oma moduli. Modulin tarkoituksena oli ratkaista, joku "oikea" ongelma. Minun modulin ajatuksena on luoda Saltilla tila, jolla saan asennettua erilaisia paketteja. Käytän modulin luomiseen herra-orja arkkitehtuuria. Asennan paketit ensin käsin herra koneelle ja sitten saltin avulla orja koneille. Ensimmäiselle orja konellee haluan ladata erilaisia kuvanmuokkaukseen soveltuvia ohjelmia, kuten GIMP, 7Zip, Inkscape. Asennan myös Apachen, jonka avulla luon valokuvaajalle kotisivun. Apachen lisäksi asennan PHP:n, jota käytetään verkkosivujen luomiseen. 

Toiselle orja koneelle lataan yleisiä paketteja, joita haluan että omalta koneeltani löytyy, kun otan sen käyttöön ensimmäistä kertaa. Kyseisiä paketteja ovat, curl, micro, tree, git, openssh-server ja cowsay. Kyseiset paketit lataan myös toiselle orjalle sillä hyödynnän niitä. Näiden pakettien lisäksi lataan molemmille orjille UFW ja muokkaan palomuuriasetuksia, laittamalla portit 22, 80, 4505 ja 4506 auki. Olen modulia tehdessä käyttänyt Tero Karvisen tekemiä eri ohjeita sekä verkosta löytämiäni ohjeita. Hyödynsin modulin teossa myös aikaisemmin tekemiäni harjoituksia, jotka löytyvät GitHubista. 

Harjoituksessa käytin VirtualBoxia, johon latasin Vagrantin avulla kolme virtuaalikoentta, joihin määritin herra-orja arkkitehtuurin. Tero karvisen sivuilla oli valmiiksi tehty Vagrantfile, 
jossa määritettiin orjat ja herra (https://terokarvinen.com/2023/salt-vagrant/?fromSearch=one%20master%20two%20slaves). Lataan ensin käsin paketit master koneelle ja saltin avulla minion koneille.

### Ladattavat paketit
7Zip

GIMP

Inkscape

Apache2

PHP

UFW

Git

Curl

Micro

Tree

Cowsay

Openssh-server 

### Salt Master ja Salt Minion

Aloitin tekemällä omalle koneelleni uuden kansion, johon tein Vagrantfile tiedoston, jonka sisällön kopioin Tero Karvisen ohjeista(https://terokarvinen.com/2023/salt-vagrant/?fromSearch=master%20and%20two%20slaves). Tällä tiedostolla loin Kolem uutta konetta, joille 
oli annettu ip-osoitteet ja ladattu salt-minion ja salt-master. Tiedostossa on myös valmiiksi määritetty minion koneille masterin ip-osoite. Käynnistin koneet ensin komennolla 'vagrant up' 
ja otin yhteyden master koneeseen komennolla 'vagrant ssh tmaster'. Master koneelle päästyäni hyväksyin orja koneiden lähettämät avaimet komennolla 'sudo salt-key -A', jonka jälkeen
testasin koneiden yhteyttä. 

<img width="338" alt="Näyttökuva 2024-5-7 kello 11 14 27" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/55e52327-890a-4ea9-bb27-47ae68997d62">

<img width="328" alt="Näyttökuva 2024-5-7 kello 11 16 45" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/6d82b1ba-eb5e-42db-a242-ca54311cb569">

Koska koneiden välinen yhteys oli kunnossa pääsin aloittaamaan seuraavan vaiheen, joka oli Hello tilan luominen. Tällä varmistan vielä, että kaikki toimii herra ja orja koneiden välillä.


### Hello tila

Loin tmaster koneelle uuden kansion 'sudo mkdir /srv/salt', johon loin uuden kansion 'sudo mkdir hello'. Hello kansion sisään loin init.sls tiedoston. Ajoin salt tilan ensin tmaster koneelle ja sitten t001 ja t002 orja koneille. 
Herra ja orja koneiden tilat onnistuivat. 

<img width="734" alt="Näyttökuva 2024-5-9 kello 15 24 50" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/fd2b479f-f8f0-4d19-a779-9add8aae760b">


<img width="525" alt="Näyttökuva 2024-5-9 kello 15 25 30" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/e84db6a5-771e-4dc1-99ad-846a830744d5">


### Pakettien lataus

Onnistuneen Hello tilan ajamisen jälkeen aloitin perus pakettien asentamisen, joista osaa tulen tarvitsemaan modulin tekemisessä. Loin tähän suoraan apps tilan, jolla sain asennettua halutut paketit. Kyseiset paketit ovat git, curl, micro, tree, cowsay ja openssh-server. Ajoin Salt tilan ensin tmaster koneelle ja sen jälkeen t001 ja t002 koneille eli orja koneille. 

<img width="800" alt="Näyttökuva 2024-5-9 kello 15 59 33" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/634da276-4849-446e-8ef5-854420c99d97">

<img width="598" alt="Näyttökuva 2024-5-9 kello 16 01 00" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/ff020745-d650-447b-bac4-5dfae26ee6bb">

<img width="573" alt="Näyttökuva 2024-5-9 kello 16 01 12" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/b130708a-0351-469f-970e-e9e78344b34f">

<img width="399" alt="Näyttökuva 2024-5-9 kello 16 01 29" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/a6bf15f0-9817-49ab-8006-0143de845ea7">

Kuvissa näkyy, että asennus Saltilla onnistui tmaster koneelle ja molemmille orja koneille t001 ja t002. 

### Git

Kokeilin Git toimivuutta ja cloonasin GitHubin palvelintenhallinta varaston 'tmaster koneelle'. Jotta voin cloonata haluamani varaston koneelle täytyy minun ensin hankkia koneen julkinen avain, jonka vien GitHubiin. Avaimen sain antamalla komennon 'ssh-keygen'. Kopioin julkisen avaimen 'id_rsa.pub' ja vein sen GitHubiin. Tämän jälkeen kopioin GitHubista ssh url:in. Antamalla komennon 'git clone (url)' sain cloonattua palvelintenhallinta varaston.

<img width="644" alt="Näyttökuva 2024-5-12 kello 19 24 43" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/330fa655-f108-43ac-9a8b-964324ee3233">



### Apache2 asennus ja kotisivujen teko

Asennetaan apache2 ensin käsin komennolla ' sudo apt-get install apache2'. Katsoin aikaisemmassa kohdassa asennetun curl avulla, miltä localhost näyttää. 

<img width="772" alt="Näyttökuva 2024-5-9 kello 16 21 31" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/3759df99-90e6-41a7-9439-1e566f7aab80">

Alkuun sallin käyttäjien kotisivut komennolla 'sudo a2enmod userdir' tämän jälkeen oli tärkeä muistaa käynnistää apche uudelleen komennolla 'sudo systemctl restart apache2'. Loin tmaster koneen '/home/vagrant' uuden kansion 'public_html' johon loin index.html tiedoston. Kotisivun pystyin testaamaan komennolla 'curl localhost'. 

<img width="371" alt="Näyttökuva 2024-5-9 kello 17 32 54" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/6a918ae1-55d7-4aaa-a066-7152bd408033">


Nyt vuorossa olisi Apachen asennus Saltilla. Aloitin luomalla kansioon '/srv/salt' uuden kansion 'apache', johon kopioin index.html sivun ja loin 'sudoedit default-index.html' tiedoston. Seuraavaksi loin 'init.html' tiedoston. 'init.sls' tiedostoon kopioin Tero Karvisen sivulta sisällön (https://terokarvinen.com/2018/apache-user-homepages-automatically-salt-package-file-service-example/).Tarkoituksena oli että tila asentaa Apache2, vaihtaa Apachen oletussivun haluamakseni ja saa sivun toimimaan oikein. Tein pienen muutoksen kuitenkin ja lisäsin siihen kohdan, joka lisää public_html kansion ja vie sinne index.html tiedoston.

<img width="392" alt="Näyttökuva 2024-5-9 kello 17 59 32" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/2b2372d2-844c-46b8-8747-7f5785d96dff">

Seuraavaksi testasin ajaa tilan orjalle t001. 

<img width="689" alt="Näyttökuva 2024-5-9 kello 18 03 04" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/7b4afb82-7ed3-442d-bba1-3b1a36a1b964">

<img width="684" alt="Näyttökuva 2024-5-9 kello 18 03 17" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/5ec47ca9-78a7-460f-8f28-14a12cab913f">

Kirjoittamalla orjan ip-osoitteen verkkoon avautui luomani sivu.

<img width="748" alt="Näyttökuva 2024-5-9 kello 17 53 47" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/6e9e67c2-63d1-4db2-802e-907dacbc8565">

Apache2 asennus ja toimivuus on nyt tarkistettu, joten pääsen seuraavaan vaiheeseen, jossa tarkoitukseni on asentaa PHP.


### PHP asennus

Nimesin 'index.html' tiedoston uudelleen komennolla 'mv index.html index.php'. Lisäsin seuraavaksi 'index.php' tiedostoon PHP koodin pätkän ja tarkistin 'curl localhost' komennolla, ettei PHP toimi vielä. 

<img width="363" alt="Näyttökuva 2024-5-9 kello 18 10 51" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/734aa4f2-112c-4ea7-8090-b26545a646b1">

Komennolla 'sudo apt install php libapache2-mod-php' sain ladattua PHP 'tmaster' koneelle. Seuraavaksi menin muokkaamaan 'php7.4.conf' tiedostoa. Tiedoston muokkaamiseen löysin apua rrich360 GitHub sivulta (https://github.com/rrich360/Apache2.4-PHP7-MySQL-phpMyAdmin-manual-configuration).

<img width="478" alt="Näyttökuva 2024-5-9 kello 18 47 17" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/fbb15e3c-8ac9-4fb4-ad6a-89235659bbfc">

Kuva 1: php7.4.conf tiedosto ennen muokkausta.

<img width="491" alt="Näyttökuva 2024-5-9 kello 18 48 09" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/5e2bdeeb-0447-44ed-9cb4-722f8e5a5110">


kuva2: php7.4.conf tiedosto muokkaamisen jälkeen.

Seuraavaksi käynnistin apachen uudelleen ja kokeilin onko sivu muuttunut ja nyt siellä näkyi tekemäni koodin pätkä oikein. 

<img width="759" alt="Näyttökuva 2024-5-9 kello 18 25 19" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/38b40285-5821-44aa-8b39-bec2a05092bd">

Nyt kun php on saatu toimimaan voimme tehdä sen asennuksen Saltilla orja koneelle. Aloitin tekemällä '/srv/salt' kansioon uuden kansion 'php', jonka sisään kopioin 'php7.4.conf' tiedoston ja tein uuden init.sls tiedoston.

<img width="354" alt="Näyttökuva 2024-5-9 kello 19 12 21" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/84fc2c14-325e-4092-aaa7-7182219dc0d1">

Seuraavaksi vielä ajoin tilan orjalle.

<img width="237" alt="Näyttökuva 2024-5-9 kello 19 12 01" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/cc826a0e-054a-4408-b784-307b61214b32">


### Palomuuri asetukset

Tutkin seuraavaksi palomuuriasetuksia ja niiden päälle laittamista. Apuna tässä käytin Tero Karvisen ohjeita (https://terokarvinen.com/2016/instant-firewall-sudo-ufw-enable/?fromSearch=ufw). Aloitin laittamalla palomuurin päälle komennolla 'sudo enable ufw', jonka jälkeen avasin portteja komennolla 'sudo allow ufw 22/tcp'. Porttien avaamisen jälkeen tarkistin, että ne on auki komennolla 'sudo ufw status'. 

<img width="401" alt="Näyttökuva 2024-5-12 kello 14 16 26" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/4a2b25f7-fc63-478d-a936-ad32a6a92302">


Nyt kun olen tarkistanut että halutut portit ovat auki siirryin saltin kimppuun. Aloitin tekemällä uuden kansion 'ufw' kansioon '/srv/salt'. Minun täytyi tuoda 'ufw' kansion sisään tiedostot jotka olivat muokkaantuneet portteja avattaessa. Nämä tiedostot löysin käyttämällä komentoa 'sudo find /etc/ -printf "T%+ %p\n" |sort|tail -10'. Kopioin ensin tiedostot 'user.conf', 'user.rules' ja 'user6.rules' kansioon '/srv/salt/ufw'. Tämän jälkeen tein init.sls tiedoston kansion sisään. Kun yritin ajaa tilaa Saltilla, se ei kuitenkaan toiminut ja aloin selvittämään, mistä tämä voisi johtua ja huomasin että kopioimani tiedostot vaativat sudo oikeuksia, joten minun täytyi kopioida tiedostojen 'uder.rules' ja 'user6.rules' sisältö uusiin tiedostoihin, joihin ei tarvita sudo oikeuksia. Uusien tiedostojen nimeksi laitoin 'user.rulesn' ja 'user6.rulesn'.

<img width="346" alt="Näyttökuva 2024-5-12 kello 14 15 33" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/ec1b5bf3-b3e0-4e58-82e4-897e9f8dce05">

Luotuani uudet tiedostot ja vaihdettuani 'init.sls' tiedostoon uudet nimet tiedostoille Salt tilan ajaminen onnistui molemmille orja koneille.

<img width="521" alt="Näyttökuva 2024-5-9 kello 20 05 33" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/1a524d79-dc18-41cd-8463-4eaecf066b09">



### Kuvanmuokkaus paketit 
Aloitin 7zip paketin asentamisesta ensin käsin 'tmaster' koneelle. Käytin komentoa 'sudo apt-get install p7zip-full'. Seuraavaksi asensin käsin GIMP paketin 'sudo apt-get install gimp'. Viimeisenä asensin vielä Inkscape paketin 'sudo apt-get install inkscape'. Kun kaikki paketit oli asennettu menin kansioon '/srv/salt' ja loin uuden kansion 'photo', jonka sisään tein init.sls tiedoston. 

<img width="350" alt="Näyttökuva 2024-5-12 kello 14 42 13" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/f998db16-406f-4bc4-b7ca-5333cce8bbaa">

Ajoin photo tilan seuraavaksi 'tmaster' koneelle 'sudo salt-call --local state.apply photo'. Koska olin asentanut paketit jo käsin tuli vastaus nopeasti. 

<img width="500" alt="Näyttökuva 2024-5-12 kello 14 43 07" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/91653f69-61ce-477f-b9da-485d1192ff02">

Seuraavaksi ajoin Salt tilan orjalle 't001' komennolla 'sudo salt 't001' state-apply photo'. Minun olisi kannattanut tähän laittaa vielä lisäksi '-l debug', sillä tilan ajamisessa meni melko kauan ja minulle ei tullut mitään ilmoitusta odotus aikana. Tilan ajaminen orjalle kuitenkin onnistui.

<img width="261" alt="Näyttökuva 2024-5-12 kello 14 49 21" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/c618c5b3-f0a5-479b-9e07-4d9e8bc99c49">

### Yhteenveto

Lopuksi tein kansioon '/srv/salt uuden tiedoston 'tp.sls', johon laitoin kaikki luomani tilat, jotta saan ajettua tilat yhdellä komennolla 'sudo salt '*' state.highstate'. Molemmilla orjilla tilojen ajo onnistui.
<img width="302" alt="Näyttökuva 2024-5-12 kello 19 44 45" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/cec4c96b-6b67-4c3d-946a-68de7219c2d7">

<img width="338" alt="Näyttökuva 2024-5-12 kello 19 43 25" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/4a0734ad-0563-4bcd-ad44-6f4132c36a5b">

<img width="245" alt="Näyttökuva 2024-5-12 kello 19 43 05" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/ddeac176-571b-4f1f-9c55-cf66b9655efd">

Nyt 't001' koneella on erilaisia kuvanmuokkaus työkaluja, git versionhallintaa varten ja omat kotisivut. Myös 't002' koneelle on asennettu siihen halutut peruspaketit. Molempiin orjiin on myös päivitetty palomuuri asetuksia. 

## Lähteet
Karvinen, T. Infra as Code - Palvelinten hallinta 2024: https://terokarvinen.com/2024/configuration-management-2024-spring/

Ubuntu, How to install and configure PHP, 2024: https://ubuntu.com/server/docs/how-to-install-and-configure-php

W3Schools, Easy Learning with "PHP Tryit": https://www.w3schools.com/php/

rrich360 Apache2.4-PHP7-MySQL-and-phpMyAdmin-Configuration, 2019: https://github.com/rrich360/Apache2.4-PHP7-MySQL-phpMyAdmin-manual-configuration

Karvinen, T. Instant Firewall – sudo ufw enable, 2016: https://terokarvinen.com/2016/instant-firewall-sudo-ufw-enable/?fromSearch=ufw

Karvinen, T. Salt Vagrant - automatically provision one master and two slaves, 2023: https://terokarvinen.com/2023/salt-vagrant/?fromSearch=master%20and%20two%20slaves

Karvinen, T. Apache User Homepages Automatically – Salt Package-File-Service Example, 2018: https://terokarvinen.com/2018/apache-user-homepages-automatically-salt-package-file-service-example/

Ashley, How can I Install 7Zip in Ubuntu, Debian, Centos & Fedora, OPERAVPS, 2023: https://operavps.com/docs/install-7zip-in-linux/#:~:text=Install%207Zip%20in%20Linux%20Using%20Command%20Line,-First%2C%20let's%20see&text=So%2C%20you%20need%20to%20open,7zip%20package%20on%20your%20system.&text=P7zip%20and%20p7zip%2Dplugins%20are,Red%20Hat%2Dbased%20Linux%20distributions.

