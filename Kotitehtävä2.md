# Kotitehtävä 2
## Soitto kotiin

x) Lue ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. 
Tiivistämiseen riittää muutama ranskalainen viiva. Kannattaa lisätä mukaan myös jokin oma havainto, idea tai kysymys.)
Karvinen 2021: Two Machine Virtual Network With Debian 11 Bullseye and Vagrant
- vagrant tulee olla ladattuna.
- tehdään uusi hakemisto ja sinne tiedosto johon laitetaan ohjeissa ollut scripti, joka luo meille kaksi uutta virtuaalikonetta t001 ja t002.
- vagrant up
- vagrant ssh t001
Karvinen 2018: Salt Quickstart – Salt Stack Master and Slave on Ubuntu Linux
- Yhteys masteriin mistä tahansa esim. palomuurin takaa.
- Yksi master ja minioneita voi olla paljon.
- minion täytyy tietää masterin ip osoite jotta se voi ottaa yhteyden.
- minionille voi antaa nimen (id), mutta se ei ole pakollista. Jos monta minionia niin helpompi olla nimeämättä kaikkia erikseen.
Karvinen 2014: Hello Salt Infra-as-Code
-Luodaan uusi tila joka vahvistaa tekemämme tekstitiedoston olemassa olon.
-luodaan uusi kansio srv/salt/hello, srv/salt on kansio, joka on kaikilla orjilla käytettävissä.
-Kirjoitetaan koodina komentoja eli tässä tehtävässä, kun annetaan komento hello orja luo uuden tiedoston tmp/helloemilia


a) Asenna kaksi virtuaalikonetta samaan verkkoon. Osoita, että pystyt käyttämään kumpaakin konetta (esim 'vagrant ssh t001'). 
Osoita, että koneet voivat pingata toisiaan. (Tämä tehtävä on helpointa tehdä Vagrantilla)

<img width="687" alt="Näyttökuva 2024-4-6 kello 10 35 47" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/4322b755-5e8e-42e3-889c-0d25c39f46d7">

Yllä olevassa kuvassa näkyy kuinka olen luonut uuden hakemiston twohost. Hakemiston sisällä loin VagrantFile tiedoston nanolla. Teksti tiedostoon lisäsin tehtävän annosta
löytyneen scriptin, jolla luotiin kaksi uutta virtuaalikonetta. Tämän jälkeen käytin vagrant up komentoa, jonka jälkeen avasin t001 virtuaalikoneen komennolla vagrant ssh t001. 
Kokeilin t001 koneella pingata t002 koneen ja sen onnistunut tulos näkyy alla olevassa kuvassa.

<img width="465" alt="Näyttökuva 2024-4-2 kello 11 08 18" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/ce197bb8-2a52-4fc1-8c39-04b68f186871">

Pääsin exit komennolla pois t001 koneelta ja käynnistin t002 koneen komennolla vagrant ssh t002. Kokeilin myös t002 koneella pingata t001 koneen, tämä näkyy alla olevassa kuvassa.

<img width="503" alt="Näyttökuva 2024-4-7 kello 19 54 28" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/affdc142-2fd6-4949-b88c-f703584abdc6">


b) Asenna Saltin herra-orja arkkitehtuuri toimimaan verkon yli. (Verkko voi olla virtuaalinen verkko paikallisten virtuaalikoneiden välillä, kuten muissakin alakohdissa)
Latasin t001 koneelle salt-masterin ja t002 koneelle salt-minionin eli t001 kone toimii herrana ja t002 kone toimii orjana. Tällä tarkoitetaan siis sitä että voin t001 koneella 
hallita t002 konetta ja antaa sille erilaisia komentoja. Aloitin tehtävän ensin päivittämällä koneen t002 eli sudo apt-get update, tämän jälkeen latasin salt-minionin eli 
sudo apt-get -y install salt-minion. Alla olevassa kuvassa on otettu kuvankaappaukset päivittämisestä ja lataamisesta t002 koneelle.

<img width="850" alt="Näyttökuva 2024-4-2 kello 11 14 31" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/35c358d0-5cf5-473e-8310-161cf019b3a6">

<img width="580" alt="Näyttökuva 2024-4-2 kello 11 13 45" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/d847319d-29e5-4d1b-84d0-bb47d07ba4e0">

