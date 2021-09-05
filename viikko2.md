# Linuxin peruskäyttö


*Sain tiistaina 31.8 oppituntien jälkeen onnistuneen toimenpiteen näkymään system.logissa tehtyäni*
`echo "Testiviesti" | systemd-cat`<sup>1</sup> *-komennon rootista.*

`sudo tail -f /var/log/syslog`<sup>1</sup> *-komennolla pääsin tarkastelemaan miltä toimenpide näyttää järjestelmän logissa. Viestin voi lukea alla näkyvän kuvan viimeiseltä riviltä*

![image](https://user-images.githubusercontent.com/77921212/132124635-fb1a8568-ae2c-4a24-8505-a24ef7b55ce5.png)

*Toisen ilmoituksen sain käyttämällä `sudo apt update` -komentoa saatavilla olevien pakettien päivittämiseen, mutta salasanaa kysyttäessä annoin tarkoituksella väärän salasanan. Alla näkyvässä logissa näkyy päivämäärä ja kellonaika sekunnin sadasosan tarkkuudella. Viestistä voi myös lukea ilmoituksen laadun: “authentication failure”. Tein yllä olevan toimenpiteen auth.logissa, jonne tallentuu kaikki tunnistautumiseen liittyvät virhetilanteet.*

![image](https://user-images.githubusercontent.com/77921212/132124739-79fe8d29-2067-4764-b918-372930bfb347.png)
\
&nbsp;

*Toisessa tehtävässä päädyin lataamaan Steamin, johon liittyy paljon mukavia muistoja nuoruudesta. Steamin asennus ei tapahtunut pelkästään yhdellä komennolla. Ensin täytyi lisätä jatkeeksi “non-free” -komponentti `/etc/apt/sources`<sup>2</sup> -tiedostoon. Avasin tiedoston `sudo nano /etc/apt/sources.list`<sup>2</sup> -komennolla ja sitten liitin rivin `deb http://deb.debian.org/debian/ buster main contrib non-free`<sup>2</sup> tiedoston loppuun.*

*Tämän jälkeen täytyi aktivoida “Multi-Arch” komennolla `sudo dpkg --add-architecture i386`<sup>2</sup>. Multi-Arch on olennainen osa Debianin riippuvuuksien ja pakettien asennusta 32- ja 64-bittisille järjestelmille. Koska pelit pyörivät parhaiten 32-bittisenä Steamissa, niin yllä mainitulla komennolla saadaan järjestelmään 32 bit tuki<sup>2</sup>. Tämän jälkeen tein vielä “sudo apt update” -komennon, jolla päivitin järjestelmän saatavilla olevat paketit. Tämän jälkeen pääsin vihdoin `sudo apt install steam`<sup>2</sup> -komennon pariin. Asennuksessa kesti tovi, koska Steam on kooltaan lähestulkoon puoli gigatavua. Tämän jälkeen käynnistin Steamin: Applications --> Games --> Steam. Ohjelma avautui loistavasti. Pääsin selailemaan vanhoja aarteitani ja kaupan uutuuksia.*

![image](https://user-images.githubusercontent.com/77921212/132125046-10397d5d-23f2-4e65-b325-cd30dec3527e.png)
\
&nbsp;

*Kolmannessa tehtävässä asensin ensimmäiseksi Audacity ohjelman, jolla voi äänittää ja muokata ääniraitoja. Löysin internetistä, että asennus on järkevintä "snap" –paketinhallinnan kautta<sup>3</sup>. Tein ensin komennon `sudo apt update`<sup>3</sup>. Seuraavaksi tein `sudo apt install snapd`<sup>3</sup> -komennon, jolla asensin "snap"-paketinhallinnan virtuaaliselle koneelle. Tämän jälkeen täytyi tehdä vielä `sudo snap install core`<sup>3</sup> -komento, jolla sain aktivoitua snapin tarjoamat hyödyt paketinhallinnassa. Tämän jälkeen pääsin asentamaan itse ohjelman snapin tuella: `sudo snap install audacity`<sup>3</sup>. Tämän jälkeen käynnistin Audacityn `snap run audacity &`<sup>3</sup> -komennolla. Ohjelman avaaminen oli kuin kurkistus 90-luvulle.*

![image](https://user-images.githubusercontent.com/77921212/132125212-5a48525f-a81a-47c4-8119-acb6307f5794.png)

*Seuraavaksi latasin shotcutin, joka on wikipedian mukaan ilmainen open source videon editointi ohjelma<sup>4</sup>. Käytin jälleen "snap" –paketinhallintaa ohjelman asennukseen, koska siihen löytyi heti hyvät ohjeet<sup>5</sup>. Tein taas `sudo apt update` -komennon, jolla päivitettiin saatavilla olevat paketit. Sitten asensin "shotcut" –ohjelman `sudo snap install shotcut –classic`<sup>5</sup> -komennolla. Pääsin tarkastelemaan sovellusta  tutulla `snap run shotcut &` -komennolla. Ohjelma oli käyttöliittymältään ja ulkonäöltään Audacityä modernimpi ja helpompikäyttöisempi.*

![image](https://user-images.githubusercontent.com/77921212/132125380-d1bdbe21-79aa-4a53-bc55-77d97cd2a5f5.png)

*Viimeiseksi asensin "Geeksforgeeks" -sivun artikkelin<sup>6</sup> suosittelemana ClamAV nimisen anti-virus ohjelman. Asennus saatiin aikaan `sudo apt-get install clamav clamav-daemon`<sup>7</sup> -komennolla. Sovelluksella ei ole graafista käyttöliittymää, joten kaikki toiminnot tapahtuvat komentoriviltä käsin. Kokeilin sovellusta skannaamalla yhden Python tiedostoni `clamscan postitoimipaikka.py`<sup>7</sup> -komennolla. Vaikka ohjelma on melko yksinkertainen, siitä voi olla paljonkin hyötyä järjestelmän pitämisessä puhtaana haittaohjelmista.
\
&nbsp;

*Aloitin tehtävien teon hyvissä ajoin jo 31.8 oppituntien jälkeen. Tein tehtäviä kolmena päivänä: tiistaina, perjantaina sekä sunnuntaina. Kaiken kaikkiaan aikaa kului noin viisi ja puoli tuntia.*

\
&nbsp;
\
&nbsp;



## Lähteet:
&nbsp;

| Lähdenumero | Linkki |
| ----------- | ---------------------------------------------------------------|
| 1   | https://devconnected.com/linux-logging-complete-guide/                 |
| 2   | https://servonode.com/install-steam-on-debian-10-11                    |
| 3   | https://snapcraft.io/install/audacity/debian                           |
| 4   | https://en.wikipedia.org/wiki/Shotcut                                  |
| 5   | https://snapcraft.io/install/shotcut/ubuntu                            |
| 6   | https://www.geeksforgeeks.org/top-20-linux-applications-to-use-in-2021 |
| 7   | https://wiki.debian.org/ClamAV                                         |















