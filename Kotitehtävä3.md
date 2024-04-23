# h3 Toimiva versio

## x) Lue ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva. Kannattaa lisätä mukaan myös jokin oma havainto, idea tai kysymys.)

### Chacon and Straub 2014: Pro Git, 2ed: 1.3 Getting Started - What is Git?
- Aina kun annetaan komento git commit tai tallennetaan tiloja git ottaa kuvan miltä kaikki tiedostot näyttävät juuri sillä hetkellä ja tallentaa viittauksen kuvaan.
- Tiedostoja ei pysty muokkaamaan tai hakemistoa vaihtamaan ilman että git huomaisi sen.
- Gitissä toimintojen tekeminen lisää dataa git-tietokantaan.
- Git 3 päätilaa jossa tiedostot voi sijaita modified, staged ja commited.
- Modified tarkoittaa että olet muokannut tiedostoa mutta et ole vielä sitonut (commit) sitä tietokantaan.
- Staged tarkoittaa että muokattu tiedosto on merkitty tämän hetkiseen versioon jotta voi siirtyä seuraavaan commit tilannekuvaan.
- Commited tarkoittaa että data on tallennettu turvallisesti tietokantaan.
### Gitin käyttö on lähinnä 'git add . && git commit; git pull && git push'. Selitä tuon komennon jokainen osa. Käytä apuna itse valitsemiasi lähteitä ja viittaa niihin.
-'git add . && git commit; git pull && git push' komento tehdään aina ensimmäisenä ja aina päätteeksi.
- Katsoin apua stackoverflow sivulta johon Byrtek Adam oli kommentoinut eri komennon eri osia. 
- git add . lisää tiedostot git indexiin, jolla tarkoitetaan aluetta jossa tiedostot odottaa että ne commitetaan.
- git commit tarkoituksena on sitoa hakemiston tiedostot varastoon.
- git pull tarkoittaa että se tuo kaikki muuutokset, joita on tehty sillä aikaa kun olit pois esim. jos joku muu on tehnyt muutoksia yöllä kun olet nukkut.
- git push tarkoittaa, että kun ollaan tehty muutoksia niin tallennetaan/tuodaan ne. Tällöin muut näkevät tekemäsi muutokset.
### Varaston terokarvinen/suolax/ historia, eli loki ja muutokset. Kätevimmin komentokehotteesta 'git clone https://github.com/terokarvinen/suolax.git; cd suolax/; git log --patch --color|less -R'. Wepistäkin saattaa onnistua kliksuttelemalla "Commits".
- 10.4 klo. 20:55 muokattu käyttöohjeita
- 10.4 klo. 20:04 on putsattu tiedosto README.md
- 10.4 klo. 20:02 on lisätty suosikki ohjelmia ja ladattu lista top file
- Katsoin lokeja ja muutoksia komentokehotteessa ja sieltä löytyi tietoa siitä mihin kellon aikaan ja päivänä muutoksia on tehty ja mitä muutoksia suolax varastoon ja sen tiedostoihin. 

## a) Online. Tee uusi varasto GitHubiin (tai Gitlabiin tai mihin vain vastaavaan palveluun). Varaston nimessä ja lyhyessä kuvauksessa tulee olla sana "summer". 
Aiemmin tehty varasto ei kelpaa. (Muista tehdä varastoon tiedostoja luomisvaiheessa, esim README.md ja GNU General Public License 3)

Alla olevassa kuvassa näkyy, että loin uuden varaston GitHubiin nimellä summer.

<img width="1371" alt="Näyttökuva 2024-4-14 kello 16 03 57" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/29ce2907-5076-4814-9340-13e541dff1ae">


## b) Dolly. Kloonaa edellisessä kohdassa tehty uusi varasto itsellesi, tee muutoksia omalla koneella, puske ne palvelimelle, ja näytä, että ne ilmestyvät weppiliittymään.

Aloitin sillä että käynnistin virtuaalikoneen debian vagrantilla. Olin viime tunnilla luonut kansion code jon olin kloonannut yhteinen varaston ja palvelintenhallinta varaston.
Jotta voin kloonata varaston git:iin minun täytyy GitHubista ottaa varaston URL, joka näkyy toisessa alla olevista kuvista. Toinen kuva on otettu terminaalissa jossa näkyy 
komento jota käytin kloonaamiseen eli git clone (URL). Kuvassa näkyy myös että olen tarkistanut, että summer varasto näkyy hakemistossa code varmasti.

<img width="510" alt="Näyttökuva 2024-4-14 kello 16 09 50" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/e0aefdaf-15c0-48a4-8663-a852d4e7bfe7">
<img width="568" alt="Näyttökuva 2024-4-14 kello 16 10 20" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/42cf19f0-6e45-436c-b022-77ffb9ac0322">

