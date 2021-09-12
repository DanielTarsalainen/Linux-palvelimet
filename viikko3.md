# Linux-palvelimet h3 tehtävät.
####  Tekijä: Daniel Tarsalainen 

\
&nbsp;

## Tehtävänanto:

- [x] a) Asenna Apache, laita käyttäjien kotisivut (http://example.com/~tero) toimimaan. Testaa esimerkkikotisivulla.<sup>1</sup>
- [x] b) Surffaa oman palvelimesi weppisivuja. Etsi Apachen lokista esimerkki onnistuneesta (200 ok) sivulatauksesta ja epäonnistuneesta (esim 404 not found) sivulatauksesta. Analysoi rivit.<sup>1</sup>
- [x] d) Tee virhe johonkin Apachen asetustiedostoon, etsi ja analysoi tuo rivi. Etsimiseen sopivat esimerkiksi Apachen omat lokit, syslog sekä ‘apache2ctl configtest’.<sup>1</sup>
- [x] i) Kuinka monta eri HTTP Status:ta (200, 404, 500…) saat aiheutettua lokeihin? Selitä, miten aiheutit tilanteet ja analysoi yksi rivi kustakin statuksesta.<sup>1</sup>
- [x] m) Vaihda Apachen oletussivu. Eli laita palvelimen etusivulla (ilman tildeä) näkyvä sivu niin, että alkuperäinen on jonkun käyttäjän kotihakemistossa ja voit muokata sitä ilman pääkäyttäjän oikeuksia.<sup>1</sup>

\
&nbsp;


### a) Asenna Apache, laita käyttäjien kotisivut (http://example.com/~tero) toimimaan. Testaa esimerkkikotisivulla.*

*Aloitin palvelimen asennuksen kirjoittamalla `sudo apt-get update komennon`, jolla   päivitin saatavilla olevat paketit. Seuraavaksi tein `sudo apt-get install apache2` -komennon, jolla sain apache palvelimen asennettua virtuaalikoneelle. Sitten testasin apache2 -palvelimen toimivuuden tekemällä komennon `sudo systemctl start apache2`. `curl localhost` -komennolla sain komentoriville näkyviin apache2 -palvelimen oletussivun sisällön komentoriville. Alla kuva tulostuksesta.*

