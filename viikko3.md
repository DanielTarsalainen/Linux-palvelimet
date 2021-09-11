a) Asenna Apache, laita käyttäjien kotisivut (http://example.com/~tero) toimimaan. Testaa esimerkkikotisivulla.

  Aloitin palvelimen asennusken kirjoittamalla sudo apt-get update komennon, jolla   päivitin saatavilla olevat paketit. Seuraavaksi tein sudo apt-get install apache2 komennon, jolla sain apache palvelimen asennettua virtuaalikoneelle. Sitten testasin apache2 toimivuuden tekemällä komennon sudo systemctl start apache2. Curl localhost -komennolla sain komentoriville näkyviin apache2 oletussivun lokaalisti. Alla kuva tulostuksesta. 
  
Seuraavaksi lähdin kokeilemaan oman kotisivun pyörittämistä lokaalisti. Tähän tarvitsin komennot sudo 2enmod userdir, jolla aktivoin käyttäjähakemiston apache palvelimen käyttöön. Seuraavaksi käynnistin apache2 palvelimen uudestaan ja loin uudn hakemiston ("public_html") omaan käyttäjähakemistooni. Tämän jälkeen valitsin hakemiston cd public_html -komennolla ja tein hakemistoon tiedston nimellä index.html. Tähän käytin komentoa nano index.html. html -tiedostoon tein yksinkertaisen html rakenteen. Alla kyseinen tiedosto selaimessa. 


b) Surffaa oman palvelimesi weppisivuja. Etsi Apachen lokista esimerkki onnistuneesta (200 ok) sivulatauksesta ja epäonnistuneesta (esim 404 not found) sivulatauksesta. Analysoi rivit.

sudo cat /var/log/apache2/access.log

200 ok:
  ::1 - - [10/Sep/2021:11:08:36 +0300] "GET / HTTP/1.1" 200 10956 "-"             "curl/7.74.0"
200 ok esim2.
  ::1 - - [10/Sep/2021:11:24:48 +0300] "GET /~danskubansku/ HTTP/1.1" 200 841     "-" "Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0"

404 not found:
  ::1 - - [10/Sep/2021:11:58:45 +0300] "GET /~dan HTTP/1.1" 404 488 "-"           "Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0"




d) Tee virhe johonkin Apachen asetustiedostoon, etsi ja analysoi tuo rivi. Etsimiseen sopivat esimerkiksi Apachen omat lokit, syslog sekä ‘apache2ctl configtest’.

etsin apache2 kansion /etc/apache2. kansion sisällä avasin apache2.conf tiedoston ja lisäsin rivin, jossa lukee "katsotaan kaatuuko palvelin". Seuraavaksi tallensin tiedoston ja käynnistin palvelimen uudestaan sudo systemctl restart apache2. Heti käynnistyksen yhteydessä tuli error: Job for apache2.service failed because the control process exited with error code.
See "systemctl status apache2.service" and "journalctl -xe" for details.

Sep 10 12:21:26 DanielinDebian systemd[1]: Failed to start The Apache HTTP Server.

Sep 10 12:21:26 DanielinDebian apachectl[3524]: Invalid command 'katsotaan', perhaps misspelled or defined by a module not included in the server configuration

Sep 10 12:21:26 DanielinDebian systemd[1]: Failed to start The Apache HTTP Server.




i) Kuinka monta eri HTTP Status:ta (200, 404, 500…) saat aiheutettua lokeihin? Selitä, miten aiheutit tilanteet ja analysoi yksi rivi kustakin statuksesta.

Käytin lokeihin sudo tail -f /var/log/apache2/access.log -komentoa, jolla sain realiajassa lokit näkyviin. 

::1 - - [10/Sep/2021:13:35:23 +0300] "GET /~danskubansku/ HTTP/1.1" 200 841 "-" "Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0"

Kyseisen tilanteen aiheutin siten, että pääsin onnistuneesti omalle kotisivulleni. Riviltä voi analysoida, että GET tarkoittaa tenkniikkaa, jolla haetaan ja pyydetään dataa joltain tietyltä nettisivulta(1). HTTP/1.1 tarkoittaa HTTP:n versiota ja 200 ilmaisee, että tapahtuma oli onnistunut. 841 puolestaan tarkoittaa muistaakseni haettavan alueen tavukokoa. Rivin viimeinen kaistele kertoo yksityiskohtaisesti tietoa selaimesta. Mozilla/5.0 tarkoittaa Mozillan versionumeroa, "X11; Linux x86_64; rv:78:0" kertoo, että kyseinen selain on tarkoitettu 64 bittiselle Linuxille. "Gecko/20100101" puolestaan kertoo firefoxin selainmoottorin nimen ja versionumeron. Viimeinen "Firefox/78.0" puolestaan kertoo Firefoxin versionumeron

::1 - - [11/Sep/2021:08:57:41 +0300] "GET /~danskuba HTTP/1.1" 404 487 "-" "Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0"

Kyseisen tilanteen aiheutin kirjoittamalla palvelimeen tahalleen väärän sivun. Tästä seurasi 404 error eli "Not Found". Ainoa ero yllä olveaan riviin on login päivämäärä ja aika, statuksen tyyppi eli 404 ja eri tavukoko: 487. 

::1 - - [11/Sep/2021:09:42:37 +0300] "GET /icons/openlogo-75.png HTTP/1.1" 304 249 "http://localhost/" "Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0"

Kyseisen tilanteen aiheutin avaamalla Apachen oletussivun palvelimelta. 304 error tarkoittaa, sitä, että sivu ei ole päivittynyt viime haun jälkeen(2). Ilmeisesti siis loki havaitsee, että openlogo-75-png on pysynyt samana, joten sen vuoksi syntyy status 304. Muut login osat vastaavat aiemmin esitettyjä rivejä päivämäärää ja aikaa lukuunottamatta





 
Lähteet:

(1) https://rapidapi.com/blog/api-glossary/http-request-methods/ 
(2) https://blog.hubspot.com/marketing/http-304-not-modified

