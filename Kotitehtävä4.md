# h4 Demoni

## x) Lue ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)

### Karvinen 2023: Salt Vagrant - automatically provision one master and two slaves, vain kohdat
  (Infra as Code - Your wishes as a text file & top.sls - What Slave Runs What States)
- vagrant up käynnistää koneet.
- vagrant ssh tmaster ottaa yhteyden master koneeseen.
- sudo salt-key -A komennolla hyväksytään minionien avaimet.
- sudo salt '*' test.ping on hellpo tapa kokeilla yhteyttä.
- sudo salt '*' grains.items kerää tietoa koneista.
- '*' tarkoittaa kaikkia minion koneita.
- top.sls on tiedosto joka määrittää mitkä tilat ajetaan millekkin orjalle
  
### Salt contributors: Salt overview, kohdat
  (Rules of YAML, YAML simple structure & Lists and dictionaries - YAML block structures)

  - YAML on merkintäkieli, jossa on monia tehokkaita ominaisuuksia.
  - YAML luomiseen on perussääntöjä.
  - esim:
    - Kommentin eteen tulee #.
    - TAB ei ole sallittu voit käyttää vain välilyöntejä.
    - Kirjainten koolla on merkitystä.
  - Scalars: kuvaukset, joissa arvo voi olla numero, merkkijono tai looginen arvo.
  - Lists: avaimen jälkeen arvoluettelo, jokainen arvo omalla rivillä ja jatkuu kahdella välilyönnillä ja yhdysviivalla.
  - Dictionaries: kokoelma avaimia, kuvauksia ja luetteloita.
  - YAML on järjestetty lohkorakenteiksi.
  
  
### Karvinen 2018: Pkg-File-Service – Control Daemons with Salt – Change SSH Server Port
(Artikkelissa on jonkun toisen Linux-version tiedosto. Jos tekisit samanlaisen, niin käyttäisit tietysti oman järjestelmäsi asetustiedostoa pohjana.)

- Artikkelissa oli näytetty yksinkertainen Salt tila ssh-palvelimen portin muuttamiseksi.
- Valtavaa määrää demoneita voi hallita kokoonpanonhallintajärjestelmällä.
  
  
  
### Silmäile Saltin ohjeet tilafunktioille pkg, file ja service. Nämä artikkelit ovat pitkiä, riittää kun luet vain johdannon ja silmäilet maintut komennot. Ei kannata yrittää opetella satoja itselle tarpeettomia parametreja ulkoa. (Less-vinkit alla)
  $ sudo salt-call --local sys.state_doc pkg # johdanto + silmäile pkg.installed, pkg.purged, pkgs
  $ sudo salt-call --local sys.state_doc file # johdanto + silmäile file.managed, file.absent, file.symlink
  $ sudo salt-call --local sys.state_doc service # johdanto + silmäile service.running, service.dead, enable

  - Kävin silmäilemässä eri artikkelit ja luin niiden johdannot otin myös parista eri kohdista kuvankaappauksia.

<img width="731" alt="Näyttökuva 2024-4-21 kello 14 22 27" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/7c8cb1bb-594a-4869-bd2a-de506de5fccd">
<img width="650" alt="Näyttökuva 2024-4-21 kello 14 22 53" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/02b88341-f979-4f3b-bbcc-7182ffa070cb">
<img width="633" alt="Näyttökuva 2024-4-21 kello 14 25 21" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/9baf7cda-f938-4165-8671-8adc62e7e65b">
<img width="683" alt="Näyttökuva 2024-4-21 kello 14 26 12" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/439b5913-b321-4712-8293-5635e397a7d6">

  
## a) Hello SLS! Tee Hei maailma -tila kirjoittamalla se tekstitiedostoon, esim /srv/salt/hello/init.sls.

