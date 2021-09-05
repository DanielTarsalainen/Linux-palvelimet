# Linuxin peruskäyttö


### Tehtävät: 
*1) Aiheuta lokiin kaksi eri tapahtumaa: yksi esimerkki onnistuneesta ja yksi esimerkki epäonnistuneesta tai kielletystä toimenpiteestä. Analysoi rivit yksityiskohtaisesti.*
*2) Tee unelmien apt-get -komento: yksi komentorivi, joka asentaa suosikkiohjelmasi.*
*3) Asenna komentokehotteen paketinhallinnasta kolme itsellesi uutta komentorivillä toimivaa ohjelmaa. Kokeile kutakin ohjelmaa sen pääasiallisessa käyttötarkoituksessa.*<sup>8</sup>

\
&nbsp;


*Sain tiistaina 31.8 oppituntien jälkeen onnistuneen toimenpiteen näkymään system.logissa tehtyäni*
`echo "Testiviesti" | systemd-cat`<sup>1</sup> *-komennon rootista.*

`sudo tail -f /var/log/syslog`<sup>1</sup> *-komennolla pääsin tarkastelemaan miltä toimenpide näyttää järjestelmän logissa. Viestin voi lukea alla näkyvän kuvan viimeiseltä riviltä*

![image](https://user-images.githubusercontent.com/77921212/132124635-fb1a8568-ae2c-4a24-8505-a24ef7b55ce5.png)

*Toisen ilmoituksen sain käyttämällä `sudo apt update` -komentoa saatavilla olevien pakettien päivittämiseen, mutta salasanaa kysyttäessä annoin tarkoituksella väärän salasanan. Alla näkyvässä logissa näkyy päivämäärä ja kellonaika sekunnin kymmenesosan tarkkuudella. Viestistä voi myös lukea ilmoituksen laadun: “authentication failure”. Tein yllä olevan toimenpiteen auth.logissa, jonne tallentuu kaikki tunnistautumiseen liittyvät virhetilanteet.*

![image](https://user-images.githubusercontent.com/77921212/132124739-79fe8d29-2067-4764-b918-372930bfb347.png)
\
&nbsp;

*Toisessa tehtävässä päädyin lataamaan Steamin, johon liittyy paljon mukavia muistoja nuoruudesta. Steamin asennus ei tapahtunut pelkästään yhdellä komennolla. Ensin täytyi lisätä jatkeeksi “non-free” -komponentti `/etc/apt/sources`<sup>2</sup> -tiedostoon. Avasin tiedoston `sudo nano /etc/apt/sources.list`<sup>2</sup> -komennolla ja sitten liitin rivin `deb http://deb.debian.org/debian/ buster main contrib non-free`<sup>2</sup> tiedoston loppuun.*

*Tämän jälkeen täytyi aktivoida “Multi-Arch” komennolla `sudo dpkg --add-architecture i386`<sup>2</sup>. Multi-Arch on olennainen osa Debianin riippuvuuksien ja pakettien asennusta 32- ja 64-bittisille järjestelmille. Koska suurin osa Steamin peleistä tukee 32-bittistä järjestelmää, niin yllä mainitulla komennolla saadaan järjestelmään 32-bit tuki<sup>2</sup>. Tämän jälkeen tein vielä “sudo apt update” -komennon, jolla päivitin järjestelmän saatavilla olevat paketit. Tämän jälkeen pääsin vihdoin `sudo apt install steam`<sup>2</sup> -komennon pariin. Asennuksessa kesti tovi, koska Steam on kooltaan lähestulkoon puoli gigatavua. Tämän jälkeen käynnistin Steamin: Applications --> Games --> Steam. Ohjelma avautui loistavasti. Pääsin selailemaan vanhoja aarteitani ja kaupan uutuuksia.*

![image](https://user-images.githubusercontent.com/77921212/132125046-10397d5d-23f2-4e65-b325-cd30dec3527e.png)
\
&nbsp;

*Kolmannessa tehtävässä asensin ensimmäiseksi Fzf nimisen ohjelman, jota käytetään ohjelmien nopeaan hakemiseen<sup>3</sup>. Käytin asentamiseen komentoa `sudo apt install fzf`<sup>3</sup>. Ohjelman sai käynnistettyä kirjoittamalla vaan haluttuun polkuun `fzf`<sup>3</sup>. Itse tein haun "Home" -hakemistossa. Seuraavaksi näytölle ilmestyi kansion kaikki tiedostot ja punainen nuoli, jolla voi valita tietyn tiedoston. Työkalu on siitä näppärä, että kansion sisällä ei tarvitse erikseen listata tiedostoja, vaan ne näkee heti ruudulla.*

![image](https://user-images.githubusercontent.com/77921212/132128031-b8f4b093-1381-4249-9f03-b978151b8752.png)

Toiseksi ohjelmaksi valitsin "Wikit" -nimisen ohjelman, jolla voi tehdä Wikipedia hakuja komentoriviltä käsin<sup>4</sup>. Ennen ohjelman asennusta, virtuaalikoneelle piti asentaa "nodejs", joka on ajoympäristö Javascript koodin suorittamiselle<sup>5</sup>. Asennus tehtiin tutulla `sudo apt install nodejs`<sup>4</sup> -komennolla. Tämän jälkeen asensin Wikit -ohjelman `sudo npm install wikit -g`<sup>4</sup> -komennolla. Ohjelman ajaminen toimi pitkälti samalla tavalla kuin edellisen kohdalla. Komentoriville tuli vain kirjoittaa `wikit {jokin hakusana}`<sup>4</sup>. Itse hain Linus Torvaldsia, ja ohjelma toi minulle pienen tiivistelmän Wikipedia-artikkelista. 

![image](https://user-images.githubusercontent.com/77921212/132127845-2d7dbca7-fd68-4bf5-80c5-261287d0deee.png)

*Viimeiseksi asensin "Geeksforgeeks" -sivun artikkelin<sup>6</sup> suositteleman ClamAV nimisen anti-virus ohjelman. Asennus saatiin aikaan `sudo apt-get install clamav clamav-daemon`<sup>7</sup> -komennolla. Kokeilin sovellusta skannaamalla yhden Python tiedostoni `clamscan postitoimipaikka.py`<sup>7</sup> -komennolla. Vaikka ohjelma on melko yksinkertainen, siitä voi olla paljonkin hyötyä järjestelmän pitämisessä puhtaana haittaohjelmista.*
\
&nbsp;

*Aloitin tehtävien teon hyvissä ajoin jo 31.8 oppituntien jälkeen. Tein tehtäviä kolmena päivänä: tiistaina, perjantaina sekä sunnuntaina. Kaiken kaikkiaan tehtäviin kului noin viisi ja puoli tuntia.*

\
&nbsp;
\
&nbsp;



### Lähteet:
&nbsp;

| Lähdenumero | Linkki |
| ----------- | ------------------------------------------------------------------------- |
| 1   | https://devconnected.com/linux-logging-complete-guide/                            |
| 2   | https://servonode.com/install-steam-on-debian-10-11                               |
| 3   | https://www.addictivetips.com/ubuntu-linux-tips/useful-linux-command-line-apps/   |
| 4   | https://www.tecmint.com/wikipedia-commandline-tool/                               |
| 5   | https://fi.wikipedia.org/wiki/Node.js                                             |
| 6   | https://www.geeksforgeeks.org/top-20-linux-applications-to-use-in-2021            |
| 7   | https://wiki.debian.org/ClamAV                                                    |
| 8   | https://terokarvinen.com/2021/linux-server-course-linux-palvelimet-ict4tn021-3016/|                                               
















