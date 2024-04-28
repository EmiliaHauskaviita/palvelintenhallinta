# h5 Tekniikoita

## x) Lue ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.) Vapaavalintainen aiemman vuoden kotitehtäväraportti Saltin käytöstä Windowsilla. Löydät raportteja esimerkiksi Google tai Duck-haulla: salt windows karvinen.

Kävin lukemassa Johan Lindell kotitehtäväraportin Saltin käytöstä Windowsilla https://johanlindell.fi/palvelintenhallinta#h1. Tehtäviä oli mielestäni hauska katsoa, sillä 
itsekin ymmärsin mitä niissä tehdään ja miksi. 

## a) Asenna Salt Windowsille tai Macille. Osoita 'salt-call --local' komentoa ajamalla, että asennus on onnistunut. (Jos olet asentanut jo aiemmin, tässä riittää pelkkä asennuksen testaaminen, eikä asennusta tarvitse tehdä uudelleen.)

Olen ladannut Salt jo aikaisemmin Macille. Saltin lataamiseen minun täytyi Macille ensin ladata Salt lataustiedosto macOS käyttöjärjestelmälle. Löysin ohjeet
Salt lataamiseen Saltproject sivulta linkki tähän löytyy lähteistä. Kokeilin komennolla sudo salt-call --local, että asennus on onnistunut. Tulos näkyy
Alta löytyvästä kuvasta.
  
<img width="618" alt="Näyttökuva 2024-4-26 kello 11 04 32" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/5cb27c91-ba18-4413-bd0d-c882d9ba0cd0">
<img width="532" alt="Näyttökuva 2024-4-26 kello 11 12 04" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/d5a4168f-b9ad-40d5-97bb-766e802584ea">


## b) Kerää Windows- tai Mac-koneesta tietoa grains.items -toiminnolla. Poimi 'grains.item' perään muutamia keskeisiä tietoja ja analysoi ne, eli selitä perusteellisesti mitä ne ovat. Kuvaile ja vertaile numeroita.

Komennolla 'sudo salt-call --local grains.items |less' pääsin katsomaan tietoja koneestani. less komennolla tiedot tulevat näytölle alla olevan kuvan näköisesti ja eteenpäin
pääsen liikkumaan space näppäimellä ja taaksepäin b. 
<img width="419" alt="Näyttökuva 2024-4-26 kello 11 19 25" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/703db188-ab07-4a23-af61-4bf5e438620e">
Käytin komentoa sudo salt-call --local grains.item (haluttu tieto). Tällä saadaan tieto vain kyseisestä halutusta asiasta eikä tarvitse erikseen etsiä sitä 
kaikkien tietojen seasta esimerkiksi jos haluan tietää ipv4 osoitteeni kirjoitan komennon 'sudo salt-call --local grains.item ipv4'. Tällöin saan esiin vain ipv4 kohdan. 

Alla olevassa kuvassa olen antanut komennon 'sudo salt-call --local grains.item ipv4' ja vastauksena sain ipv4 osoitteeni tiedot.
<img width="576" alt="Näyttökuva 2024-4-26 kello 11 22 38" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/4c8f5973-97cf-43c0-9608-10d1c5d1c651">

Toinen komento jonka annoin oli 'sudo salt-call --local grains.item kernelversion' tästä sain vastaukseksi tiedon oman koneeni kernel versiosta. Alla 
on kuva tästä. Kernel tarkoitetaan käyttöjärjestelmän ydintä. 
<img width="806" alt="Näyttökuva 2024-4-26 kello 11 23 29" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/05a657db-49b3-4d0d-9ea4-a62f2fb5e02c">

Seuraavassa alla olevassa kuvassa olen poiminut tiedon koneeni cpu mallista komennolla 'sudo salt-call --local grains.item cpu_model.
<img width="628" alt="Näyttökuva 2024-4-26 kello 11 24 56" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/abdd296d-7d0b-4568-8120-9fcce72afe14">

Viimeisenä tietona poimin koneeseeni lataaman saltin verison komennolla 'sudo salt-call --local grains.item saltversion'.
<img width="644" alt="Näyttökuva 2024-4-26 kello 11 25 20" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/fd985e7f-2900-4878-873c-f53c5b1e96d5">


## c) Kokeile Saltin file -toimintoa Windowsilla tai Macilla.
Käytin komentoa 'sudo salt-call --local state.single file.managed /tmp/hello' eli kun ajan tämän komennon kone tarkistaa minulta löytyykö hello niminen tiedosto jo
tmp kansiosta ja jos ei niin se luodaan mutta jos se on jo olemassa sitä ei luoda uudelleen. Alla olevassa kuvassa näkyy, että succeeded 1 ja changed 1 eli
tällöin minulla ei ennestään ollut tiedostoa tehtynä joten se luotiin. Kävin vielä tmp kansiossa tarkistamassa että hello tiedosto oli varmasti tullut sinne.
<img width="887" alt="Näyttökuva 2024-4-27 kello 12 05 45" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/c21d5030-5ca2-41fa-80b8-010c50618e75">
<img width="690" alt="Näyttökuva 2024-4-27 kello 12 05 59" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/d2e425b6-54c0-4724-b0ce-f403f3c4f6d7">


