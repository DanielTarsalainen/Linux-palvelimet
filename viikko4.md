# h4 - Oikea palvelin oikeaan nettiin
####  Tekijä: Daniel Tarsalainen 

\
&nbsp;


## Tehtävänanto


- [x] a) Vuokraa oma julkinen palvelin Internetiin. Vinkkejä: Perustele tehdyt valinnat. Voit saada myös ilmaiseksi Github Education -paketilla. Jos sinulla on aiempi palvelin, tee uusi alusta lähtien ja raportoi samalla. Käytä aina hyviä salasanoja.
- [x] b) Suojaa palvelin tulimuurilla. Muista ensin reikä ssh-palvelimelle.
- [x] c) Laita koneellesi Apache-weppipalvelin. Korvaa testisivu. Laita käyttäjän kotisivut toimimaan. Kokeile eri koneelta, esim. kännykällä, että sivut toimivat. Vinkki: tee kotisivut normaalina käyttäjänä public_html/ alle, opettelemme "name based virtual hosting" myöhemmin.
- [x] d) Etsi lokeistasi merkkejä murtautumisyrityksistä ja analysoi ne. Vinkki: auth.log.



\
&nbsp;



#### a) Vuokraa oma julkinen palvelin Internetiin. Vinkkejä: Perustele tehdyt valinnat. Voit saada myös ilmaiseksi Github Education -paketilla. Jos sinulla on aiempi palvelin, tee uusi alusta lähtien ja raportoi samalla. Käytä aina hyviä salasanoja.

*Lähdin vuokramaan palvelinta DigitalOceanista, koska sitä suositeltiin oppitunnilla. Sain Github Education -paketilla 100 dollaria käytettäväksi kahden kuukauden ajaksi. Lähdin luomaan uutta julkista palvelinta "Create a droplet" -kohdasta. Napinpainalluksen jälkeen ilmestyi alla näkyvä sivu, josta valitsin Debian 10:nen palvelimen käyttöjärjestelmäksi. Seuraavaksi valitsin tavallisen suunnitelman, johon sisältyi tavallinen Intel prosessori SSD:n kanssa.*

![image](https://user-images.githubusercontent.com/77921212/133623762-26ad3845-e05c-4c10-ba18-40bb1e60f51a.png)

*Seuraavaksi tuli valita alue, joista valitsin Amsterdamin.*

![image](https://user-images.githubusercontent.com/77921212/133624676-dee3a1b3-9a7b-4e1e-9dc3-fb4b71defe21.png)

*Tämän jälkeen lähdin valitsemaan salasanaa. Tein siitä mahdollisimman monimutkaisen, jotta tunkeutumisuhka on mahdollisimman pieni. Lopuksi tuli valita palvelimen "hostname", jonka myös tein kryptiseksi turvallisuussyistä. Tämän jälkeen painoin jälleen "Create a droplet" -nappia, jolloin pääsin poimimaan palvelimen ip-osoitteen.*

*Sitten vuorossa oli palvelimelle kirjautuminen komentoriviltä käsin.*

\
&nbsp;

#### b) Suojaa palvelin tulimuurilla. Muista ensin reikä ssh-palvelimelle.

*Hyödynsin tässä tehtävässä Tero Karvisen sivulla<sup>1</sup> näkyviä ohjeita. Kirjauduin palvelimelle sisään rootilla komennolla `ssh root @178.128.245.233`. Ip-osoitteen syöttämisen jälkeen tuli varmistusviesti (yes or no).*

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

*Tämän jälkeen lähdin muuttamaan Apache2 oletussivun omaksi nettisivukseni. Tein viime viikon "m)" -kohdan tapaan kopion `etc/apache2/sites-available` -kansion `000-default.conf` tiedostosta ja asetin kopion nimeksi `leinadsite.conf`. Viime viikon tapaan lisäsin ServerName ja ServerALias -kohdat, ja niihin kumpaankin palvelimeni IP-osoitteen. DocumentRoot -kohtaan laitoin jo valmiiksi kohta tekemäni public_html kansion "leinad" -käyttäjän kotihakemistoon. Directory -kohtaan asetin äsken mainititun hakemiston ja sen sisälle "Require all granted" asetuksen, joka mahdollistaa palvelimen pääsyn "public_html" -hakemistoon.*

![image](https://user-images.githubusercontent.com/77921212/133633857-23368a9c-2e95-4fea-b57b-46eff3cdc56a.png)

*Tämän jälkeen otin uudet configuraatiot käyttöön `sudo a2ensite leinadsite.conf` -komennolla. Sitten käynnistin apache2 palvelimen uudestaan `sudo systemctl start apache2` -komennolla, jonka jälkeen päivitin palvelimen `sudo systemctl reload apache2 -komennolla`, jotta aseutukset tulisivat varmasti voimaaan.*

*Lopuksi tein omaan kotihakemistoon uuden kansion nimeltä "public_html" ja loin sinne tiedoston nimellä "index.html". Tiedoston sisään kirjotin tekstin "Palvelin toimii juhuu!"*

![image](https://user-images.githubusercontent.com/77921212/133822839-6bb027d8-2342-4177-aedb-76a73e8059ce.png)

*Onnistuin pääsemään myös puhelimella palvelimelle*

![kuva](https://user-images.githubusercontent.com/77921212/133823774-aaba2233-f917-448d-89ed-e776bb773ee8.png)


\
&nbsp;


#### d) Etsi lokeistasi merkkejä murtautumisyrityksistä ja analysoi ne. Vinkki: auth.log.

*`sudo nano /var/log/auth.log` -komennolla pääsin tarkastelemaan auth.logia. Alla muutama epäilyttävä rivi kyseisestä tiedostosta.*

> Sep 19 00:43:14 valas sshd[24269]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=187.72.3.242  user=root

*Ylläolevalta riviltä voi lukea päivämäärän ja kellonajan tarkasti. Siitä voi myös todeta, että käyttäjän kirjautumisyritys rootilla on ollut epäonnistunut. rhost -kohdasta voi lukea ip-osoitteen*

> Sep 19 00:07:42 valas sshd[24161]: Did not receive identification string from 141.98.10.179 port 38066

*Ylläolevalta riviltä tulkitsin, että kyseisestä ip-osoitteesta syötetty käyttäjänimi tai salasana ovat olleet tyhjänä.*

> Sep 19 00:47:23 valas sshd[24396]: pam_unix(sshd:auth): check pass; user unknown

*Ylläolevalta riviltä tulkitsin, että syötettyä käyttäjänimeä ei ole olemassa*

> Sep 19 00:47:35 valas sshd[24405]: Invalid user nagios from 187.72.3.242 port 43281

*Ylläolevalta riviltä tulkitsin, että syötettyä käyttäjänimeä "nagios" ole ole olemassa, joten pääsy-yritys tyrehtyi siihen*



\
&nbsp;


## Lähteet:
*- (1) https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/*