Aloitin tehtävän avaamalla terminaalin jossa menin kansioon 'twohost'. Kansiossa tein komennon 'vagrant up', joka käynnisti koneet ja 'vagrant ssh t001', jolla sain yhteyden
t001 koneeseen. Menin '/srv/salt' kansioon johon loin uuden kansion 'mkdir hello'. Kansion 'hello' sisään tein 'init.sls' tiedoston.

<img width="348" alt="Näyttökuva 2024-4-19 kello 17 57 31" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/e34c2bc1-9234-466c-aac8-33f1ee740b19">

init.sls tiedoston sisään kirjoitin alla olevan kuvan sisällön. Tämä tarkoittaa sitä että kun ajetaan komento 'sudo salt-call --local state.apply hello' tapahtuu 'init.sls' tiedostoon
määrätty komento. Tässä tapauksessa siis 'sudo salt-call --local state.apply hello' luo meille uuden tiedoston nimeltä 'helloemilia' kansioon '/tmp'. 

<img width="649" alt="Näyttökuva 2024-4-19 kello 17 57 41" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/1f95d081-3467-42b8-ad5d-9eaf623250e5">

Alta löytyvästä kuvasta näkyy vastaus kun ajetaan komento 'sudo salt-call --local state.apply hello'. Niin kuin kuvasta näkyy kaikki onnistui ja kohdassa 'Summary for local'
ja Succeeded näkyy 1 ja changed 1 tarkoittaa sitä että komento onnistui, mutta jotta se onnistui täytyi tehdä muutos. 

<img width="1075" alt="Näyttökuva 2024-4-21 kello 10 32 59" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/7729ed9d-de8b-4e25-b0e4-4c6f99eefec8">

Seuraavaksi vielä tarkistin, että uusi tiedosto oli luotu '/tmp' kansioon. Alla olevasta kuvasta näkyy että olen kansiossa '/tmp' ja ls komennolla olen katsonut että tiedosto on siellä.

<img width="187" alt="Näyttökuva 2024-4-21 kello 10 20 25" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/110f8d20-055c-430f-93b6-5082f786f97a">


## b) Top. Tee top.sls niin, että useita valitsemiasi tiloja ajetaan automaattisesti, esim komennolla "sudo salt '*' state.apply" tai "sudo salt-call --local state.apply".

Käytin tähän tehtävään hyväksi äsken luomaani hello tilaa hyödyksi. '/srv/salt' kansioon loin uuden kansion 'mkdir favourites', sekä uuden tiedoston nimeltä top.sls. 
'sudoedit top.sls' tein alla olevan kuvan mukaiset muutokset. 

<img width="235" alt="Näyttökuva 2024-4-19 kello 18 03 32" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/de2f63ba-165f-449b-968c-66cbc363a957">

Seuraavaksi siirryin 'cd favourites' kansioon, johon tein init.sls. 'sudoedit init.sls' laitoin pari eri ohjelmaa jotka halusin minulle latautuvan. Alla olevassa kuvassa näkyy 
init.sls sisältö.

<img width="290" alt="Näyttökuva 2024-4-19 kello 18 17 03" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/e5170970-04b6-4cac-b515-e3395948ddb9">

Ajoin komennon sudo salt-call --local state.apply jonka tulos oli alla olevan kuvan mukainen. Kuvasta näkee että succeeded oli 3 ja changed oli 1 tämä tarkoittaa että kaikki onnistu,
mutta jotain piti muuttaa. Koska minulla ei ollut kaikkia paketteja vielä niin osa niistä latautui vasta ja sen vuoksi changed on 1. 

<img width="1074" alt="Näyttökuva 2024-4-19 kello 18 18 18" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/a193d527-2149-48fc-a981-daa61936c222">

Kokeilin vielä että eri paketit toimivat minulla. Tree ja cowsay toimivat molemmat niin kuin kuvista voidaan nähdä. 

<img width="323" alt="Näyttökuva 2024-4-19 kello 18 22 19" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/701e5207-960f-4759-88d1-3b703d961373">
<img width="303" alt="Näyttökuva 2024-4-21 kello 11 14 36" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/fc541483-2299-4a24-bba2-f367db5ef16d">


