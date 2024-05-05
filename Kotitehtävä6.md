# h6 Benchmark
## x) Lue ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)
Windows Package Manager: Introduction, Install libraries, Populate the local Git repository, Update minion database, Install software package, Usage osa. Eli sivun alusta kappaleen "Remove a package" loppuun, poislukien "Configuration". (Kannatta soveltaa asennuksesta idempotentti versio, ulkomuistista: 'sudo salt-call --local -l info state.apply pkg.installed curl').

-Salt tarjoaa Windowsille oman paketinhallinta työkalun. 
-Ohjelman määritelmätiedosto on .sls loppuinen.
-Jos käytetään Salt Windows -paketinhallintaa Salt Git -varastossa isännöityjen paketinmääritystiedostojen kanssa, asennetaan kirjastot GitPython tai pygit2.
-Luodakseen tietokantamerkinnät paketin määritystiedostolle ja rakentaakseen pakettitietokanta pkg.refresh_dp tulee ajaa minioneilla.
-Pakettien lataus Windowsissa tapahtuu komennolla salt-call --local pkg.install (haluttu ohjelma).


## a) Paketti Windowsia. Asenna Windowsiin tai Macciin ohjelmia Saltin pkg.installed -funktiolla. (Jos teit tarvittavat asennukset jo tunnilla, voit kirjoittaa ympäristön asennuksen ulkomuistista, ja asentaa nyt vain jonkin uuden paketin. Muistinvaraisesti kirjoitetut muistiinpanot ovat paljon epämääräisempiä kuin työn aikana kirjoitetut, joten merkitse selvästi, mitkä osat on kirjoitettu ulkomuistista ja mitkä työskennellessä.)
Kyseisen tehtävän kerkesin thedä jo tunnilla. Olin ladannut koneelleni Saltin jo aikaisemmin. Kokeilin toimiiko Saltin pkg.installed konellani. Käytin komento 'sudo salt-call --local 
state.single pkg.installed tree'. Komento latasi minulle onnistuneesti tree ohjelman. Seuraavaksi aloitin tekemään hello tilaa Saltilla. Tein kansioon '/tmp' uuden kansion 'mkdir salt'.
'/tmp/salt' loin uuden kansion nimeltä hello jonka sisään tein init.sls tiedoston. Init.sls tiedostoon tein alla olevan kuvan mukaisen sisällön. 

Seuraavaksi kokeilin ajaa Hello tilan komennolla 'sudo salt-call --local --file-root /tmp/salt state.apply hello'. Tila ajettiin onnistuneesti ja siitä on kuva alhaalla.
<img width="712" alt="Näyttökuva 2024-4-30 kello 13 08 00" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/2c4a86ef-d7c5-4ca0-9f3f-876feb9ea477">


Nyt pääsin tekemään tilaa jolla saan ladattua eri paketteja. Tein kansioon '/tmp/salt' uuden kansion favourites ja kävin sen sisään tekemässä init.sls tiedoston johon lisäsin eri paketteja. 
Alla olevassa kuvassa näkyy favourites kansion init.sls tiedostosta kuva. 

<img width="569" alt="Näyttökuva 2024-4-30 kello 13 32 57" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/86de047a-cece-4258-b442-857ebfa4e95e">


Viimeiseksi tein top.sls tiedoston '/tmp/salt' kansioon. Top.sls tiedostoon lisäsin moelmmat favourites ja Hello joista löytyy init.sls tiedostot. Kokeilin ajaa komennon 
'sudo salt-call --local --file-root /tmp/salt state.apply' Jolloin top.sls tiedoston sisältö ajettiin. Paketit latautui onnistuneesti ja myös tiedosto löytyi, jonka olin määrittänyt Hello init.sls tiedostossa.

<img width="615" alt="Näyttökuva 2024-5-1 kello 16 11 43" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/000fe42d-4b2d-4ad5-9c4c-a7ba974861d7">


