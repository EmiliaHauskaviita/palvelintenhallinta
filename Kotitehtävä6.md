# h6 Benchmark
## x) Lue ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)
Windows Package Manager: Introduction, Install libraries, Populate the local Git repository, Update minion database, Install software package, Usage osa. Eli sivun alusta kappaleen "Remove a package" loppuun, poislukien "Configuration". (Kannatta soveltaa asennuksesta idempotentti versio, ulkomuistista: 'sudo salt-call --local -l info state.apply pkg.installed curl').
## a) Paketti Windowsia. Asenna Windowsiin tai Macciin ohjelmia Saltin pkg.installed -funktiolla. (Jos teit tarvittavat asennukset jo tunnilla, voit kirjoittaa ympäristön asennuksen ulkomuistista, ja asentaa nyt vain jonkin uuden paketin. Muistinvaraisesti kirjoitetut muistiinpanot ovat paljon epämääräisempiä kuin työn aikana kirjoitetut, joten merkitse selvästi, mitkä osat on kirjoitettu ulkomuistista ja mitkä työskennellessä.)
Kyseisen tehtävän kerkesin thedä jo tunnilla. Olin ladannut koneelleni Saltin jo aikaisemmin. Kokeilin toimiiko Saltin pkg.installed konellani. Käytin komento 'sudo salt-call --local 
state.single pkg.installed tree'. Komento latasi minulle onnistuneesti tree ohjelman. Seuraavaksi aloitin tekemään hello tilaa Saltilla. Tein kansioon '/tmp' uuden kansion 'mkdir salt'.
'/tmp/salt' loin uuden kansion nimeltä hello jonka sisään tein init.sls tiedoston. Init.sls tiedostoon tein alla olevan kuvan mukaisen sisällön. 

Seuraavaksi kokeilin ajaa Hello tilan komennolla 'sudo salt-call --local --file-root /tmp/salt state.apply hello'. Tila ajettiin onnistuneesti ja siitä on kuva alhaalla.

Nyt pääsin tekemään tilaa jolla saan ladattua eri paketteja. Tein kansioon '/tmp/salt' uuden kansion favourites ja kävin sen sisään tekemässä init.sls tiedoston johon lisäsin eri paketteja. 
Alla olevassa kuvassa näkyy favourites kansion init.sls tiedostosta kuva. 

Viimeiseksi tein top.sls tiedoston '/tmp/salt' kansioon. Top.sls tiedostoon lisäsin moelmmat favourites ja Hello joista löytyy init.sls tiedostot. Kokeilin ajaa komennon 
'sudo salt-call --local --file-root /tmp/salt state.apply' Jolloin top.sls tiedoston sisältö ajettiin. Paketit latautui onnistuneesti ja myös tiedosto löytyi, jonka olin määrittänyt Hello init.sls tiedostossa.

## b) Benchmark. Etsi 3-7 keskitetyn hallinnan projektia, esimerkiksi tämän kurssin "Oma moduli" lopputyötä. Työn tulee olla modernia keskitettyä hallintaa (idempotentti, infra koodina, yksi totuus). Esimerkiksi pelkkä shell script ei kelpaa. Työ saa käyttää mitä vain työkalua, esim Salt, Puppet, Ansible, Chef, Conftero, CFEngine. Tässä alakohdassa ei tehdä mitään testejä, vaan arvioidaan töitä vain niiden kotisivujen perusteella. Etsimiseen voit käyttää hakukoneita. Listaa kustakin
Tarkoitus (eli "mitä hyötyä tästä on" eli "business purpose" eli "miksi haluaisin asentaa tämän".)
Kyllä näin: (business purpose): "Robotti kuljettaa minulla jääkaapista limpparia"
Ei näin, tekniikoiden luetteleminen ei ole sovelluksen tarkoitus: "ESP32 ja Arduino ohjaavat servoja, jotka LIDAR:lla väistelevät kappaleita C++-ohjelmalla; tartuntakomponentti käyttää PDI-säädintä..."
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
1. https://sampohautala.wordpress.com/2018/12/09/ph-h7-oma-moduli/x
2. https://jannelinux.design.blog/2020/05/19/oma-moduuli-h7/x
3. https://koodiprojektit.wordpress.com/h7-oma-projekti/x
4. https://markuspyharanta.com/2016/12/10/palvelinten-hallinta-oma-moduuli/x
5. https://janni.tech.blog/2020/05/19/h7-oma-moduuli/
6. https://katrilaulajainen.wordpress.com/2018/05/10/palvelinten-hallinta-h6-8-5-2018-oma-miniprojekti-saltilla/x

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

Valitsin tehtävään moduliksi Katri Laulajaisen modulin, jossa tarkoituksena oli ladata kolme pakettia, firefox, gimp ja sshopen-server. Aloitin tehtävän tekemisen noudattamalla 
Laulajaisen ohjeita, mutta ensimmäinen ongelma tuli kun ajoin salt firefox-tilan. Jostain syytä sain alla näkyvässä kuvassa olevan virheilmoituksen. 
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