Loin seuraavaksi koneellani uusia tiedostoja varastoon ja tarkistin, että ne ovat näkyvissä myös verkossa. Alla olen ottanut kuvan uusista tiedostoista jotka olen tehnyt koneellani.
Olen myös ottanut kuvan siitä, että nämä kyseiset tiedostot näkyvät verkossa. Tiedostojen luomiseen käytin nanoa. Kun olin tehnyt halutut muutokset eli luonut kaksi uutta tiedostoa ajoin komennon 'git add . && git commit; git pull && git push', josta avautui 
tekstieditori johon kirjoitin commit messagen eli lyhyt kuvaus siitä mitä muutoksia olen tehnyt. Tämän jälkeen tarkistin ls -la komennolla,
että tiedostot näkyivät varastossa. Kun tiedostot näkyivät siirryin tarkastamaan verkosta, että uudet tiedostot näkyvät sielläkin.

<img width="569" alt="Näyttökuva 2024-4-14 kello 16 23 21" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/07c084bd-f04c-40fb-a61d-455f8a47738c">
<img width="572" alt="Näyttökuva 2024-4-14 kello 16 24 12" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/61c5fcc5-2907-46ad-8bd4-9a4240982fc9">
<img width="566" alt="Näyttökuva 2024-4-14 kello 16 23 57" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/ff3913a4-45f2-4656-8e3a-d37aae9076f6">
<img width="479" alt="Näyttökuva 2024-4-14 kello 16 24 32" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/cd9ffa3d-b3e7-449b-a2f6-3a88c3e36912">
<img width="903" alt="Näyttökuva 2024-4-14 kello 16 27 10" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/b75274cf-bd44-42b9-83c1-7d69487d07a8">

## c) Doh! Tee tyhmä muutos gittiin, älä tee commit:tia. Tuhoa huonot muutokset ‘git reset --hard’. Huomaa, että tässä toiminnossa ei ole peruutusnappia.
Kävin alla olevan kuvan mukaisesti muokkaamassa tiedostoa varastoh3.md kun lähdin nanosta en tehnyt normaalia komentoa 'git add . && git commit; git pull && git push' vaan 
annoin komennon git reset --hard, joka tuhosi tekemäni muutokset tiedostoon. Kävin vielä nanon avulla tarkistamassa että tämä onnistui oikein ja kirjoittamani muutos oli kadonnut
mutta muut tekstit olivat edelleen tiedostossa.

<img width="568" alt="Näyttökuva 2024-4-14 kello 16 40 14" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/8f06ef4f-d912-44b4-a219-30d3ce8f0e2f">
<img width="572" alt="Näyttökuva 2024-4-14 kello 16 41 21" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/bd4dcacb-8b6d-4a03-b20a-45538e9de8b3">


## d) Tukki. Tarkastele ja selitä varastosi lokia. Tarkista, että nimesi ja sähköpostiosoitteesi näkyy haluamallasi tavalla ja korjaa tarvittaessa.
<img width="571" alt="Näyttökuva 2024-4-14 kello 16 45 55" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/fac7f63e-a5b4-4ef6-b65a-9d7a3b6f648a">

Yllä olevassa kuvassa tarkastelin varastoni lokia. Kuvassa näkyy että nimeni on haluamallani tavalla eli EmiliaHauskaviita yhteen ja että sähköposti osoitteeni on oikein.
Mikäli nimeni ja sähköpostini olisi väärin voisin alla olevan kuvan mukaisilla komennoilla korjata ne. 

<img width="553" alt="Näyttökuva 2024-4-14 kello 16 48 35" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/a6c77ff9-355d-4fbc-af52-0abb37ea5216">


## e) Suolattu rakki. Aja Salt-tiloja omasta varastostasi. (Salt tiedostot mistä vain hakemistosta "--file-root teronSaltHakemisto". 
Esimerkiksi 'sudo salt-call --local --file-root srv/salt/ state.apply', huomaa suhteellinen polku.)

En osannut tehdä tehtävää kun yritin tehdä sitä sain alla olevan kuvan virheen. 
<img width="709" alt="Näyttökuva 2024-4-14 kello 17 21 44" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/7cf885cc-260f-426d-91f7-b52d2da2e478">
23.4.2024 päivitys:
Loin '/srv/salt' kansioon 'mkdir hello' hakemiston jonka sisään tein init.sls tiedoston johon laitoin /tmp/helloemilia: ja uudelle riville kahdella välillä file.managed. Hello tilan ajo onnistui oikein mutta komento 'sudo salt-call --local --file-root srv/salt/ state.apply' en saanut toimimaan. Sain edelleen yllä olevan failed ilmoituksen.