## b) Benchmark. Etsi 3-7 keskitetyn hallinnan projektia, esimerkiksi tämän kurssin "Oma moduli" lopputyötä. Työn tulee olla modernia keskitettyä hallintaa (idempotentti, infra koodina, yksi totuus). Esimerkiksi pelkkä shell script ei kelpaa. Työ saa käyttää mitä vain työkalua, esim Salt, Puppet, Ansible, Chef, Conftero, CFEngine. Tässä alakohdassa ei tehdä mitään testejä, vaan arvioidaan töitä vain niiden kotisivujen perusteella. Etsimiseen voit käyttää hakukoneita. Listaa kustakin
  Tarkoitus (eli "mitä hyötyä tästä on" eli "business purpose" eli "miksi haluaisin asentaa tämän".)
  Kyllä näin: (business purpose): "Robotti kuljettaa minulla jääkaapista limpparia"
  Ei näin, tekniikoiden luetteleminen ei ole sovelluksen tarkoitus: "ESP32 ja Arduino ohjaavat servoja, jotka LIDAR:lla väistelevät       kappaleita C++-ohjelmalla; tartuntakomponentti käyttää PDI-säädintä..."
  Lisenssi
  Lisenssin nimi
  Missä tuossa työssä se lisenssi lukee
  Mitä lisenssi tarkoittaa, eli pääasiallinen jurdiinen vaikutus
  Tekijä ja vuosi
  Riippuvuudet: Alusta (käyttöjärjestelmä, jokin tietty pilvi...), verkkoympäristö tms.
  Kiinnostavaa, esim
  Hyödyllinen lopputulos
  Kiinnostava tekniikka, esim. jokin tapa käyttää Saltia
  Avoimet kysymykset ja muut huomiot
  
1. https://sampohautala.wordpress.com/2018/12/09/ph-h7-oma-moduli/
   Tarkoitus: Kehitysympäristön luominen linuxille, ja kuvanmuokkaus ja 3D-mallinnus graaffiselle suunnittelijalle Windowsiin.
   Lisenssi: En löytänyt.
   Tekijä ja vuosi: Sampo Hautala, 2018
   Riippuvuudet: Virtuaalikone, Herra-orja arkkitehtuuri, linux ja windows orjat.
   Kiinnostava: Työstä kiinnostavan teki se että tässä ladattiin hyvin erilaisia paketteja ja niitä ladattiin linuxille ja Windowsille.
   
2. https://jannelinux.design.blog/2020/05/19/oma-moduuli-h7/
   Tarkoitus: Luoda tila, jolla pystytään asentamaan halutut paketit jo valmiina confattuina uudelle koneelle.
   Lisenssi: En löytänyt
   Tekijä ja vuosi: Janne Mustonen, 2020
   Riippuvuudet: linux ja virtualbox
   Kiinnostava: Työ oli erittäin hyödyllinen ja varmasti tulee auttamaan myös tulevaisuudessa. Osaan paketeista tarvitsi ladata myös                     repository ja niiden tekeminen oli mielestäni kiinnostavaa.
   
3. https://markuspyharanta.com/2016/12/10/palvelinten-hallinta-oma-moduuli/
   Tarkoitus: Automatisoida Puppetin avulla Lamp-stack ja gedit asennus uusille koneille. 
   Lisenssi: En löytänyt.
   Tekijä ja vuosi: Markus Pyhäranta, 2016
   Riippuvuudet: Linux, virtuaalikone ja Puppet
   Kiinnostava: Erityisesti itseäni kiinnosti työssä se että se oli tehty käyttäen Puppettia eikä Saltia.

4. https://katrilaulajainen.wordpress.com/2018/05/10/palvelinten-hallinta-h6-8-5-2018-oma-miniprojekti-saltilla/
   Tarkoitus: Automatisoida Saltin avulla pakettien lataus valmiiksi confattuina uusille koneille.
   Lisenssi: En löytänyt.
   Tekijä ja vuosi: Katri Laulajainen, 2018
   Riippuvuudet: Linux, virtuaalikone, (git)
   Kiinnostava: Työssä erityisesti itseäni kiinnosti firefox oletuskotisivun vaihtaminen.

## c) Testbench. Aja toisen tekemä tila.
Valitse jokin edellisessä kohdassa tutkimasi moduli. Perustele valintasi.
Tarkista koodi.
Lataako koodi binäärejä? Lataako paketinhallinnan ulkopuolelta? Onko luotettavia ohjelmistolähteitä?
Aja koodi. Käytä tarvittaessa virtuaaliympäristöä tai muuta eristystä.
Testaa lopputulos.
Ota ruutukaappauksia sopivassa laajuudessa.
Kommentoi ja arvioi modulia.
Modulin kaikkia bugeja ei tarvitse korjata, tarkoitus on ajaa modulia ja arvioida sitä.
Jos jokin moduli vaikuttaa täysin toimimattomalta, kirjaa ylös yrityksesi ja kokeile toista modulia.