## d) CSI Kerava. Näytä 'find' avulla viimeisimmäksi muokatut tiedostot /etc/-hakemistosta ja kotihakemistostasi. Selitä kaikki käyttämäsi parametrit ja format string 'man find' avulla.
Katsoin ensin komennolla man find, miten find komentoa voi käyttää ja siitä tuli aika paljon tietoa. Käytin apuna myös Tero Karvisen "Apache User Homepages Automatically – Salt Package-File-Service Example" 
artikkelia. Päädyin käyttämään komentoa 'sudo find /etc $HOME -printf '%T+ %p\n' | sort -n | tail -10'. Alla näkyy kuva tuloksesta. 

<img width="573" alt="Näyttökuva 2024-4-28 kello 15 02 02" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/89d61f6a-c480-4962-a313-25275289ee0f">

/etc ja $HOME ovat tarkasteltavia hakemistoja. Tulostusta tarkoittaa -printf. '%T+ %p\n' ovat %T= päivämäärä muokkaukselle, %p=tiedoston nimi ja polku, \n=uusi rivi. 
sort -n kertoo meille järjestys tavan eli n tarkoittaa uudempaa newer. tail -10 kertoo että näytetään vain 10 uusinta.  

## e) Komennus. Tee Salt-tila, joka asentaa järjestelmään uuden komennon.
Tehtävään sain apua verkosta (hellu.home.blog). Käytin scriptin luomiseen omia muistiinpanojani Haaga-Helian Linux-palvelimet kurssilta. Tehtävän aloitin luomalla
uuden komentotiedoston 'Heiohjelma' kansioon '/usr/local/bin'. Komentotiedostoon kirjoitin haluamani scriptin. Tarkoituksena oli siis että kun anna komennon 'Heiohjelma' 
saan vastaukseksi "Hei oma ohjelma!". Komentotiedoston luomisen jälkeen vaihdoin komennolla 'sudo chmod 755 /usr/local/bin/Heiohjelma' tiedoston oikeudet.
Kahdessa alla olevassa kuvassa on kuvat kansiosta ja luodusta komentotiedostosta, sekä scriptistä.

<img width="575" alt="Näyttökuva 2024-4-28 kello 14 48 56" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/fd999af3-0c24-446f-aa9a-31e8e8236e11">
<img width="525" alt="Näyttökuva 2024-4-28 kello 14 53 48" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/98041297-3aad-4bb3-912a-f60da81292a3">

Alla on kuva joss aolen kokeillut, että tekemäni scripti toimii komennolla 'Heiohjelma'.

<img width="316" alt="Näyttökuva 2024-4-28 kello 14 54 23" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/7485dbec-bc41-46e4-9e97-3efedef58972">

Kun olin kokeillut scriptin toimivuuden siirryin seuraavaksi saltin pariin. Menin luomaani '/srv/salt' kansioon johon loin uuden kansion nimeltä 'ohjelma'.
'ohjelma' kansion sisälle kopioin komentotiedoston komennolla 'cp /usr/local/bin/Heiohjelma /srv/salt/ohjelma'. Loin ohjelma kansioon myös uuden init.sls tiedoston.
init.sls tiedoston sisältö on alla olevassa kuvassa. Alla on myös kuva miltä 'ohjelma' kansio näyttää. Tiedostossa init.sls source kohta kertoo meille, mistä 
tiedosto 'Heiohjelma' löytyy ja mode kohta kertoo tiexoston oikeudet. 

<img width="423" alt="Näyttökuva 2024-4-28 kello 14 57 40" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/3f772a82-dc06-47a5-9ab9-4aa740deeeb7">
<img width="361" alt="Näyttökuva 2024-4-28 kello 14 57 51" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/06c67316-4172-4de9-b6cc-31088f8da186">

Seuraavaksi vuorossa oli testaaminen ja ajoin salt-tilan paikallisesti. Käytin komentoa 'sudo salt-call --local state.apply ohjelma' ja tästä sain vastaukseksi 
succeeded 1. Tuloksesta on alla kuva. 

<img width="566" alt="Näyttökuva 2024-4-28 kello 14 59 47" src="https://github.com/EmiliaHauskaviita/palvelintenhallinta/assets/165004928/eb939723-892a-453a-b1ad-418b60ceb2f1">



## Lähteet:
Saltproject, Salt install quide: https://docs.saltproject.io/salt/install-guide/en/latest/topics/install-by-operating-system/macos.html#

Karvinen, T, h5 Tekniikoita, 2024: https://terokarvinen.com/2024/configuration-management-2024-spring/#h5-tekniikoita

hellu, 5. Uusi komento, 2020: https://hellu.home.blog/2020/11/30/5-uusi-komento/

Lindell, J: https://johanlindell.fi/palvelintenhallinta#h1

Karvinen, T, Apache User Homepages Automatically – Salt Package-File-Service Example, 2018: https://terokarvinen.com/2018/apache-user-homepages-automatically-salt-package-file-service-example/