Sama päivittäminen sudo apt-get update tehtiin myös t001 koneelle ja salt-minionin sijasta latasin t001 koneelle salt-masterin komennolla sudo apt-get -y install salt-master.
Kun koneille oli ladattu salt-master ja salt-minion menin t002 koneella sudoedit etc/salt/minion ja kirjoitin sinne master koneen ip-osoitteen eli t001 koneen. t001 koneen ip osoitteen sain,
kun käytin t001 koneella ollessa komentoa ip a. sudoedit etc/salt/minion, master koneen ip-osoitteen lisäksi laitoin t002 eli orja koneen id emilia. ID ei ollut pakollinen laittaa ja sitä 
ei edes kannata laittaa, jos orja koneita on useampi, koska niillä kuuluu kaikilla olla eri id. Jos id kohtaan ei olisi laittanut mitään olisi kone itse antanut sille nimen. 
Tämän vaiheen jälkeen minun piti restart t002 kone komennolla sudo systemctl restart salt-minion, jonka jälkeen exit komennolla pääsin pois koneelta. 

<img width="571" alt="Näyttökuva 2024-4-2 kello 11 10 35" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/3a5f7e54-77a9-44e4-9cbc-81e71867853d">

<img width="855" alt="Näyttökuva 2024-4-2 kello 11 11 39" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/d0674c63-a18e-4ceb-bd34-36561533b6fc">

<img width="450" alt="Näyttökuva 2024-4-2 kello 11 19 26" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/b6d4380e-b55e-45d2-afb7-9f23fab1bec5">

<img width="694" alt="Näyttökuva 2024-4-2 kello 11 27 12" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/63414aed-ad5f-4ce0-a988-59c88a89f637">


Avasin t001 koneen ja annoin komennon sudo salt-key -A. Tässä kohtaa minulle tuli ongelma, sillä olin katsonut ip osoitteen hostname -I komennolla ja sain sillä 10.0.2.15
ja 192.168.88.101 näistä kahdesta en tiennyt kumpaa käyttäisin t002 koneen sudoedit kohdassa ja laitoin ensin 10.0.2.15 t001 koneella syöttäessäni komentoa salt-key ... 
sain ilmoituksen että se ei toimi joten menin exit pois koneelta ja avasin t002 koneen ja jälleen sudoedit ja kokeilin 192.168.88.101 Jälleen tuli muistaa restart,
jonka jälkeen vasta exit. Avasin t001 koneen ja kokeilin sudo salt-key -A komentoa ja tällä kertaa se toimi oikein. Niin kuin kuvasta näkyy niin hyväksyimme orjan avaimen. 

<img width="391" alt="Näyttökuva 2024-4-2 kello 11 20 29" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/8efd7172-ad60-4eb3-9922-672f7ce1414c">

<img width="340" alt="Näyttökuva 2024-4-2 kello 11 24 52" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/18d96fa5-8fa4-4826-9436-f630ca10d83b">


### Kysymys: Miksi komennossa sudo apt-get -y install ... on -y? 

c) Aja shell-komento orjalla Saltin master-slave yhteyden yli.
En ollut ihan varma tästä onko tämä oikein.

<img width="405" alt="Näyttökuva 2024-4-7 kello 19 06 34" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/d3f206d3-8548-42ec-b98c-848cb6e59b98">

Tässä on kokeiltu eri komentoja:

<img width="400" alt="Näyttökuva 2024-4-2 kello 11 28 06" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/6c7db98b-6ba9-458c-abc8-530f16bdf482">

Yllä olevassa kuvassa olen antanut komennon sudo salt '*' cmd.run 'hostname -I' jolla sain tietää t002 eli orja koneen ip-osoitteen. 
Alla olevassa kuvassa kysyn masterilla minionilta, että kuka olen. Komento jota käytin oli sudo salt '*' cmd.run 'whoami' tästä vastauksena tuli orjalta mikä sen nimi on.

<img width="350" alt="Näyttökuva 2024-4-2 kello 11 25 42" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/b81123af-5467-4c37-9290-55bdacc281a1">

Seuraavassa alla olevassa kuvassa halusin nähdä orjan /etc kansion sisällön. 

<img width="554" alt="Näyttökuva 2024-4-7 kello 18 51 33" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/736334a3-fa4a-47f6-a64a-de86a7cb67d5">