Valitsin tehtävään moduliksi Katri Laulajaisen modulin, jossa tarkoituksena oli ladata kolme pakettia, firefox, gimp ja sshopen-server. 
Valitsin kyseisen työn, sillä kiinnostuin firefoxin asentamisesta. Aloitin tehtävän tekemisen noudattamalla 
Laulajaisen ohjeita, mutta ensimmäinen ongelma tuli kun ajoin salt firefox-tilan, jonka sisään tein init.sls tiedoston jossa oli eri paketteja, joita ladattaisiin. Jostain syytä sain alla näkyvässä kuvassa olevan virheilmoituksen. 
<img width="653" alt="Näyttökuva 2024-5-3 kello 19 36 50" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/be227587-c10c-4715-aa3d-caf614ab706b">

Päätin kokeilla toimiiko kuitenkin kahden muun paketin lataukset, jos poistan init.sls tiedostosta kohdan firefox. Ajoin scriptin high.sh jonka olin tehnyt sitä varten että voisin ajaa salt-komentoja sillä.
Kokeilin uudelleen tilan toimivuutta ja tällä kertaa sain onnistuneen vastausken. 
<img width="513" alt="Näyttökuva 2024-5-3 kello 19 56 45" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/9d754d7d-d5f6-4d5c-8d6c-f25ec7de0dd5">

Jatkoin ohjeiden seuraamista jättämällä firefox kohdan pois. Tarkoituksena olisi kuitenkin ollut firefox oletuskotisivun vaihtaminen. Tämän jälkeen keskityttiinkin ssh-serveriin. 
Tarkoituksena oli vaihtaa oletusportti 22 numeroon 8888. Kopioin sshd_config tiedoston /srv/salt/firefox kansioon. Init.sls tiedostoon lisäsin kaksi uutta kohtaa. Jotka näkyvät kuvassa alla.
<img width="367" alt="Näyttökuva 2024-5-3 kello 21 04 17" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/0aa7154d-d054-4d20-b92d-99bb8d8c1559">

Seuraavaksi kävin muokkaamassa sshd_config tiedostoon kohdan Port {{port}}. Tehtävässä käytettiin apuna jinjaa joka vaihtaa sulkujen sisällä olevan port sanan numeroiksi 8888. 
Kokeilin jälleen ajaa tilaa.
<img width="714" alt="Näyttökuva 2024-5-3 kello 20 54 23" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/180255d4-8e62-4a99-b99f-cc25a6c6877b">

Viimeiseksi tehtävässä oli tarkoitus avata portteja palomuurissa. Tämä olisi tapahtunut kopioimalla /etc/ufw/user.rules mutta en löytänyt haluttua tiedostoa kansiosta. 
Moduli oli mielestäni hyvin toteutettu ja ohjeet olivat selkeät noudattaa. Vaikka en saanut modulia kokonaan tehtyä ymmärsin mitä sillä haetaan ja mitä eri kohdat tarkoittaisivat. 


## d) Viisi ideaa. Listaa viisi ideaa omalle modulille, kurssin lopputehtävälle. Modulilla tulee olla tarkoistus. Sen ei tarvitse silti ratkaista mitään oikeaa liiketoiminnan ongelmaa, vaan tarkoitus voi olla keksitty. Kunkin idean kuvaukseen riittää yksi virke. Ensi kerralla katsomme yhdessä aiheen valintaa ja sopivia vinkkejä. Tarvitsen pohjaksi omia ideoitasi, jotta voin antaa hyödyllisiä ja juuri sinulle sopivia neuvoja.

1- 
2-
3-
4-
5-

## Lähteet

Karvinen, T. h6 Benchmark, 2024: https://terokarvinen.com/2024/configuration-management-2024-spring/#h6-benchmark

Hautala, S. h7 oma moduli, 2018: https://sampohautala.wordpress.com/2018/12/09/ph-h7-oma-moduli/

Mustonen, J. oma moduli h7, 2020: https://jannelinux.design.blog/2020/05/19/oma-moduuli-h7/

Pyhäranta, M. Palvelinten hallinta - Oma moduuli, 2016: https://markuspyharanta.com/2016/12/10/palvelinten-hallinta-oma-moduuli/

Laulajainen, K. Oma miniprojekti Saltilla, 2018: https://katrilaulajainen.wordpress.com/2018/05/10/palvelinten-hallinta-h6-8-5-2018-oma-miniprojekti-saltilla/

Salt project, 2024: https://docs.saltproject.io/en/latest/topics/windows/windows-package-manager.html
