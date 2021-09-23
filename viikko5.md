# H5
####  Tekijä: Daniel Tarsalainen 

\
&nbsp;

## Tehtävänanto


*Tee kukin tehtävä alusta lähtien ja kirjaa samalla, vaikka olisit kokeillut tunnilla. Jos pidät propellihattua, katso kohta x.*

- [ ]  a) Leikkinimi. Tee Apachelle uusi Name Based Virtual Host, ja testaa sitä simuloimalla nimipalvelua hosts-tiedoston avulla.

- [ ] b) Julkinen nimi. Laita julkiselle palvelimellesi julkinen domain-nimi. Käytä oikeaa nimeä (joko vuokrattua tai ilmaispalvelusta). Tee Apachelle Name Based Virtual Host tälle nimelle. Kokeile eri laitteelta (esim. kännykältä), että nimi oikeasti toimii.

- [ ] c) Hello Flask! Tee Python Flask hei maailma kehitysympäristössä. Voit siis käyttää tuotantoon sopimatonta app.run(debug=True) ajoa.

- [ ] d) Tuotanto-Flask. Tee tuotantotyyppinen asennus Flaskista käyttäen Apachen WSGI-modulia. Kokeile, että pystyt muokkaamaan koodia ilman sudoa ja saat uuden version käyttöön käynnistämättä Apachea uudelleen. ('touch foo.wsgi')


\
&nbsp;


#### a) Leikkinimi. Tee Apachelle uusi Name Based Virtual Host, ja testaa sitä simuloimalla nimipalvelua hosts-tiedoston avulla.

*Päivitin paketit `sudo apt-get update` -komennolla. Sitten loin `sudo nano index.html` komennolla uuden html tiedoston `var/www/html` -hakemistoon. Seuraavaksi kirjotin `echo "Default" | sudo tee /var/Www/html/index.html` -komennolla kyseiselle sivulle tekstin "Default". Sitten lähdin luomaan uutta nimen sisältävää virtuaalista hostia. Tähän käytin komentoa $ sudoedit /etc/apache2/sites-available/danieltars.com.conf (kuva1).*