d) Aja useita idempotentteja (state.single) komentoja master-slave yhteyden yli.

<img width="464" alt="Näyttökuva 2024-4-7 kello 19 14 31" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/05c20a6b-9429-4961-a71a-3f06c36f5b0f">

Yllä olevassa kuvassa käyttäjä emilia luotiin sillä komennossa määritin että käyttäjä emilia tulee olal olemassa.
Alla olevassa kuvassa näkyy, että kansio moi luotiin sillä sen nimistä kansiota ei vielä ollut. Olen myös lisännyt kuvan jossa näkyy että olen kokeillut että kansio moi 
löytyy t002 koneella.

<img width="465" alt="Näyttökuva 2024-4-7 kello 19 17 29" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/8eee960a-c615-4907-9038-
63eca7551ec5">

<img width="499" alt="Näyttökuva 2024-4-7 kello 19 20 24" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/bae121a9-9ed1-401a-ac95-8157528bee39">


e) Kerää teknistä tietoa orjista verkon yli (grains.item)

<img width="380" alt="Näyttökuva 2024-4-7 kello 18 59 41" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/4b8cdf90-d612-4509-b07a-73dd27171a81">

<img width="540" alt="Näyttökuva 2024-4-7 kello 18 59 54" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/dc0cfe96-9a16-44e4-aeb8-e669d41c1948">

Yllä olevissa kuvissa näkyy tietoja orja koneesta joita katsoin komennolla sudo salt '*' grains.items |less.

<img width="409" alt="Näyttökuva 2024-4-2 kello 11 30 24" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/74e32fb7-f066-4998-83f5-b03089003739">

Yllä olevassa kuvassa näkyy orjan eli koneen t002 virtual tieto. 
Alla olevassa kuvassa näkyy biosin julkaisu päivä.

<img width="437" alt="Näyttökuva 2024-4-7 kello 18 57 29" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/fd6b0b70-d7ee-40b8-9b66-067ad120f970">


f) Hello, IaC. Tee infraa koodina kirjoittamalla /srv/salt/hello/init.sls. Aja tila jollekin orjalle. Tila voi esimerkiksi tehdä esimerkkitiedoston johonkin hakemistoon.
Testaa toisella komennolla, että pyytämäsi muutos on todella tehty.
Loin ensin uuden kansion mkdir /srv/salt/hello ja menin tähän kyseiseen kansioon cd /srv/salt/hello. Seuraavaksi menin tekstieditoriin sudoedit init.sls. Alla olevissa kuvissa 
näkyy mitä kirjoitin tekstieditoriin. Ideana oli siis luoda uusi tiedosto /tmp/helloemilia.txt. Komennolla sudo salt '*' state.apply hello tiedosto luotiin ja kuvissa näkyy,
kuinka tiedosto on jo luotuna. Viimeisessä kuvassa tarkistin ls avulla että /tmp/helloemilia.txt on luotu.

<img width="299" alt="Näyttökuva 2024-4-2 kello 12 36 33" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/6391d273-4c13-49a0-811f-dd3e5f08aaab">

<img width="518" alt="Näyttökuva 2024-4-7 kello 19 36 03" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/2b7e51b9-2e17-4989-8378-4863b40d0582">

<img width="562" alt="Näyttökuva 2024-4-7 kello 19 39 33" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/38ddc52d-1f8b-4719-bec4-fa07b704bbe7">


## Lähteet:
Karvinen, Tero 2024: Infra as Code - Palvelinten hallinta 2024, h2 Soitto kotiin. https://terokarvinen.com/2024/configuration-management-2024-spring/#h2-soitto-kotiin

Karvinen 2018: Salt Quickstart – Salt Stack Master and Slave on Ubuntu Linux https://terokarvinen.com/2018/salt-quickstart-salt-stack-master-and-slave-on-ubuntu-linux/?fromSearch=salt%20quickstart%20salt%20stack%20master%20and%20slave%20on%20ubuntu%20linux

Karvinen 2014: Hello Salt Infra-as-Code. https://terokarvinen.com/2024/hello-salt-infra-as-code/

Karvinen 2021: Two Machine Virtual Network With Debian 11 Bullseye and Vagrant. https://terokarvinen.com/2021/two-machine-virtual-network-with-debian-11-bullseye-and-vagrant/

