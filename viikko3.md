a) Asenna Apache, laita käyttäjien kotisivut (http://example.com/~tero) toimimaan. Testaa esimerkkikotisivulla.

  Aloitin palvelimen asennusken kirjoittamalla sudo apt-get update komennon, jolla   päivitin saatavilla olevat paketit. Seuraavaksi tein sudo apt-get install apache2 komennon, jolla sain apache palvelimen asennettua virtuaalikoneelle. Sitten testasin apache2 toimivuuden tekemällä komennon sudo systemctl start apache2. Curl localhost -komennolla sain komentoriville näkyviin apache2 oletussivun lokaalisti. Alla kuva tulostuksesta. 
  
Seuraavaksi lähdin kokeilemaan oman kotisivun pyörittämistä lokaalisti. Tähän tarvitsin komennot sudo 2enmod userdir, jolla aktivoin käyttäjähakemiston apache palvelimen käyttöön. Seuraavaksi käynnistin apache2 palvelimen uudestaan ja loin uudn hakemiston ("public_html") omaan käyttäjähakemistooni. Tämän jälkeen valitsin hakemiston cd public_html -komennolla ja tein hakemistoon tiedston nimellä index.html. Tähän käytin komentoa nano index.html. html -tiedostoon tein yksinkertaisen html rakenteen. Alla kyseinen tiedosto selaimessa. 


b) Surffaa oman palvelimesi weppisivuja. Etsi Apachen lokista esimerkki onnistuneesta (200 ok) sivulatauksesta ja epäonnistuneesta (esim 404 not found) sivulatauksesta. Analysoi rivit.

200 ok:
  ::1 - - [10/Sep/2021:11:08:36 +0300] "GET / HTTP/1.1" 200 10956 "-"             "curl/7.74.0"
200 ok esim2.
  ::1 - - [10/Sep/2021:11:24:48 +0300] "GET /~danskubansku/ HTTP/1.1" 200 841     "-" "Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0"

404 not found:
  ::1 - - [10/Sep/2021:11:58:45 +0300] "GET /~dan HTTP/1.1" 404 488 "-"           "Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0"
  
  




d) Tee virhe johonkin Apachen asetustiedostoon, etsi ja analysoi tuo rivi. Etsimiseen sopivat esimerkiksi Apachen omat lokit, syslog sekä ‘apache2ctl configtest’.

i) Kuinka monta eri HTTP Status:ta (200, 404, 500…) saat aiheutettua lokeihin? Selitä, miten aiheutit tilanteet ja analysoi yksi rivi kustakin statuksesta.

m) Vaihda Apachen oletussivu. Eli laita palvelimen etusivulla (ilman tildeä) näkyvä sivu niin, että alkuperäinen on jonkun käyttäjän kotihakemistossa ja voit muokata sitä ilman pääkäyttäjän oikeuksia.
