# h7
####  Tekijä: Daniel Tarsalainen 10.10.2021

\
&nbsp;

# Tehtävänanto

- [x] a) Ratkaise valitsemasi vanha arvioitava laboratorioharjoitus tältä kurssilta. (Löytyy DuckDuckGolla, Googlella, linkeistä tältä sivulta tai hakemalla yläreunan hakutoiminnolla). Sovella tarvittaessa tehtäviä tähän toteutukseen sopivaksi, esimerkiksi PHP:n tilalta voi tehdä vastaavan Pythonilla; tai jättää pois jonkin epärelevantin kohdan<sup>1</sup>



### a) Ratkaise valitsemasi vanha arvioitava laboratorioharjoitus tältä kurssilta. (Löytyy DuckDuckGolla, Googlella, linkeistä tältä sivulta tai hakemalla yläreunan hakutoiminnolla). Sovella tarvittaessa tehtäviä tähän toteutukseen sopivaksi, esimerkiksi PHP:n tilalta voi tehdä vastaavan Pythonilla; tai jättää pois jonkin epärelevantin kohdan<sup>1</sup>

\
&nbsp;

### Linuxin asennus<sup>2</sup>

Ennen tehtävien tekemistä asensin uuden virtuaalikoneen 8.10.2021. Tein uuden virtuaalikoneen painamalla Oraclen VirtualBox Managerista sivun vasemmasta yläkulmasta näkyvästä Machine painikkeesta kohdan `new machine`. 

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

Kun asennus oli valmis, järjestelmä käynnistyi automaattisesti uudelleen ja pääsin syöttämään kirjautumistunnuksia. Sisällekirjauduttuani asensin vielä virtuaaliselle koneelle Guest Additions ominaisuudet. Sen tein avaamalla sovelluksen ylävasemmalla näkyvästä menu-valikosta Devices -> Insert Guest Additions CD image, jonka jälkeen menin komentorivillä järjestelmän juuressa VBox -kansioon komennolla `cd /media/daniel/VBox_GAs_6.1.26`, jossa ajoin laajennuspaketin komennolla `sudo bash VBoxLinuxAdditions.run`. Tämän jälkeen sammutin virtuaalisen koneen ja muutin General sivun asetuksia siten, että kopiointi on mahdollista virtuaalikoneelta päätietokoneelle ja toisinpäin. Tämän jälkeen käynnistin virtuaalisen koneen uudelleen, jonka jälkeen olin valmis suorittamaan laboratorio-harjoitusta.


\
&nbsp;


### Työntekijät<sup>3</sup>
##### Työntekijöitämme ovat Joe Doe, Jorma Mähkylä, Pekka Hurme, Ronaldo Smith, Håkan Petersson ja Einari Mikkonen. Laita einarin käyttäjätunnukseksi "einari". Tee kullekin käyttäjälle esimerkkikotisivu<sup>3</sup>

Käytin tehtävän teossa apuna vanhaa raporttiani<sup>4</sup>

Aloitin tehtävän teon tutulla `sudo apt-get update` -komennolla, jonka jälkeen asensin maailman suosituimman palvelimen, eli Apache2 -palvelimen komennolla `sudo apt-get install apache2`. Tämän jälkeen halusin heti korvata apache2 oletussivun tekstillä "Oletus". Käytin tähän komentoa: `echo "Oletus" | sudo tee /var/www/html/index.html`. Tämän jälkeen käynnistin Apachen palvelimen komennolla `sudo systemctl start apache2`, jonka jälkeen tulostin sivun sisällön komentorivillä komennolla `curl localhost`. Menin myös selaimeen, jonne sivu ilmestyi onnistuneesti näkyviin.