![kuva](https://user-images.githubusercontent.com/77921212/132941775-c5cb3824-7653-4140-af6e-af5d40370085.png)


*Seuraavaksi lähdin kokeilemaan oman kotisivun pyörittämistä lokaalisti. Tähän tarvitsin komennot `sudo 2enmod userdir`, jolla aktivoin käyttäjähakemiston apache palvelimen käyttöön. Seuraavaksi käynnistin apache2 -palvelimen uudestaan komennolla `sudo systemctl restart apache2` ja loin uuden hakemiston nimellä "public_html" omaan käyttäjähakemistooni. Tämän jälkeen valitsin hakemiston `cd public_html -komennolla` ja tein hakemistoon tiedoston nimellä "index.html". Tähän käytin komentoa `nano index.html`. Html -tiedostoon tein yksinkertaisen html-rakenteen. Alla kyseinen tiedosto selaimessa.*

![kuva](https://user-images.githubusercontent.com/77921212/132941794-41cccbc4-9258-4d70-a256-49679606aa62.png)


\
&nbsp;


### b) Surffaa oman palvelimesi weppisivuja. Etsi Apachen lokista esimerkki onnistuneesta (200 ok) sivulatauksesta ja epäonnistuneesta (esim 404 not found) sivulatauksesta. Analysoi rivit.

*Käytin lokien hakemiseen komentoa: `sudo cat /var/log/apache2/access.log`*

*Ensimmäiseltä riviltä voi analysoida päivämääräärän, kellonajan sekunninkymmenesosan tarkkuudella sekä myös "0300+", joka tarkoittaa Itä-Euroopan kesäaikaa. "GET" tarkoittaa puolestaan tenkniikkaa, jolla haetaan ja pyydetään dataa joltain tietyltä nettisivulta<sup>2</sup>. "HTTP/1.1" tarkoittaa HTTP:n versiota ja "200" ilmaisee, että tapahtuma oli onnistunut. "841" puolestaan tarkoittaa muistaakseni haettavan alueen tavukokoa. Rivin viimeinen kaistele kertoo yksityiskohtaisesti tietoa selaimesta. Mozilla/5.0 tarkoittaa Mozillan versionumeroa, "X11; Linux x86_64; rv:78:0" kertoo, että kyseinen selain on tarkoitettu 64 bittiselle Linuxille. "Gecko/20100101" puolestaan kertoo firefoxin selainmoottorin nimen ja versionumeron. Viimeinen "Firefox/78.0" puolestaan kertoo Firefoxin versionumeron*
  
> ::1 - - [10/Sep/2021:11:24:48 +0300] "GET /~danskubansku/ HTTP/1.1" 200 841     "-" "Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0"
  
 
*Toisen rivin sisältö on muuten sama, mutta status "404", aika sekä päivämäärä ovat eri. GET-pyynnön polku on myös eri kuin edeltävässä ja "404" kertoo, että kyseisellä polulla ei löydy nettisivua.*
  
> ::1 - - [10/Sep/2021:11:58:45 +0300] "GET /~dan HTTP/1.1" 404 488 "-"           "Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0"
  

\
&nbsp;


### d) Tee virhe johonkin Apachen asetustiedostoon, etsi ja analysoi tuo rivi. Etsimiseen sopivat esimerkiksi Apachen omat lokit, syslog sekä ‘apache2ctl configtest’.

*Etsin apache2 -kansion etc -polussa "/etc/apache2". Kansion sisällä avasin "apache2.conf" -tiedoston komennolla sudo `sudo nano apache2.conf` ja lisäsin rivin, jossa lukee teksti: "katsotaan kaatuuko palvelin". Sudoa jouduin käyttämään sen takia, että ilman sudoa komentorivistä tuli viestiä, että tarvittavia oikeuksia ei ole. Seuraavaksi tallensin tiedoston ja käynnistin palvelimen uudestaan `sudo systemctl restart apache2`. Heti käynnistyksen yhteydessä tuli error-viesti:*

> Job for apache2.service failed because the control process exited with error code.
See "systemctl status apache2.service" and "journalctl -xe" for details.

*Yllänäkyvästä virheviestistä tulkitsin, että apache2:n hallintajärjestelmä havaitsi, että jossain konfigurointitiedostossa on virheellisetä koodia*

*Tämän jälkeen menin taas Apachen access.logiin ja poimin sieltä kyseistä erroria ilmaisevat rivit:*

> Sep 10 12:21:26 DanielinDebian systemd[1]: Failed to start The Apache HTTP Server.

*Yllänäkyvältä riviltä voi nähdä tarkan päivämäärän ja kellonajan, järjestelmän ylläpitäjän nimen ja systemd (tarkoittaa Linuxin alustamis- ja palvelunhallintajärjestelmää).<sup>3</sup> Viimeiseksi voi lukea tarkan virheviestin, eli Apachen HTTP Serverin käynnistys epäonnistui*

> Sep 10 12:21:26 DanielinDebian apachectl[3524]: Invalid command 'katsotaan', perhaps misspelled or defined by a module not included in the server configuration

*Yllänäkyvä lokin rivi on muuten hyvin samanlainen, mutta Apachen kontrolleri "apachectl"<sup>4</sup>, kertoo, että palvelimen konfiguroinnissa on vääränlainen komento.*
  

\
&nbsp;


### i) Kuinka monta eri HTTP Status:ta (200, 404, 500…) saat aiheutettua lokeihin? Selitä, miten aiheutit tilanteet ja analysoi yksi rivi kustakin statuksesta.

*Käytin lokeihin `sudo tail -f /var/log/apache2/access.log` -komentoa, jolla sain realiajassa lokit näkyviin.*

> ::1 - - [10/Sep/2021:13:35:23 +0300] "GET /~danskubansku/ HTTP/1.1" 200 841 "-" "Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0"

*Yllänäkycän tilanteen aiheutin siten, että pääsin onnistuneesti omalle kotisivulleni. Riviltä voi analysoida päivämääräärän, kellonajan sekunninkymmenesosan tarkkuudella, sekä myös 0300+, joka tarkoittaa Itä-Euroopan kesäaikaa. "GET" tarkoittaa puolestaan tenkniikkaa, jolla haetaan ja pyydetään dataa joltain tietyltä nettisivulta <sup>2</sup>. "HTTP/1.1" tarkoittaa HTTP:n versiota ja "200" ilmaisee, että tapahtuma oli onnistunut. "841" puolestaan tarkoittaa muistaakseni haettavan alueen tavukokoa. Rivin viimeinen kaistele kertoo yksityiskohtaisesti tietoa selaimesta. "Mozilla/5.0" tarkoittaa Mozillan versionumeroa, "X11; Linux x86_64; rv:78:0" kertoo, että kyseinen selain on tarkoitettu 64-bittiselle Linuxille. "Gecko/20100101" puolestaan kertoo firefoxin selainmoottorin nimen ja versionumeron. Viimeinen "Firefox/78.0" puolestaan kertoo Firefoxin versionumeron*

> ::1 - - [11/Sep/2021:08:57:41 +0300] "GET /~danskuba HTTP/1.1" 404 487 "-" "Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0"

*Yllänäkyvän tilanteen aiheutin kirjoittamalla palvelimeen tahalleen väärän sivun. Tästä seurasi 404 error eli "Not Found". Ainoa ero yllä olveaan riviin on lokin päivämäärä ja aika, statuksen tyyppi eli "404" ja eri tavukoko: "487".*

> ::1 - - [11/Sep/2021:09:42:37 +0300] "GET /icons/openlogo-75.png HTTP/1.1" 304 249 "http://localhost/" "Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0"

*Yllänäkyvän tilanteen aiheutin avaamalla Apachen oletussivun palvelimelta. "304" tarkoittaa, sitä, että sivu ei ole päivittynyt viime haun jälkeen <sup>5</sup>. Ilmeisesti siis loki havaitsee, että "openlogo-75-png" on pysynyt samana, joten sen vuoksi syntyy "status 304". Muut lokin osat vastaavat aiemmin esitettyjä rivejä päivämäärää ja aikaa lukuunottamatta*

> ::1 - - [11/Sep/2021:10:27:44 +0300] "GET /~danskubansku/ HTTP/1.1" 403 491 "-" "Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0"

*Yllänäkyvän tilanteen sain aikaan muuttamalla "public_html" -kansion nimen. Tästä toiminnasta seurasi "Status 403" eli forbidden, tarkoittaen, että minulla ei ole oikeutta kyseiseen kansioon, koska se ei ole nimetty vaaditulla tavalla, eli "public_html". Rivin muut tiedot vastaavat aikaisempia päivämäärää ja aikaa lukuunottamatta.*

\
&nbsp;

### m) Vaihda Apachen oletussivu. Eli laita palvelimen etusivulla (ilman tildeä) näkyvä sivu niin, että alkuperäinen on jonkun käyttäjän kotihakemistossa ja voit muokata sitä ilman pääkäyttäjän oikeuksia.
  
*En ollut aikaisemmin tehnyt vastaavanlaista operaatiota niin minun täytyi turvautua internetin puoleen. Löysin "askubuntu.com" -sivulta hyvän langan <sup>6</sup>, jolla oli erinomaiset ohjeet oletussivun vaihtamiselle. Ennen kyseisen keskustelulangan löytämistä olin oivaltanut, että Apachen oletussivun voi poistaa menemällä hakemistoon "/var/www/html". Poistin index.html tiedoston `sudo rm index.html` -komennolla. Tämän jälkeen noudatin nettisivulla <sup>6</sup> näkyviä ohjeita. Etenin "/etc/apache2/sites-available" -hakemistoon, jossa tein konfigurointi-tiedostosta kopion `sudo cp 000-default.conf mywebsite.conf` -komennolla. Tämän jälkeen avasin "mywebsite.conf" -tiedoston ja lähdin muuttamaan asetuksia. Ensiksi muutin "DocumentRoot" asetuksen vastaamaan omaa public_html hakemistoani. Sitten lisäsin ohjeiden mukaan*
> "<Directory /home/danskubansku/public_html>
> Require all granted.."

*-osion, jolla annoin oikeudet kyseiseen käyttäjähakemistoon. Sitten lisäsin vielä ServerName- ja ServerAlias -asetukset vastaamaan paikallista osoitetta "localhost". Lopuksi otin käyttöön tekemäni konfiguroinnit komennolla `sudo a2ensite mywebsite.conf` ja käynnistin vielä palvelimen uudestaan komennolla `sudo systemctl restart apache2`. Alla kuvat konfigurointi-tiedostosta ja selainnäkymästä.*
 
![image](https://user-images.githubusercontent.com/77921212/132984012-006f35b0-8481-4ae0-8990-e3680d7adf08.png)

![image](https://user-images.githubusercontent.com/77921212/132984314-9c5134f6-39e7-4f38-9e9d-aa8fb40b53b6.png)

\
&nbsp;

### Loppuajatuksia

*Tehtävät olivat varsin mielenkiintoisia, kun pääsi kunnolla vauhtiin. Koin erityisen kiinnostavaksi "m)" -kohdan, koska ratkaisu ei ollut täysin selvillä ja sitä varten joutui tekemään hieman tutkimustyötä. Tehtävien tekoon kului kaikenkaikkiaan aikaa noin kahdeksan tuntia ja ripottelin tehtävien tekemiset perjantaille, lauantaille ja sunnuntaille*

\
&nbsp;


### Lähteet:


| Lähdenumero | Linkki |
| ----------- | ------------------------------------------------------------------------- |
| 1   | https://terokarvinen.com/2021/linux-server-course-linux-palvelimet-ict4tn021-3016/                            |
| 2   | https://rapidapi.com/blog/api-glossary/http-request-methods/ |
| 3   | https://www.linode.com/docs/guides/what-is-systemd/ |
| 4   | https://stackoverflow.com/questions/904621/what-does-apachectl-stand-for-why-isnt-it-just-apache/904626                              |
| 5   | https://blog.hubspot.com/marketing/http-304-not-modified |
| 6   | https://askubuntu.com/questions/857609/apache2-now-pointing-to-new-default-page             |    
