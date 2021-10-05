# H6 Shell scriptit, bash-skriptaus.
####  Tekijä: Daniel Tarsalainen 

\
&nbsp;

## Tehtävänanto


- [x]  a) Uusi komento Linuxiin. Tee uusi komento, joka tulostaa käyttäjälle hyödyllistä tietoa. Kokeile, että komento toimii kaikista hakemistoista ja muillakin käyttäjillä kuin omallasi<sup>1</sup>

- [x]  b) Parametreja. Tee skripti, joka ottaa komentoriviparametreja. Esim. 'greetuser Tero' joka tulostaa "moi" ja parametrinä olevan nimen, esim "moi Tero"<sup>1</sup>

- [x]  c) Monta polkua. Tee Flask-ohjelma, jossa on useampi polku. Esim "localhost:5000/foo" näyttää sivun, jolla lukee "Foo" ja "localhost:5000/bar" näyttää sivun, jolla lukee "Bar". Voit käyttää testipalvelinta<sup>1</sup>
  
- [x] d) Muotti. Tulosta Flaskilla sivu muotista. Voit käyttää testipalvelinta<sup>1</sup>


\
&nbsp;


#### a) Uusi komento Linuxiin. Tee uusi komento, joka tulostaa käyttäjälle hyödyllistä tietoa. Kokeile, että komento toimii kaikista hakemistoista ja muillakin käyttäjillä kuin omallasi<sup>1</sup>
*Aloitin tehtävien tekemisen luomalla uuden kansion kotihakemistooni komennolla `$ mkdir linux_skriptit`. `linux_skriptit` -kansioon loin uuden tieston nimellä `showdate`. `showdate` -tiedostoon kirjoitin ensitöikseen, että skripti ajetaan käyttämällä bashia tulkkina. Itse skripti oli seuraavanlainen:*

