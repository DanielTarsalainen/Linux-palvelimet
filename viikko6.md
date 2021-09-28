# H5 Ohjelmat weppipalvelimella, Python Flask
####  Tekijä: Daniel Tarsalainen 

\
&nbsp;

## Tehtävänanto<sup>1</sup>


- [ ]  a) Uusi komento Linuxiin. Tee uusi komento, joka tulostaa käyttäjälle hyödyllistä tietoa. Kokeile, että komento toimii kaikista hakemistoista ja muillakin käyttäjillä kuin omallasi.

- [ ]  b) Parametreja. Tee skripti, joka ottaa komentoriviparametreja. Esim. 'greetuser Tero' joka tulostaa "moi" ja parametrinä olevan nimen, esim "moi Tero".

- [ ]  c) Monta polkua. Tee Flask-ohjelma, jossa on useampi polku. Esim "localhost:5000/foo" näyttää sivun, jolla lukee "Foo" ja "localhost:5000/bar" näyttää sivun, jolla lukee "Bar". Voit käyttää testipalvelinta.
  
- [ ] d) Muotti. Tulosta Flaskilla sivu muotista. Voit käyttää testipalvelinta.


\
&nbsp;


#### a) Uusi komento Linuxiin. Tee uusi komento, joka tulostaa käyttäjälle hyödyllistä tietoa. Kokeile, että komento toimii kaikista hakemistoista ja muillakin käyttäjillä kuin omallasi.
*Aloitin tehtävien tekemisen luomalla uuden kansion kotihakemistooni komennolla `$ mkdir linux_skriptit`. `linux_skriptit` -kansioon loin uuden tieston nimellä `showdate`. `showdate` -tiedostoon kirjoitin ensitöikseen, että skripti ohjautuu`#!/bin/bash` hakemistoon. Itse skripti oli seuraavanlainen:*

![kuva](https://user-images.githubusercontent.com/77921212/135107423-2f265be2-1767-4af1-b53b-a36f4201c29c.png)

*Määritin siis kolme muuttujaa, jotka (alhaalta ylös) tulostavat päivämäärän, kellonajan ja viikkonumeron*

*Tämän jälkeen tallensin tiedoston `CTRL X` komennolla ja käynnistin juuri luomani skriptin.*

![kuva](https://user-images.githubusercontent.com/77921212/135108796-6afc5537-c965-432b-b6a9-ddc27f57bc77.png)


*Sitten lähdin muuttamaan tiedoston oikeuksia chmodilla. Muutin oikeuksia siten, että käyttäjällä, ryhmällä ja muilla on lukuoikeuden lisäksi ajo-oikeus.*

![kuva](https://user-images.githubusercontent.com/77921212/135108542-9b1c4793-d04e-44e8-9b96-a0855723af18.png)

*Tämän jälkeen kopioin vielä tiedoston /usr/local/bin hakemistoon, mikä mahdollitaa sen, että skriptiä voi käyttää mistä vain. Tämän jälkeen tuli seuraavanlainen ilmoitus terminaaliin:*
> 'showdate' -> '/usr/local/bin/showdate'

*Lopuksi vielä kokeilin käynnistää skriptin rootin etc hakemistosta, että käyttäjän perushakemistosta:*

![kuva](https://user-images.githubusercontent.com/77921212/135110072-ec78b6a5-1670-42c9-989d-c85e093e8b1e.png)


\
&nbsp;


#### b) Parametreja. Tee skripti, joka ottaa komentoriviparametreja. Esim. 'greetuser Tero' joka tulostaa "moi" ja parametrinä olevan nimen, esim "moi Tero".


\
&nbsp;


#### c)  Monta polkua. Tee Flask-ohjelma, jossa on useampi polku. Esim "localhost:5000/foo" näyttää sivun, jolla lukee "Foo" ja "localhost:5000/bar" näyttää sivun, jolla lukee "Bar". Voit käyttää testipalvelinta.


\
&nbsp;


#### d) Muotti. Tulosta Flaskilla sivu muotista. Voit käyttää testipalvelinta.

\
&nbsp;

## Loppumietteitä

*Tehtävät olivat mielenkiintoisia, joskin aikaavieviä. Aikaa tehtäviin kului noin kuusi ja puoli tuntia.*

\
&nbsp;

## Lähteet


| Lähdenumero | Linkki |
| ----------- | ------------------------------------------------------------------------- |
| 1 | https://terokarvinen.com/2021/linux-server-course-linux-palvelimet-ict4tn021-3016/#peruskaytto                           |
| 2 | https://stackoverflow.com/questions/1401482/yyyy-mm-dd-format-date-in-shell-script                           |
| 3 |  |
| 4 | |
| 5 |                           |





























