## c) Apache easy mode. Asenna Apache, korvaa sen testisivu ja varmista, että demoni käynnistyy.
 -Ensin käsin, vasta sitten automaattisesti.
 -Kirjoita tila sls-tiedostoon.
 -pkg-file-service
 -Tässä ei tarvita service:ssä watch, koska index.html ei ole asetustiedosto

Aloitin tehtävän antamalla komennon 'sudo apt-get update', jonka jälkeen latasin apache2 'sudo apt-get -y install apache2'. Lataamisen jälkeen tarkistin komennolla 'systemctl status apache2',
että apache on päällä. Latauksesta ja statuksen tarkastamisesta on kuvat alapuolella.

<img width="1066" alt="Näyttökuva 2024-4-19 kello 18 05 58" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/a74cdf01-c7b3-41e6-a5d1-eebae8c1dac2">
<img width="656" alt="Näyttökuva 2024-4-19 kello 18 06 28" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/e5277bcf-2841-4770-bdc9-591e111940cd">

Komennolla 'echo "Apache easy mode testi" | sudo tee /var/www/html/index.html' korvasin testisivun index.html sisällön. Seuraavaksi menin kansioon '/etc/apache2/sites-available', johon
tein uuden conf tiedoston nimeltä emilia.conf. Alla löytyy kuva jossa näkyy reitti jota olen kulkenut. Alla on myös kuva emilia.conf sisällöstä. 

<img width="938" alt="Näyttökuva 2024-4-21 kello 11 55 16" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/0d87d422-878f-4138-a1e2-7df90936b54b">
<img width="422" alt="Näyttökuva 2024-4-21 kello 11 58 08" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/34a377dc-81e7-4107-81dd-fd6278ad4a09">

Tiedoston emilia.conf luomisen jälkeen menin taaksepäin kohtaan '/etc/apache2', josta avasin kansion 'cd sites-enabled'. Tähän kansioon tein uuden linkin emilia.conf tiedostoon.
 
<img width="615" alt="Näyttökuva 2024-4-21 kello 11 47 16" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/b5873bd0-5a48-4e0e-ae2b-8705eb718a57">

Viimeiseksi muutoksien jälkeen käynnistin apache2 uudelleen komennolla 'sudo systemctl restart apache2'. Komennolla 'curl localhost' tuli vastaus "Apache easy mode testi"

<img width="437" alt="Näyttökuva 2024-4-21 kello 11 53 44" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/c2fc87c3-fd08-4057-a817-70f700725a16">

Seuraavaksi meillä on vuorossa tämän äskeisen automatisointi. Tämä tapahtui menemällä kansioon '/srv/salt' johon loin uuden kansion 'sudo mkdir apache'. '/srv/salt/apache' kansioon
tein uuden 'init.sls' tiedoston. 'init.sls' tiedoston sisältö näyttää alla olevan kuvan mukaiselta. Jotta kaikki toimi oikein täytyi minun kopioida 'emilia.conf' 'salt' kansioon.
Tämä tapahtui komennolla 'cp /etc/apache2/sites-available/emilia.conf /srv/salt'.

<img width="429" alt="Näyttökuva 2024-4-21 kello 13 29 36" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/ef93ad01-c56e-4184-bea7-43fd42a47ea5">

Suoritin komennon 'sudo salt-call --local state.apply apache', jonka tuloksista voidaan nähdä että automatisointi on nyt onnistunut. Tulokset näkyvät alla olevassa kuvassa. 

<img width="1124" alt="Näyttökuva 2024-4-21 kello 13 28 23" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/4d719462-dc6d-4090-afb0-69a977ee6a85">

Kokeilin seuraavaksi ajaa vielä tilan minion eli t002 koneelleni. Alla olevista tuloksista nähdään, että tämä onnistui onnistuneesti.