![kuva](https://user-images.githubusercontent.com/77921212/134549159-4509e1b0-6849-4b84-a70d-dc85451e86cc.png)


*Tämän jälkeen otin konfiguroinnit käyttöön `sudo a2ensite danieltars.com.conf` -komennolla ja latasin apache2 palvelimen uudestaan `systemctl reload apache2` -komennolla. `mkdir -p /home/danskubansku/publicsites/danieltars.com` -komennolla tein uuden hakemiston publicsites hakemistoon. `echo hei sinä! > /home/danskubansku/publicsites/danieltars.com/index.html` -komennolla tein uuden index.html -tiedoston ja kirjotin siihen tekstin "hei sinä". *

*Lopuksi vielä käynnistin Apache palvelimen uudestaan `sudo systemctl restart apache2` -komennolla.*

*Sitten kokeilin vielä tulostaa nettisivuni sisällön komennolla `curl -H 'Host: danieltars.com' localhost`*

*Lopuksi vielä simuloin nettisivulle halutun nimen, eli "danieltars.com". Tein sen "/etc/hosts" -polussa komennolla `sudoedit /etc/hosts`*

![kuva](https://user-images.githubusercontent.com/77921212/134549292-9d4f850b-32b6-44f2-8b56-fe930e4bef45.png)

*Lopuksi hain sekä localhost nimellä, että danieltars.com nimellä. Kummallakin tavalla sain auki halutun sivun. "Sinä" -sana muuttui sen takia muotoa, koska index.html tiedostossa ei ole minkäänlaista dokumentin siällön määrittävää dokumenttityyppiä.*

![kuva](https://user-images.githubusercontent.com/77921212/134549569-92335fc7-8efc-4832-8b9c-1ed691731e2b.png)


\
&nbsp;


#### b) Julkinen nimi. Laita julkiselle palvelimellesi julkinen domain-nimi. Käytä oikeaa nimeä (joko vuokrattua tai ilmaispalvelusta). Tee Apachelle Name Based Virtual Host tälle nimelle. Kokeile eri laitteelta (esim. kännykältä), että nimi oikeasti toimii.

*Vuokrasin namecheapista xyz-loppuisen domainin*

![kuva](https://user-images.githubusercontent.com/77921212/134465546-c5e388dc-57b5-473a-a3a1-47956ad09ed7.png)

*Tämän jälkeen tein "Add a domain kohdasta" -kohdasta uuden domainin digital oceanin sivulla. Nimeksi annoin vuokratun domainin nimen, eli danieltarsalainen.xyz* 

![kuva](https://user-images.githubusercontent.com/77921212/134468600-83188c40-f137-4cb4-964c-f2931dd0205a.png)

*Tämän jälkeen menin tarkastelemaan digital oceanin domain-näkymää, joka näytti seuraavanalaiselta.*

![kuva](https://user-images.githubusercontent.com/77921212/134468854-760d43eb-d827-4471-acc7-0d21314d017a.png)

*Sitten noudatin domain -sivulla näkyviä ohjeita nimipalvelinten muuttamiseen.*

*https://www.digitalocean.com/community/tutorials/how-to-point-to-digitalocean-nameservers-from-common-domain-registrars -ohjeessa neuvottiin vaihtamaan digital oceanin nameservers kohta seuraavanlaiseksi*

![kuva](https://user-images.githubusercontent.com/77921212/134466271-eb778e0f-da39-4ad3-ab0d-d4b251e52d37.png)

*Muutosten tultua voimaan tuli seuraavanlainen viesti.*

![kuva](https://user-images.githubusercontent.com/77921212/134466373-4f7726da-0b9e-4a4e-8880-23418d31e0c9.png)

*Digital oceanin ohjesivulla tosin luki, että muutoksissa voi mennä vain 30 minuttia. Odotellessani huomasin, että viime viikolta oli jäänyt Apache2 oletussivu var/www/html kansioon. Korjasin tämän tekemällä julkislle palvelimelle `echo "Default"|sudo tee /var/www/html/index.html`komennon. Näin oletussivulle ylikirjottui teksti "Default".*

*Nyt kun aikaa oli kulunut reilu puoli tuntia, niin menin julkisella palvelimella `/etc/apache2/sites-available`-polkuun ja muokkasin viimeviikkoista `leinadsite.conf` tiedostoa. ServerNamessa ja ServerAliaksessa oli aikaisemmin nettisivun ip-osoite, mutta nyt kun domain saatiin yhdistettyä digital oceanin julkiseen palvelimeen, niin nyt niihin kohtaiin voitiin laitaa oman domainin nimen. ServerName -kohtaan "www.danieltarsalainen.xyz" ja ServerAlias -kohtaan "danieltarsalainen.xyz"*

![kuva](https://user-images.githubusercontent.com/77921212/134511373-0155b70a-f1fd-4eef-8b04-c5f984139152.png)

*Tämän jälkeen käynnistin Apache2 palvelimen uudestaan komennola `sudo systemctl restart apache2`*

*Tämän jälkeen halusin testata, tulostuuko "danieltarsalainen.xyz" -sivulta mitään curl komennolla. Ensiksi päivitin saatavilla olevat paketit `sudo apt-get update` -komennolla ja sitten asensin curlin `sudo apt-get install curl` -komennolla. Tämän jälkeen tulostin oman nettisivuni sisällön komennolla `curl danieltarsalainen.xyz`. Tulostus oli onnistunut. Tämän jälkeen kokeilin vielä selaimessa, joka myös näytti onnistuneesti sivun sisällön.*

![kuva](https://user-images.githubusercontent.com/77921212/134489928-8e75605f-aa65-4963-8c54-606426703437.png)

![kuva](https://user-images.githubusercontent.com/77921212/134489963-70ae52f8-fc10-43e1-98dd-50737cfd0749.png)


\
&nbsp;


#### c) Hello Flask! Tee Python Flask hei maailma kehitysympäristössä. Voit siis käyttää tuotantoon sopimatonta app.run(debug=True) ajoa.

*Lähdin tekmään tehtävää Teron (https://terokarvinen.com/2020/hello-flask-python-web-app/) kotisivun ohjeen mukaan. Ensiksi päivitin saatavilla olevat paketit `sudo apt get update` -komennolla. Sitten asensin flaskin virtuaalikoneelle komennolla `sudo apt-get -y install python3-flask`.*

*Lähdin tekemään tehtävää luomalla kotihakemistoon uuden kansion nimeltä flask komennolla `mkdir flask`. Kansion sisälle loin uuden tiedoston nimeltä hello.py komennolla `nano hello.py`*

![kuva](https://user-images.githubusercontent.com/77921212/134548329-8a8da363-b45a-4572-a3ba-98cb3d508ca7.png)

*Python-tiedoon kirjoitin "hello" -niminen funkio, joka palauttaa viestin "Learn flask at danieltarsalainen.xyz!". `python3 hello.py` -komennon jälkeen sain tulostuksen näkymään lokaalisti portti 5000:ssa.*

![kuva](https://user-images.githubusercontent.com/77921212/134548890-1214bcc6-bf59-4b03-9594-cd8108235144.png)


\
&nbsp;


#### d) Tuotanto-Flask. Tee tuotantotyyppinen asennus Flaskista käyttäen Apachen WSGI-modulia. Kokeile, että pystyt muokkaamaan koodia ilman sudoa ja saat uuden version käyttöön käynnistämättä Apachea uudelleen. ('touch foo.wsgi')

*Lähdin liikkeelle luomalla uuden käyttäjän virtuaaliselle koneelle komennolla `sudo adduser danewsgi`. Tietojen täyttämisen jälkeen lukitsin käyttäjälle kirjautumisen `sudo usermod --lock danewsgi` -komennolla. `sudo adduser $(whoami) danewsgi` -komennolla lisäsin oman käyttäjän danwsgi ryhmään.*

![kuva](https://user-images.githubusercontent.com/77921212/134489822-8c22dbb9-c9ba-4a6f-a214-a966d133e0fe.png)

*Tämän jälkeen loin uuden name based virtual hostin komennolla `sudoedit /etc/apache2/sites-available/danewsgi.conf`*

![kuva](https://user-images.githubusercontent.com/77921212/134489706-161e7e54-289d-44ad-983c-f58fe96898d7.png)

*Sitten otin konfiguraatiot käyttöön komennolla `sudo a2ensite danewsgi.conf` ja poistin vanhan sivun konfiguraatiot komennolla `sudo a2dissite 000-default.conf`.*  

![kuva](https://user-images.githubusercontent.com/77921212/134490451-f73f18db-5b95-4af8-93a9-e38f7771123c.png)

![kuva](https://user-images.githubusercontent.com/77921212/134490916-98ce675e-0c40-4e71-ad38-54541a90e869.png)

*Tämän jälkeen kokeilin käynnistää apachen uudelleen, jonka jälkeen tuli kyseinen kyseinen error: `Job for apache2.service failed`. Sitten ajoin vielä kertaalleen config testin komennolla `apache2ctl configtest`. Siitä seurasi alla oleva virhe. 
![kuva](https://user-images.githubusercontent.com/77921212/134491667-0fa6cdc8-7a2c-4e79-9f9a-ac115bf35f65.png)


*Tämän korjaukseen käytin wsgi-moduulin asennusta. Päivitin ensin saatavilla olevat paketit `sudo apt-get update` -komennolla, jonka jälkeen asensin wsgi-moduulin komennolla `sudo apt-get -y install libapache2-mod-wsgi-py3`*

![kuva](https://user-images.githubusercontent.com/77921212/134492106-e2faf4b9-2d4d-4a11-bfa8-94a77bd7d543.png)

*Apachen restarttaus meni läpi ja config-testissä tuli seuraavanlainen tulos:*

![kuva](https://user-images.githubusercontent.com/77921212/134492563-1f7fc5fa-2b14-4c09-b16a-8e28cbbcf734.png)

*Seuraavaksi kokeilin vielä Localhostin printtausta curlin avaulla ja siitä seurasi tuli seuraavanlainen tulos: *

![kuva](https://user-images.githubusercontent.com/77921212/134492942-9939c12e-26f9-406b-b3e6-f0bdc5097192.png)

*403 forbidden viittaa siihe, että minun peruskäyttäjällä ei ole oikeuksia kyseiseen sivuun*

![kuva](https://user-images.githubusercontent.com/77921212/134493366-e7736d20-d465-4d4b-b6ba-b2427ae6b8ea.png)

*Viimeiseltä riviltä voi lukea "client denied server configuration", joka tarkoittaa, että kyseistä kansiota ei ole olemassa*

*`groups danskubansku` -komennolla näin kaikki ryhmät, joihin oma käyttäjäni kuuluu, ja löysin danewsgi -ryhmän listasta.*
*Tällä sain varmuuden siitä, että minulla on tarvittavat oikeudet toimenpiteisiin*

*Sitten lähdin tekeään uutta hakemistoa komennolla `sudo mkdir /home/danewsgi/public_wsgi`. Tämän jälkeen muutin oikeuksia vielä niin, että peruskäyttäjästä tulisi hakemiston omistaja. Tähän käytin komentoa `sudo chown danewsgi:danewsgi /home/danewsgi/public_wsgi`.*

*Tämän jälkeen muutin oikeuksia vielä siten, että ryhmällä on luku-, kirjotus- ja ajo-oikeudet. Tähän käytin komentoa `sudo chmod g=rwxs /home/danewsgi/public_wsgi`. Sitten vielä tarkistin oikeudet ls -ld /home/danewsgi/public_wsgi -komennolla.*

![kuva](https://user-images.githubusercontent.com/77921212/134495722-231627e5-84a8-45b2-9904-9e4d9bb91718.png)

*Tämän jälkeen kokeilin udelleen curl localhost -komentoa, joka näytti tällä kertaa 404, eli not found.*

![kuva](https://user-images.githubusercontent.com/77921212/134496067-21826eda-d85f-4fde-b93e-f64d4c780083.png)

*Tämän jälkeen tein vielä `sudo tail -l /var/log/apache2/error.log` -komennon*

![kuva](https://user-images.githubusercontent.com/77921212/134503711-e9a24fce-2da3-4315-b4b7-86371dad5c65.png)

*Viestistä voi tulkita, että kyseistä tiedostoa ei ole olemassa.*

*Seuraavaksi lähdin luomaan uutta tiedostoa nanolla, mutta huomasin, että tiedostoon on vain lukuoikeudet. Päättelin tästä, että luotu ryhmä "danewsgi" ei ole vielä aktivoitunut, joten kirjauduin ulos käyttäjältä ja kirjauduin uudelleen sisään.*

*Tämän operaation jälkeen tiedoston avaaminen täysillä oikeuksilla onnistui.*

*Tiedoston sisään kirjoitin seuraavanlaisesti:

![kuva](https://user-images.githubusercontent.com/77921212/134506886-564d1b5b-f7b3-4261-8182-6feed6ad3274.png)

*lisäsin oman wsgi-polun Pythonin poluksi ja importoin kohta luodun sovelluksen. Teron ohjeiden (lähde 2) mukaan tein vielä assertionin, jolla sain tarvittaessa virhe koodin jos Python 3 koodi tulkitaan Python 2 koodina. Tämän jälkeen tallensin ja kokeilin jälleen uudelleen localhostin tulostamista komentoriville.*

![kuva](https://user-images.githubusercontent.com/77921212/134507696-5a79200e-df0c-4d52-811d-eea58f8dc6be.png)

*Tästä seurasi Internal Server Error. Se tarkoittaa sitä, että palvelin kyllä tunnistaa kansion, mutta sen sisällä ei ole vielä mitään mitä näyttää. Tämän jälkeen tein vielä lopuksi viime tehtävässä nähdyn Hello Flask -sovelluksen, mutta tällä kertaa palvelimen pyörittämänä. Sovelluksen loin `nano /home/danewsgi/public_wsgi/hello.py` -komennolla.*

![kuva](https://user-images.githubusercontent.com/77921212/134508793-4fd96235-5f32-4bb4-b57c-210e5c670b6c.png)

*Tämän jälkeen kokeilin tulostaa sovelluksen sisällön `curl localhost` -komennolla.*

![kuva](https://user-images.githubusercontent.com/77921212/134509136-218971a6-cd7c-4e10-bc6c-a3356666c576.png)

*Äsköisen toimenpiteen jälkeen avasin localhostin vielä palvelimessa.*

![kuva](https://user-images.githubusercontent.com/77921212/134509375-962a1d1b-6542-4932-88e8-346286eabec8.png)

*Tästä voidaan vetää johtopäätös, että Flask toimii halutulla tavalla. Lopuksi muutin vielä luomani hello-sovelluksen sisältöä seuraavasti.*

![kuva](https://user-images.githubusercontent.com/77921212/134514265-8d488bef-31fb-44cb-8b36-6736d1c8088d.png)

*Lopuksi tein vielä `touch dane.wsgi` -komennon, jolla ajoin python tiedoston käynnistämättä apachea uudestaan ja kokeilin päivittyikö sivu halutulla tavalla. Tiedosto muuttui niin kuin halusin.*

![kuva](https://user-images.githubusercontent.com/77921212/134516223-1d0e85c2-8f46-4c26-a6f3-d04952988cb0.png)

































































