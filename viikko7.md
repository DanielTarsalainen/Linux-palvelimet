# h7
####  Tekijä: Daniel Tarsalainen 10.10.2021

\
&nbsp;

# Tehtävänanto

- [ ] a) Ratkaise valitsemasi vanha arvioitava laboratorioharjoitus tältä kurssilta. (Löytyy DuckDuckGolla, Googlella, linkeistä tältä sivulta tai hakemalla yläreunan hakutoiminnolla). Sovella tarvittaessa tehtäviä tähän toteutukseen sopivaksi, esimerkiksi PHP:n tilalta voi tehdä vastaavan Pythonilla; tai jättää pois jonkin epärelevantin kohdan<sup>1</sup>
- [ ] b) Tarkista, että olet viitannut jokaisessa tehtävässä kaikkiin lähteisiin. Esimerkiksi kurssiin, tehtävänantoihin, käyttämiisi toisten kotitehtävärapotteihin, manuaalisivuihin, kotisivuihin<sup>1</sup>
- [ ] c) Kaikki tehtävät arvioitavaksi. Palauta linkki sivuun, josta löytyvät kaikki kotitehtäväraporttisi. Arviointi tehdään ensisijaisesti tästä linkistä. Linkki voi olla esimerkiksi blogin etusivu (jos blogissa on vain kotitehtävät) tai sivuun, jossa on linkki kuhunkin tehtävään. Kaikki tehtävät -linkin palautus Moodlessa kohtaan "Kaikki tehtävät arvioitavaksi"<sup>1</sup>
- [ ] d) Tee uusi tyhjä virtuaalikone viimeisen kerran arvioitavaa labraa varten. Koneella ei saa olla luottamuksellisia tietoja. Kannattaa tehdä koneelle tarpeeksi iso virtuaalinen levy. Guest additions saa olla asennettuna<sup>1</sup>


\
&nbsp;

## a) Ratkaise valitsemasi vanha arvioitava laboratorioharjoitus tältä kurssilta. (Löytyy DuckDuckGolla, Googlella, linkeistä tältä sivulta tai hakemalla yläreunan hakutoiminnolla). Sovella tarvittaessa tehtäviä tähän toteutukseen sopivaksi, esimerkiksi PHP:n tilalta voi tehdä vastaavan Pythonilla; tai jättää pois jonkin epärelevantin kohdan<sup>1</sup>

### Linuxin asennus

Aloitin tehtävän teon asentamalla uuden virtuaalikoneen 8.10.2021 . Tein uuden virtuaalikoneen painamalla Oraclen VirtualBox Managerista sivun vasemmasta yläkulmasta näkyvästä Machine painikkeesta kohdan `new machine`. 

Tämän jälkeen avautui modaali-ikkuna näytön keskelle, johon laitoin nimeksi `daniel2` ja käyttöjärjestelmäksi ja versioksi `Debian (64-bit)`. Tämän jälkeen painoin `next` -painiketta, jonka jälkeen avautui uusi ikkuna, jossa kysyttiin välimuistin määrää. Laitoin määräksi 4000 megatavua. 