<img width="913" alt="Näyttökuva 2024-4-21 kello 13 37 21" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/a4d5274d-bea9-41b0-93e7-c6a98f22b575">
<img width="632" alt="Näyttökuva 2024-4-21 kello 13 37 50" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/0e8b191f-ec41-4ac7-b573-bf5a9a15eee5">


## d) SSHouto. Lisää uusi portti, jossa SSHd kuuntelee.
(Jos käytät Vagrantia, muista jättää portti 22/tcp auki - se on oma yhteytesi koneeseen. SSHd:n asetustiedostoon voi tehdä yksinkertaisesti kaksi "Port" riviä, molemmat portit avataan.
Löydät oikean asetuksen katsomalla SSH:n asetustiedostoa
Nyt tarvitaan service-watch, jotta demoni käynnistetään uudelleen, jos asetustiedosto muuttuu masterilla)

Käytin tehtävässä samaa t001 konetta jota olen käyttänyt aikaisemmissakin tehtävissä. Aloitin kopioimalla 'sshd_config' tiedoston '/srv/salt' kansioon. 

<img width="462" alt="Näyttökuva 2024-4-21 kello 12 54 54" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/b81d77b8-c408-4c4f-94c4-6555474cdae3">

Kopioinnin jälkeen tein '/srv/salt' kansioon uuden tiedoston 'sudoedit sshd.sls' jonka sisältö on alla olevan kuvan mukainen. Tämän jälkeen menin lisäämään uudet portit 
'sshd_config' tiedostoon. Lisäsin portit 22 ja 1234 tiedostoon.

<img width="298" alt="Näyttökuva 2024-4-21 kello 13 09 34" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/ed39839c-4040-44df-bde0-414d07ac1656">
<img width="568" alt="Näyttökuva 2024-4-21 kello 13 11 14" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/1f6d24d9-bedb-4673-89fd-a7e122342d97">

Seuraavaksi käyynistin ssh uudelleen komennolla 'sudo systemctl restart ssh', jonka jälkeen ajoin komennon 'sudo salt-call --local state.apply sshd' (tulos näkyy alla olevassa kuvassa).
Alla olevasta kuvasta nähdään että portit on onnistuneesti nyt lisätty. 

<img width="574" alt="Näyttökuva 2024-4-21 kello 13 06 50" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/ddac64d3-acac-4742-acb3-8e9215a5c067">
<img width="433" alt="Näyttökuva 2024-4-21 kello 13 06 55" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/f68445a8-dc3a-4585-b574-1974dd7526cc">

Seuraavaksi varmistin että pyydetyt portit kuuntelevat ja siihen käytin komentoa 'sudo lsof -i -P -n | grep LISTEN', kyseisen komennon löysin netistä (cyberciti,2024). Alla 
olevassa kuvassa näkyy että lisäämäni portit kuuntelevat.

<img width="589" alt="Näyttökuva 2024-4-21 kello 13 24 44" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/ef06fa35-acfc-4688-8fb1-3fccc713acd5">


## Lähteet
Vivek Gite, How to check if port is in use on Linux or Unix, 2024: https://www.cyberciti.biz/faq/unix-linux-check-if-port-is-in-use-command/

Karvinen, T, h4 Demoni, 2024: https://terokarvinen.com/2024/configuration-management-2024-spring/#h4-demoni

Salt contributors: Salt overview: https://docs.saltproject.io/salt/user-guide/en/latest/topics/overview.html#rules-of-yaml

Karvinen 2018: Pkg-File-Service – Control Daemons with Salt – Change SSH Server Port: https://terokarvinen.com/2018/04/03/pkg-file-service-control-daemons-with-salt-change-ssh-server-port/?fromSearch=karvinen%20salt%20ssh

Karvinen 2023: Salt Vagrant - automatically provision one master and two slaves: https://terokarvinen.com/2023/salt-vagrant/#infra-as-code---your-wishes-as-a-text-file

