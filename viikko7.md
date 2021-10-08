# h7
####  Tekijä: Daniel Tarsalainen 

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

### Työntekijät
##### Työntekijöitämme ovat Joe Doe, Jorma Mähkylä, Pekka Hurme, Ronaldo Smith, Håkan Petersson ja Einari Mikkonen. Laita einarin käyttäjätunnukseksi "einari". Tee kullekin käyttäjälle esimerkkikotisivu.

Aloitin tehtävän teon asentamalla uuden virtuaalikoneen. Tein uuden virtuaalikoneen painamalla Oraclen VirtualBox Managerista sivun vasemmasta yläkulmasta näkyvästä Machine painikkeesta kohdan `new machine`. 

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

Kun asennus oli valmis, järjestelmä käynnistyi automaattisesti uudelleen ja pääsin syöttämään kirjautumistunnuksia. Sisällekirjauduttuani asensin vielä virtuaaliselle koneelle Guest Additions ominaisuudet. Sen tein avaamalla sovelluksen ylävasemmalla näkyvästä menu-valikosta Devices -> Insert Guest Additions CD image, jonka jälkeen menin komentorivillä järjestelmän juuressa 
``` 
$ cd /media/daniel/VBox_GAs_6.1.26
``` 
VBox -kansioon, jossa ajoin laajennuspaketin komennolla  ```$ sudo bash VBoxLinuxAdditions.run```. Tämän jälkeen sammutin virtuaalisen koneen ja muutin General sivun asetuksia siten, että kopiointi on virtuaalikoneelta päätietokoneelle ja toisinpäin. Tämän jälkeen käynnistin virtuaalisen koneen uudelleen ja ryhdyin viimein suorittamaan laboratorio-harjoitusta.





\
&nbsp;

### LAMP
##### Asenna LAMP - Linux, Apache, MySQL, PHP. Tee einarin kotihakemistoon esimerkkisovellus, joka näyttää tietueita tietokannasta.

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