![kuva](https://user-images.githubusercontent.com/77921212/136552123-ac2a1a5c-5fb5-46c2-8211-0d8713423fa4.png)

Sitten jatkoin jälleen `next` -painikkeella eteenpäin. Seuraavaksi valitsin `Create a virtual hard disk now` ja valitsin kovalevyn tyypiksi `VDI (VirtualBox Disk Image)` ja valitsin, että virtuaalinen kovalevy ottaa tilaa niin paljon kuin tarvitsee (`Dynamically allocated`). Seuraavaksi asetin virtuaalisen kovalevyn kapasiteetiksi 40 gigatavua ja painoin lopuksi `create` -painiketta. Uusi virtuaalinen kone ilmestyi Oracle VM VirtualBox Managerin etusivulle. 

![kuva](https://user-images.githubusercontent.com/77921212/136553114-54ffdf52-d25f-43b5-9583-113ac357ae27.png)

Ennen käynnistystä valitsin vielä Controller IDE -kohtaan virtuaalisen iso-levyn, jolla saa debianin asennuspaketin ja Debianin oletustyöpöydän näkyviin. Tämän jälkeen painoin ok-painiketta.

![kuva](https://user-images.githubusercontent.com/77921212/136554009-634b568a-a6c8-4ba0-9f2a-d0802c94fa31.png)

Tämän jälkeen käynnistin virtuaalisen koneen viherästä `Start` -painikkeesta. 

Valitsin debian 11 etusivulta `Debian GNU/Linux Live (kernel 5.10.0-8-amd64)` ja painoin entteriä

Noin kahden minuutin päästä Debianin työpöytä ilmestyi esiin. 

![kuva](https://user-images.githubusercontent.com/77921212/136554995-b44a2c16-5c4c-47e1-ae25-359c736197fc.png)

Seuraavaksi lähdin asentamaan Debiania virtuaaliselle koneelle. Valitsin kieleksi `American English` ja alueeksi `Europe`, sekä vyöhykkeeksi `Helsinki`. Näppäimistöasetteluksi asetin `Finnish`. Tämän jälkeen valitsin, että Virtuaalinen kovalevy alustetaan ja siihen asennetaan Debian. Lopuksi täytin tarvittavat tiedot Debian käyttäjän luomiseksi. Varmistin myös, että käyttämäni salasana on vahva.

![kuva](https://user-images.githubusercontent.com/77921212/136556155-19139e50-3fdc-4280-a37c-2d43ea76395c.png)

Sitten vihdoin ja viimein lähdin asentamaan debiania 

![kuva](https://user-images.githubusercontent.com/77921212/136556553-99ef9eee-cea1-4ef9-b78a-9c25ecaf50f3.png)

Kun asennus oli valmis, järjestelmä käynnistyi automaattisesti uudelleen ja pääsin syöttämään kirjautumistunnuksia. Sisällekirjauduttuani asensin vielä virtuaaliselle koneelle Guest Additions ominaisuudet. Sen tein avaamalla sovelluksen ylävasemmalla näkyvästä menu-valikosta Devices -> Insert Guest Additions CD image, jonka jälkeen menin komentorivillä järjestelmän juuressa VBox -kansioon komennolla `cd /media/daniel/VBox_GAs_6.1.26`, jossa ajoin laajennuspaketin komennolla `sudo bash VBoxLinuxAdditions.run`. Tämän jälkeen sammutin virtuaalisen koneen ja muutin General sivun asetuksia siten, että kopiointi on virtuaalikoneelta päätietokoneelle ja toisinpäin. Tämän jälkeen käynnistin virtuaalisen koneen uudelleen, jonka jälkeen olin valmis suorittamaan laboratorio-harjoitusta.


\
&nbsp;


### Työntekijät
##### Työntekijöitämme ovat Joe Doe, Jorma Mähkylä, Pekka Hurme, Ronaldo Smith, Håkan Petersson ja Einari Mikkonen. Laita einarin käyttäjätunnukseksi "einari". Tee kullekin käyttäjälle esimerkkikotisivu.

Aloitin tehtävän teon tutulla `sudo apt-get update` -komennolla, jonka jälkeen asensin maailman suosituimman palvelimen, eli Apache2 -palvelimen komennolla `sudo apt-get install apache2`. Tämän jälkeen halusin heti korvata apache2 oletussivun tekstillä "Oletus". Käytin tähän komentoa: `echo "Oletus" | sudo tee /var/www/html/index.html`. Tämän jälkeen käynnistin Apachen palvelimen komennolla `sudo systemctl start apache2`, jonka jälkeen tulostin sivun sisällön komentorivillä komennolla `curl localhost`. Menin myös selaimeen, jonne sivu ilmestyi onnistuneesti näkyviin.

![kuva](https://user-images.githubusercontent.com/77921212/136690795-328604e0-c7c9-4f76-b603-e8033b72c4ab.png)

![kuva](https://user-images.githubusercontent.com/77921212/136690820-94058c2e-1c99-406b-8ed6-5fb41fb8429f.png)

Tämän jälkeen loin uuden käyttäjän nimeltä Einari Mikkonen. Käytin tähän komentoa `sudo adduser einari`. Annoin käyttäjälle vahvan sanan. 

![kuva](https://user-images.githubusercontent.com/77921212/136691149-35d5e743-b244-471f-a7d1-4489f839b516.png)

Tämän jälkeen lissäin itseni käyttäjän "einari" -ryhmään komennolla `sudo adduser $(whoami) einari`, jonka jälkeen loin einarin hakemistoon uuden kansion nimeltä `public_html` komennolla `sudo mkdir public_html`. Tämän jälkeen muutin kansion oikeuksia vielä siten, että ryhmästä ja  käyttäjästä einari tulisi kansion omistaja. Käytin tähän komentoa `sudo chown einari:einari /home/einari/public_html`. Tämän jälkeen kirjauduin ulos käyttäjältä ja kirjauduin uudelleen sisään, jotta ryhmä "einari" aktivoituisi. Tämän jälkeen annoin vielä ryhmän jäsenille kirjoitus, luku ja ajo-oikeudet komennolla `sudo chmod g=rwxs /home/einari/public_html`. "s" -kirjain muistaakseni spesifioi, että oikeudet tulevat vain kyseiseen kansioon. Tämän jälkeen kokeilin luoda uutta kansiota public_html kansioon, mutta se ei onnistunut, joten päätin vielä kerran kirjautua ulos ja sisään. Tarkistin vielä ennen tiedoston luontia oikeudet, jotka olivat juuri niin kuin pitkin. 

![kuva](https://user-images.githubusercontent.com/77921212/136692634-3dfe7e40-11dd-409e-86b7-27d75e16a52d.png)

Tämän jälkeen loin uuden tiedoston nimeltä index.html, jonne kirjoitin sanan "Einari". Sitten käynnistin apache2-palvelimen uudestaan. `localhost/~einari` -sivulle ei ollut ilmestynyt vielä mitään, joten päättelin, että käyttäjähakemistoja ei ole vielä aktivoitu apache2 -palvelimen käyttöön. Siihen käytin komentoa `sudo a2enmod userdir`. Sitten vielä käynnistin palvelimen uudestaan komennolla `sudo sytemctl restart apache2`. 


![kuva](https://user-images.githubusercontent.com/77921212/136693288-517fd93f-f281-4651-9594-f694cf32614e.png)

Helpompaa olisi ollut tehdä kansio ja sivu itse einarin käyttäjällä, mutta ajattelin, että yrityksen toimitusjohtaja saattaisi hyvinkin tehdä samalla tavalla kuin minäkin, eli operoida omalta käyttäjältä käsin. 



\
&nbsp;

### LAMP
##### Asenna LAMP - Linux, Apache, MySQL, PHP. Tee einarin kotihakemistoon esimerkkisovellus, joka näyttää tietueita tietokannasta.

Koska MySQL tietokantaa ja PHP:tä ei käytetty tunneilla niin päätin tehtävässä virkistää muistiani Python Flaskin ja WSGI moduulin käytöstä. Lähdin liikkeelle tehtävässä tekemällä uuden kansion einarin kotihakemistoon komennolla `sudo mkdir public_wsgi`. Heti tämän jälkeen muutin kansion omistjaksi einarin ryhmän `sudo chown einari:einari /home/einari/public_wsgi`. Tämän jälkeen lisäsin ryhmälle vielä tarvittavat oikeudet komennolla `sudo chmod g=rwxs /home/einari/public_wsgi`. Tämän jälkeen tarkistin vielä että tarvittavat oikeudet ilmestyivät kansioon:

```
daniel@daniel-virtualbox:/home/einari/public_wsgi$ ls -ld
drwxrwsr-x 2 einari einari 4096 10.10. 14:42 .

```

Tämän jälkeen asensin Python flaskin komennolla: `sudo apt-get -y install python3-flask` ja tämän jälkeen vielä wsgi-moduulin komennolla `sudo apt-get -y install libapache2-mod-wsgi-py3`. 

Sitten loin uuden wsgi-moduulin public_wsgi kansioon. Tähän käytin komentoa `nano einari.wsgi`. Tiedoston sisään tein tyypillisen wsgi rakenteeen

![kuva](https://user-images.githubusercontent.com/77921212/136694650-1e77625f-e1f6-452b-871d-4dcde9a60a55.png)




\
&nbsp;


### invis.example.com
##### Laita Einarin esimerkkisovellus näkymään osoitteesta http://invis.example.com. Voit simuloida nimipalvelun toimintaa hosts-tiedoston avulla.

\
&nbsp;


### mitakello
##### Tee uusi komento 'mitakello', joka tulostaa kellonajan. Komennon tulee toimia kaikilla käyttäjillä, kaikista hakemistoista pelkällä nimellä kutsuttuna.

\
&nbsp;


### Metapaketti
##### Tee meille metapaketti, joka asentaa ohjelmat: git, httpie, curl, mitmproxy. Kuulemma "karvinen equivs" hakusanalla saattaisi löytyä ohjeita. Liitä metapaketin lähdekoodi palautettavan lab.txt:n loppuun.

\
&nbsp;

### unikarhu.example.com
##### Laita staattinen html5-esimerkkisivu näkyviin osoitteeseen http://unikarhu.example.com. Voit simuloida nimipalvelun toimintaa hosts-tiedoston avulla.

\
&nbsp;

### bonuskuorma 
##### Mittaa koneesi kuormitusta työkalulla, joka kerää kuormitustietoja yli ajan (ei pelkästään yhdellä hetkellä). Kuormita konetta haluamallasi tavalla, ja etsi kuormitustieto työkalusi keräämästä historiasta.


\
&nbsp;

### Metapaketin uusi nimi
##### Muuta metapaketin nimeksi xoy-tools. Asenna se.


\
&nbsp;

## b) Tarkista, että olet viitannut jokaisessa tehtävässä kaikkiin lähteisiin. Esimerkiksi kurssiin, tehtävänantoihin, käyttämiisi toisten kotitehtävärapotteihin, manuaalisivuihin, kotisivuihin<sup>1</sup>


\
&nbsp;

## c) Kaikki tehtävät arvioitavaksi. Palauta linkki sivuun, josta löytyvät kaikki kotitehtäväraporttisi. Arviointi tehdään ensisijaisesti tästä linkistä. Linkki voi olla esimerkiksi blogin etusivu (jos blogissa on vain kotitehtävät) tai sivuun, jossa on linkki kuhunkin tehtävään. Kaikki tehtävät -linkin palautus Moodlessa kohtaan "Kaikki tehtävät arvioitavaksi"<sup>1</sup>

\
&nbsp;

## d) Tee uusi tyhjä virtuaalikone viimeisen kerran arvioitavaa labraa varten. Koneella ei saa olla luottamuksellisia tietoja. Kannattaa tehdä koneelle tarpeeksi iso virtuaalinen levy. Guest additions saa olla asennettuna<sup>1</sup>


\
&nbsp;

## Lähteet


| Lähdenumero | Linkki |
| ----------- | ------------------------------------------------------------------------- |
| 1 | https://terokarvinen.com/2021/linux-server-course-linux-palvelimet-ict4tn021-3016/#peruskaytto                           |
| 2 |                           |
| 3 |  |