![kuva](https://user-images.githubusercontent.com/77921212/135107423-2f265be2-1767-4af1-b53b-a36f4201c29c.png)

*Määritin siis kolme muuttujaa, jotka (alhaalta ylös) tulostavat päivämäärän, kellonajan ja viikkonumeron. Käytin skriptin kirjoittamisessa hieman apuna stackoverflon keskustelua <sup>2</sup>*

*Tämän jälkeen tallensin tiedoston `CTRL X` komennolla ja käynnistin juuri luomani skriptin.*

![kuva](https://user-images.githubusercontent.com/77921212/135108796-6afc5537-c965-432b-b6a9-ddc27f57bc77.png)

*Sitten lähdin muuttamaan tiedoston oikeuksia chmodilla. Muutin oikeuksia siten, että käyttäjällä, ryhmällä ja muilla on lukuoikeuden lisäksi ajo-oikeus. Tähän tarvittiin komento `chmod ugo+x ekaskripti`*

![kuva](https://user-images.githubusercontent.com/77921212/135108542-9b1c4793-d04e-44e8-9b96-a0855723af18.png)

*Tämän jälkeen kopioin vielä tiedoston `/usr/local/bin` -hakemistoon, mikä mahdollistaa sen, että skriptiä voi käyttää mistä vain. Käytin siihen komentoa `sudo cp -v showdate /usr/local/bin`.*

Tämän jälkeen tuli seuraavanlainen ilmoitus terminaaliin:*
> 'showdate' -> '/usr/local/bin/showdate'

*Ylläolevasta ilmoituksesta voi tulkita, että "showdate" tiedosto on kopioitu kyseiseen hakemistoon onnistuneesti*

*Lopuksi vielä kokeilin käynnistää skriptin rootin etc hakemistosta, että käyttäjän danskubansku kotihakemistosta:*

![kuva](https://user-images.githubusercontent.com/77921212/135110072-ec78b6a5-1670-42c9-989d-c85e093e8b1e.png)

*Myös käyttäjän "joonatan" -hakemistosta skriptin ajaminen onnistui.*

![kuva](https://user-images.githubusercontent.com/77921212/135116872-d4132d3b-a0fd-4046-b5d4-02cdc071ff9b.png)


*Tästä voidaan todeta, että skriptiä voi todellakin käyttää mistä sijainnista tahansa.*


\
&nbsp;


#### b) Parametreja. Tee skripti, joka ottaa komentoriviparametreja. Esim. 'greetuser Tero' joka tulostaa "moi" ja parametrinä olevan nimen, esim "moi Tero"<sup>1</sup>

*Aloitin skriptin kirjottamisen luomalla uuden tiedoston viime tehtävässä luotuun `linux_skriptit` -kansioon. Loin greet_user tiedoston komennolla `nano greet_user`. Tiedoston sisään kirjotin kyseisen rivin:*

![kuva](https://user-images.githubusercontent.com/77921212/135120634-18cdcb0e-805f-492e-ab9f-cf33d1a71023.png)

*Skripti toimi niinkuin halusin*

![kuva](https://user-images.githubusercontent.com/77921212/135120942-e2a21fb4-6d61-4ec5-b58e-0d31d53da5b7.png)


\
&nbsp;


#### c)  Monta polkua. Tee Flask-ohjelma, jossa on useampi polku. Esim "localhost:5000/foo" näyttää sivun, jolla lukee "Foo" ja "localhost:5000/bar" näyttää sivun, jolla lukee "Bar". Voit käyttää testipalvelinta<sup>1</sup>

*Tein uuden Flask-ohjelman kotihakemistossani sijaitsevaan flask-kansioon. Lisäsin tiedostoon kome eri polkua: "/greeting", "/about" ja "/faq".*

![kuva](https://user-images.githubusercontent.com/77921212/135755218-d341637b-961d-4edb-9259-017d6d985c7e.png)

*Tiedoston tallentamisen jälkeen ajoin ohjelman `python3 test.py` -komennolla, ja menin tarkastelemaan miltä sivut näyttävät testipalvelimella.* 

![kuva](https://user-images.githubusercontent.com/77921212/135755335-24294d59-0fff-4fee-b647-94457d2ad832.png)

*Avasin sivun painamalla linkin kohdalta hiiren vasenta klikkiä ja `ctrl` -näppäintä samaanaikaan pohjassa. Tämän jälkeen avautui testipalvelimen oletussivu, joka näytti tällä kertaa virhettä 404, eli not found, koska etusivua ei ollut määritetty:*

![kuva](https://user-images.githubusercontent.com/77921212/135755491-70d8e372-d4fe-4e0c-bf54-991cc09ac676.png)

*Kun kirjotin hakukenttään poluksi "greeting", niin selaimeen ilmestyi haluamani sivu. Samoin kävi "about"- ja "faq" -sivujen kanssa.*

![kuva](https://user-images.githubusercontent.com/77921212/135755569-9ac80b50-9336-4aab-8aba-e13238d58e4f.png)

![kuva](https://user-images.githubusercontent.com/77921212/135755593-838c26de-1c33-4d2b-b9e6-c04ee1d4b6e6.png)

![kuva](https://user-images.githubusercontent.com/77921212/135755577-9c9e171d-0d89-473d-bb3e-712fb0384778.png)

\
&nbsp;


#### d) Muotti. Tulosta Flaskilla sivu muotista. Voit käyttää testipalvelinta<sup>1</sup>

*Tein tuttuun flask-kansiooni uuden tiedoston nimeltä `flask_app.py`, jonka sisään kirjoitin seuraavanlaisesti:*

![kuva](https://user-images.githubusercontent.com/77921212/135756240-a0cc89c5-c266-42a0-bfbc-097313991438.png)

*Tällä kertaa flaskin lisäksi täytyi importoida render_template-metodi sekä request-metodi. Päättelin, että funktion ekat kaksi riviä tarkistavat lähetetäänkö kirjoituskentän syötettä "side". Funktion paluuarvoksi "return" asetin renderöitävksi "whatsup.html" -sivun. `app.run(debug=True` -rivin lisäsin sen takia, että ohjelmaa voi helposti kokeilla testipalvelimella. Endpointiksi asetin "/", mikä tarkoittaa sitä, että sivulle pääsee suoraan testipalvelimen etusivulta.*

*Tämän jälkeen tallensin sivun ja lähdin luomaan "whatsup.html" -sivua samaan flask hakemistoon komennolla `nano whatsup.html`.*

![kuva](https://user-images.githubusercontent.com/77921212/135756805-3429c933-a10f-4fce-9bdd-23bb281005d5.png)

*Sivun sisälle tein validin HTML-rakenteen ja tekstikentän, jonka metodiksi asetin "POST", tarkoittaen, että tekstikentän avulla voi lähettää jotakin tekstiä*

*Tämän jälkeen käynnistin python flask ohjelman komennolla `python3 flask_app.py`. Tästä seurasi virhe:*

>  File "/home/danskubansku/flask/flask_app.py", line 9
>    print(request.form["side"])
> TabError: inconsistent use of tabs and spaces in indentation

*Menin tämän jälkeen tarkistamaan mitä olin kirjoittanut väärin rivillä 9.*

*Poistin tyhjän välin ennen funktion määrittämistä ja ajoin tiedoston uudelleen, tämän jälkeen tuli edelleen sama virhe.*

*Avasin tiedoston vielä kerran ja huomasin, että ohjelman viimeisellä rivillä on tyhjä välilyönti ennen "app.run" -kohtaa. Poistin tyhjän välilyönnin ja ajoin ohjelman vielä kertaalleen `python3 flask_app.py` -komennolla.* 

> python3 flask_app.py
> File "/home/danskubansku/flask/flask_app.py", line 9
> return render_template("whatsup.html")
>                                       ^
> IndentationError: unindent does not match any outer indentation level

*Nyt tuli paljon selkeämpi virheilmoitus. Avasin tiedoston vielä kertaalleen ja kirjotin uudelleen koko whatsup-funktion sisällön. Tallensin ja ajoin tiedoston uudelleen. Nyt ohjelma käynnistyi moitteetta, eli kyseessä oli mahdollisesti jokin debianin bugi*

![kuva](https://user-images.githubusercontent.com/77921212/135757753-991fc278-73ca-45d9-9145-bec426f04db3.png)

*Virheitä tuli tämän jälkeen lisää. Portin 5000 etusivulle tuli vihre, että "name "requst" is not defined".*

![kuva](https://user-images.githubusercontent.com/77921212/135757848-fa102f57-7fc1-48f7-a1ab-df59604b5989.png)

*Kyseessä oli siis kirjoitusvirhe. Menin seuraavaksi korjaamaan kyseisen virheen python tiedostosta ja käynnistin ohjelman uudelleen. Ohjelma käynnistyi onnistuneesti, mutta sivulle ilmestyi taas virhe, joka väitti, että whatsup.html -nimistä templatea ei ole olemassa. Päättelin tästä, että html-tiedosto ei ole oikeassa hakemistossa. Tein hieman tutkimustyötä, ja flask.palletproject -sivulla<sup>3</sup> näkyvästä rakenteesta selvisi, että flask muoteilla työskennellessä täytyy olla spesifi rakenne, joten lähdin tekemään tehtävää uudelleen.*

*Loin uuden kansion nimeltä `flask_project` kotihakemistooni. Kyseiseen hakemistoon tein uuden kansion nimeltä `templates`. Sitten loin kansioon tiedoston nimeltä `whatsup.html`. Kopioin tiedoston sisälle aiemmin luodun sisällön ja tallensin muutokset. Tämän jälkeen menin hakemsistossa taaksepäin `cd ..` komennolla ja loin uuden tiedoston nimeltä `flask_app.py`. Kopioin aiemmin luodun tiedoston sisällön. Tämän jälkeen käynnistin ohjelman komennolla `python3 flask_app.py`.*

*Nyt sivulle viimein ilmestyi oikea sivu:*

![kuva](https://user-images.githubusercontent.com/77921212/135759540-e523055e-f2b6-4389-b675-ce7f1297ee6b.png)

*Kokeilin vielä POST-metodin toimivuutta kirjoittamalla tekstikenttään "Hei sielä" ja painamlla enter-painiketta. Tämän jälkeen avasin kehittäjän työkalut selaimessa F12 painikkeela ja menin "Netwokrk" -osioon. Sielä havaitsin, että POST-pyynnön lähetys oli statukseltaan 200, eli OK. Tästä voidaan todeta, että ohjelma toimi onnistuneesti tämänhetkisessä käyttötarkoituksessaan* 

![kuva](https://user-images.githubusercontent.com/77921212/135759614-0ce5b9fe-6870-4f7b-99c0-c252c4f230a4.png)

\
&nbsp;

## Loppumietteitä

*Tehtävät olivat mielenkiintoisia, mutta d) kohta turhautti. Tästä tosin opin olemaan entistäkin tarkempi tehtävien tekemisessä ja tekemisen suunnittelussa. Tehtäviin kului kaiken kaikkiaan aikaa noin kuusi tuntia.*

\
&nbsp;

## Lähteet


| Lähdenumero | Linkki |
| ----------- | ------------------------------------------------------------------------- |
| 1 | https://terokarvinen.com/2021/linux-server-course-linux-palvelimet-ict4tn021-3016/#peruskaytto                           |
| 2 | https://stackoverflow.com/questions/1401482/yyyy-mm-dd-format-date-in-shell-script                           |
| 3 | https://flask.palletsprojects.com/en/2.0.x/quickstart/#rendering-templates |





























