<img width="364" alt="Näyttökuva 2024-4-23 kello 8 31 22" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/e8a2b57b-8068-4e85-a956-30bc447f207d">
<img width="727" alt="Näyttökuva 2024-4-23 kello 8 32 16" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/d1bfff60-ad05-4662-b858-e3d812179276">

23.4.2024 päivitys:
tee srv/salt/hello kansio kotihakemiston alle. Nyt sain komennon 'sudo salt-call --local --file-root srv/salt/ state.apply' toimimaan. Olin aikaisemmin tehnyt hello kansion väärään hakemmistoon sillä olin tehnyt sen root hakemiston alle.
<img width="876" alt="Näyttökuva 2024-4-23 kello 10 53 26" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/1e7fbdb1-d1e5-45a8-b0b0-f08b1601bf1c">



## f) Vapaaehtoinen: Se toinen järjestelmä: kokeile Gittiä eri käyttöjärjestelmällä kuin sillä, millä teit muut harjoitukset. 
Selitä niin, että kyseistä järjestelmää osaamatonkin onnistuu. Mahdollisuuksia on runsaasti: Debian, Fedora, Windows, OSX...
Gitin latasin myös omalle koneelleni jossa macOS käyttöjärjestelmä. Jotta pystyin lataamaan gitin minun täytyi ensin ladata brew. Alla olevassa kuvassa näkyy komento,
jolla sain brew:n avulla gitin ladattua. Tämän jälkeen loin uuden kansion, jossa olisi kloonatut varastot. Jotta kloonaaminen onnistuisi täytyi minun ensin hakea ssh public key.
Tämä tapahtui menemällä .ssh kansioon ja käyttämällä komentoa ssh-keygen. Avaimen sain kopioitua kun käytin komentoa cat id_rsa.pub. Hyvin tärkeää on kopioida pub avain,
sillä se on julkinen, pelkkä id_rsa on yksityinen avain ja sitä ei missään nimessä saa näyttää muille! Kävin viemässä avaimen minun GitHub asetuksista löytyvään SSH key kohtaan.
Tällöin saan kloonattua varastojani. Olen ottanut alas myös kuvan asetuksista johon olen tuonut kaksi avainta sillä latasin git ensin virtuaalikoneelle debian ja 
sitten vasta macille. Sen vuoksi tarvitsin molemmilta koneilta omat julkiset avaimet. Seuraavaksi menin luomaani hakemistoon johon kloonasin varaston URL käyttäen. Tämän
jälkeen pystyin muokkaamaan kloonaamiani varastoja gitillä.

<img width="1160" alt="Näyttökuva 2024-4-9 kello 11 06 55" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/299caa71-c046-497b-969a-152382362b53">
<img width="1159" alt="Näyttökuva 2024-4-9 kello 11 06 34" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/6ceaf4f3-72d6-45a3-aeaf-5934a44ad595">
<img width="1357" alt="Näyttökuva 2024-4-14 kello 16 58 20" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/f991e82c-afe4-429f-8775-adfb5b0886ca">


## g) Vapaaehtoinen: yhteistyötä: anna kaverillesi (tai alter egollesi) oikeus kirjoittaa varastoosi (commit access). Tehkää molemmat muutoksia varastoon gitillä.
Kokeilimme tätä tunnilla Leevin kanssa niin että loin uuden repon ja annoin Leeville oikeudet tähän ja pääsimme molemmat tekemään muutoksia varastoon. Loimme tiedostoja
gitillä ja myös suoraan verkossa ja saimme kaiken toimimaan. Myös tiedostojen muokkaaminen niin gitissä että verkossa onnistui ja muutokset tulivat näkyviin. Alla olevassa 
kuvassa olen avannut tiedoston verkossa ja leevi on käynyt muokaamassa sitä gitillä.

<img width="820" alt="Näyttökuva 2024-4-9 kello 10 35 23" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/778992e9-5567-4e27-8323-a3f59a622dcd">

Kuvassa joka on alla näkyy git clone komento jossa olen cloonannut yhteinen repon.

<img width="953" alt="Näyttökuva 2024-4-9 kello 10 41 10" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/198a6af5-9903-4cf9-bc14-8954229d206a">


## Lähteet
Chacon & Straub 2014: https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F

Karvinen, T. Suolax, GitHub 2024: https://github.com/terokarvinen/suolax/commits/main/

Karvinen, T. h3 Toimiva versio 2024: https://terokarvinen.com/2024/configuration-management-2024-spring/#h3-toimiva-versio

Byrtek, A. 2011. Stockoverflow: https://stackoverflow.com/questions/6143285/git-add-vs-push-vs-commit 