![kuva](https://user-images.githubusercontent.com/77921212/136690795-328604e0-c7c9-4f76-b603-e8033b72c4ab.png)

![kuva](https://user-images.githubusercontent.com/77921212/136690820-94058c2e-1c99-406b-8ed6-5fb41fb8429f.png)

Tämän jälkeen loin uuden käyttäjän nimeltä Einari Mikkonen. Käytin tähän komentoa `sudo adduser einari`. Annoin käyttäjälle vahvan salasanan. 

![kuva](https://user-images.githubusercontent.com/77921212/136691149-35d5e743-b244-471f-a7d1-4489f839b516.png)

Tämän jälkeen lisäsin itseni käyttäjän "einari" -ryhmään komennolla `sudo adduser $(whoami) einari`, jonka jälkeen loin einarin hakemistoon uuden kansion nimeltä `public_html` komennolla `sudo mkdir public_html`. Tämän jälkeen muutin kansion oikeuksia vielä siten, että ryhmästä ja käyttäjästä einari tulisi kansion omistaja. Käytin tähän komentoa `sudo chown einari:einari /home/einari/public_html`. Tämän jälkeen kirjauduin ulos käyttäjältä ja kirjauduin uudelleen sisään, jotta ryhmä "einari" aktivoituisi. Tämän jälkeen annoin vielä ryhmän jäsenille kirjoitus, luku ja ajo-oikeudet komennolla `sudo chmod g=rwxs /home/einari/public_html`. "s" -kirjain muistaakseni spesifioi, että oikeudet tulevat vain kyseiseen kansioon. Tämän jälkeen kokeilin luoda uutta tiedostoa public_html kansioon, mutta se ei onnistunut, joten päätin vielä kerran kirjautua ulos ja sisään. Tarkistin vielä ennen tiedoston luontia oikeudet, jotka olivat juuri niin kuin pitkin. 

![kuva](https://user-images.githubusercontent.com/77921212/136692634-3dfe7e40-11dd-409e-86b7-27d75e16a52d.png)

Tämän jälkeen loin uuden tiedoston nimeltä index.html, jonne kirjoitin sanan "Einari". Sitten käynnistin apache2-palvelimen uudestaan. `localhost/~einari` -sivulle ei ollut ilmestynyt vielä mitään, joten päättelin, että käyttäjähakemistoja ei ole vielä aktivoitu apache2 -palvelimen käyttöön. Siihen käytin komentoa `sudo a2enmod userdir`. Sitten vielä käynnistin palvelimen uudestaan komennolla `sudo sytemctl restart apache2`. 

![kuva](https://user-images.githubusercontent.com/77921212/136693288-517fd93f-f281-4651-9594-f694cf32614e.png)

Helpompaa olisi tietenkin ollut tehdä kansio ja sivu itse Einarin käyttäjällä, mutta ajattelin, että yrityksen toimitusjohtaja saattaisi hyvinkin tehdä samalla tavalla kuin minäkin, eli operoida omalta käyttäjältä käsin. 

\
&nbsp;

### LAMP<sup>3</sup>
##### Asenna LAMP - Linux, Apache, MySQL, PHP. Tee einarin kotihakemistoon esimerkkisovellus, joka näyttää tietueita tietokannasta<sup>3</sup>

Käytin tehtävässä apuna parin viikon takaista raporttiani<sup>5</sup>

Koska MySQL tietokantaa ja PHP:tä ei käytetty tunneilla niin päätin tehtävässä virkistää muistiani Python Flaskin ja WSGI moduulin käytöstä. Lähdin liikkeelle tehtävässä tekemällä uuden kansion einarin kotihakemistoon komennolla `sudo mkdir public_wsgi`. Heti tämän jälkeen muutin kansion omistajaksi einarin käyttäjän sekä einarin ryhmän `sudo chown einari:einari /home/einari/public_wsgi`. Tämän jälkeen lisäsin ryhmälle vielä tarvittavat oikeudet (luku, kirjoitus ja ajo-oikeudet) komennolla `sudo chmod g=rwxs /home/einari/public_wsgi`. Tämän jälkeen tarkistin vielä että tarvittavat oikeudet ilmestyivät kansioon:

```
daniel@daniel-virtualbox:/home/einari/public_wsgi$ ls -ld
drwxrwsr-x 2 einari einari 4096 10.10. 14:42 .

```

Tämän jälkeen asensin Python flaskin komennolla: `sudo apt-get -y install python3-flask` ja tämän jälkeen vielä wsgi-moduulin komennolla `sudo apt-get -y install libapache2-mod-wsgi-py3`. 

Sitten loin uuden wsgi-moduulin public_wsgi kansioon. Tähän käytin komentoa `nano einari.wsgi`. Tiedoston sisään tein tyypillisen wsgi rakenteeen

![kuva](https://user-images.githubusercontent.com/77921212/136697620-5ccf7f2c-c1a2-49c6-8ab6-adbac80fb6c6.png)

Tämän jälkeen tein uuden virtual hostin nimellä einari.conf. 

![kuva](https://user-images.githubusercontent.com/77921212/136698032-6f2aeaca-7003-418e-9226-e03935d7bb5b.png)

Sitten poistin vanhan apachen oletus virtualhost configuraatiot komennola `sudo a2dissite 000-default.conf` ja otin uudet käyttöön komennolla sudo `a2ensite einariwsgi.conf`. Tämän jälkeen käynnistin apachen uudellee, jotta uudet asetukset tulisi voimaan. Käytin komentoa `sudo systemctl restart apache2`. 

Tämän jälkeen lähdin luomaan Python ohjelman einarin kotihakemistoon komennolla `nano tervehdys.py`. Ohjelma sisällöstä tuli seuraavanlainen:

![kuva](https://user-images.githubusercontent.com/77921212/136698784-1da7ab06-c930-4036-a45e-ddcdf43f2de6.png)

Curlilla selvisi, että palvelimella tuli virhe 500, eli Internal Server Error. Selvisi, että olin nimennyt einari.wsgi -kansiossa polun väärin einari_wsgi:ksi, vaikka sen täytyi olla public_wsgi. Korjasin virheen ja päivitin ohjelman käyttämällä `touch einari.wsgi` -komentoa, jolloin itse palvelinta ei tarvinnut käynnistää uudelleen. Tämän jälkeen curlilla saatiin tulostettua haluttu lopputulos:

```
daniel@daniel-virtualbox:/home/einari/public_wsgi$ curl localhost 
Welcome to Einari Mikkonen's site! :)
```

Selaimessa näkymä oli seuraava:

![kuva](https://user-images.githubusercontent.com/77921212/136698923-21c50350-ce4b-4f5d-a048-11a23d3d022f.png)

\
&nbsp;


### invis.example.com<sup>3</sup>
##### Laita Einarin esimerkkisovellus näkymään osoitteesta http://invis.example.com. Voit simuloida nimipalvelun toimintaa hosts-tiedoston avulla<sup>3</sup>

Menin järjestelmän juuresta hosts kansioon `sudoedit /etc/hosts`, jossa vaihdoin localhostin nimeksi `http://invis.example.com` seuraavanlaisesti. `127.0.0.1` siis vastaa paikallista palvelimen ip-osoitetta:

![kuva](https://user-images.githubusercontent.com/77921212/136701347-79808c69-0ec2-454d-9b04-db7a4d2de643.png)


Tämän jälkeen muutin vielä einari.conf tiedoston ServerName kohtaa vastaamaaan sivun uutta nimeä: `invis.example.com`

![kuva](https://user-images.githubusercontent.com/77921212/136701301-44c4fd6b-3967-4e9c-b6e4-71cd8fae68fa.png)


Sitten käynnistin vielä lopuksi palvelimen uudestaan `sudo systemctl restart apache2`. Uusi simuloitu nimi tuli onnistuneesti näkyviin:

![kuva](https://user-images.githubusercontent.com/77921212/136702008-df3b9804-8fd2-4d63-ab09-d437e4be71dc.png)


\
&nbsp;


### mitakello<sup>3</sup>
##### Tee uusi komento 'mitakello', joka tulostaa kellonajan. Komennon tulee toimia kaikilla käyttäjillä, kaikista hakemistoista pelkällä nimellä kutsuttuna<sup>3</sup>

Käytin tehtävässä apuna viime viikolla tehtyä raporttia<sup>6</sup>

Lähdin tekemään tehtävää luomalla uuden kansion käyttäjän "daniel" kotihakemistoon komennolla `mkdir skriptit`. Kansion sisään tein uuden tiedoston komennolla `nano mitakello`.

![kuva](https://user-images.githubusercontent.com/77921212/136702312-c0d4aff6-13c4-42e2-9a8a-04f111007471.png)

Ensimmäinen rivi määrittää, että bashia käytetään skriptin tulkkina. Kolmannella rivillä määritetään date olio, ja echon kohdalla se tulostetaan tekstin kanssa ja tietyn formaatin mukaisesti. 

![kuva](https://user-images.githubusercontent.com/77921212/136702483-93eb512e-1479-4c5b-943a-aaba02876e6b.png)

Kokeilin ajaa skriptin komennolla `bash mitakello`:

```
daniel@daniel-virtualbox:~/skriptit$ bash mitakello
Show time: 18:30:58
```

Tämän jälkeen muutin, että kaikilla on oikeus skriptin ajamiseen. Käytin tähän komentoa `chmod ugo+x mitakello`. Oikeudet päivittyivät onnistuneesti:

```
daniel@daniel-virtualbox:~/skriptit$ ls -ld mitakello
-rwxr-xr-x 1 daniel daniel 65 10.10. 18:30 mitakello

```

Lopuksi vielä kopioin tiedston `/ust/local/bin` hakemistoon, mikä mahdollistaa sen, että skriptin voi ajaa mistä tahansa sijainnista komentoriviltä. Tein sen komennolla `sudo cp -v mitakello /usr/local/bin`. Kopiointi oli onnistunut.

```
daniel@daniel-virtualbox:~/skriptit$ sudo cp -v mitakello /usr/local/bin
[sudo] password for daniel: 
'mitakello' -> '/usr/local/bin/mitakello'
```

Tämän jälkeen ajoin skriptin einarin kotihakemistosta:

```
daniel@daniel-virtualbox:/home/einari$ bash mitakello
Show time: 18:37:45
```


\
&nbsp;


### unikarhu.example.com<sup>3</sup>
##### Laita staattinen html5-esimerkkisivu näkyviin osoitteeseen http://unikarhu.example.com. Voit simuloida nimipalvelun toimintaa hosts-tiedoston avulla<sup>3</sup>

Käytin tehtävän teossa Teron ohjetta muistin virkistykseksi<sup>7</sup>

Lähdin tekemään danielin kotihakemistoon uudet kansiot nimeltä public_sites ja sen sisään unikarhu.com. unikarhu.com kansioon tein uuden html tiedoston nimeltä index.html. Tiedoston sisältö oli seuraavanlainen:

![kuva](https://user-images.githubusercontent.com/77921212/136703325-392a55b5-13ad-4097-94bc-a8ad0b766801.png)

Sitten menin luomaan uuden config tiedoston komennolla `sudoedit /etc/apache2/sites-available/unikarhu.com.conf`.
Sisällöstä tuli seuraavanlainen:

![kuva](https://user-images.githubusercontent.com/77921212/136706037-3fa32a6c-35e6-49a7-8ba1-352ead38df49.png)

Tämän jälkeen otin VirtualHostin käyttöön komennolla `sudo a2ensite unikarhu.com.conf` ja otin vanhan virtualhostin pois käytöstä komennolla `sudo a2disste einariwsgi.conf`.

Lopuksi menin vielä `etc hosts` -kansioon, jonne lisäsin testipavelimen kohdalle `unikarhu.example.com` sivun. 

![kuva](https://user-images.githubusercontent.com/77921212/136705691-e97e148a-bfe9-4dd1-bbb8-658e3b37741d.png)

Sitten käynnistin palvelimen uudestaan komennolla `sudo systemctl restart apache2`.

Sivu tuli onnistuneesti näkyviin

![kuva](https://user-images.githubusercontent.com/77921212/136706058-3295c227-c440-4828-8574-5d0a0982f175.png)

\
&nbsp;

## Loppumietteitä

Tehtävät olivat mukavaa kertausta. Tuntuu, että osaamiseni vahvistui paremmaksi kertauksen myötä. Aikaa tehtäviin kului noin seitsemän tuntia. Tein tehtäviä sekä 8.10.2021, että 10.10.2021.

\
&nbsp;

## Lähteet


| Lähdenumero | Linkki |
| ----------- | ------------------------------------------------------------------------- |
| 1 | https://terokarvinen.com/2021/linux-server-course-linux-palvelimet-ict4tn021-3016/#peruskaytto                           |
| 2 | https://terokarvinen.com/2021/install-debian-on-virtualbox/|
| 3 | https://terokarvinen.com/2018/arvioitava-laboratorioharjoitus-linux-palvelimet-ict4tn021-7-tiistai-alkukevat-2018-5-op/?fromSearch=laboratori                  |
| 4 | https://github.com/DanielTarsalainen/Linux-palvelimet/blob/main/viikko3.md               |
| 5 | https://github.com/DanielTarsalainen/Linux-palvelimet/blob/main/viikko5.md|
| 6 | https://github.com/DanielTarsalainen/Linux-palvelimet/blob/main/viikko6.md|
| 7 | https://terokarvinen.com/2018/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/|



