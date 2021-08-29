# Viikko 1

### Tällä viikolla aloitettiin kurssi asentamalla Linux VirtualBoxille. Päivämääränä 24.8.2021 Ladattiin Tero Karvisen nettisivulta tarvittavat ohjelmat: Debian Iso Image ja VirtualBox, eli virtuaalinen tietokone, jolla Linux pyörii. Asensin VirtualBoxissa 64 bittisen Debian Linuxin. Asetin virtuaaliselle välimuistille kapasiteetiksi 4000 megatavua ja 50 gigaa tallennustilaa virtuaaliselle kovalevylle. VirtualBoxin käynnistyksen yhteydessä tuli alussa yleinen "black screen" -ongelma. Tämän sain korjattua poistamalla tallennus -osiosta löytyvän Controller: IDE liitteen.

### Seuraavaksi 25.8.2021 listasin 'sudo lshw -short -sanitize' -komennolla koneen raudan. Aluksi tuli ilmoitus, että komentoa ei ole olemassa. Sitten käytin "sudo apt-get install lshw" -komentoa, jotta saan tarvittavan asennuspaketin tietojen näyttämiseen. Listauksessa näkyi kaikki virtuaalisen tietokoneen tiedot yksitellen mm. RAM-muisti, levytila ja prosessori. Alla kuva kyseisestä listasta.

![image](https://user-images.githubusercontent.com/77921212/131260390-e016aa6c-681a-49b4-860e-342243965fb6.png)

### Jatkoin samana päivänä vielä Linux-työskentelyä asentamalla Gimpin, joka on siis ilmainen kuvankäsittelyohjelma. Asensin Gimpin komennolla "sudo snap install gimp". Seuraavaksi asensin ohjelman nimeltä Pydf. Kyseisellä ohjelmalla näkee näppärästi esimerkiksi tietokoneen jäljellä olevan kovalevytilan. Käytin asennukseen komentoa "sudo apt install pydf". Viimeiseksi asensin vielä Inkspacen, joka on ohjelma, jossa voi tehdä vektorigrafiikkaa. Käytin asennukseen "sudo apt-get -y install inkscape" -komentoa. Kaikki ohjelmat toimivat sujuvasti käyttötarkotuksessaan.

### Lisensseistä mainittakoon se, että Gimp käyttää GPL-3.0-or-later -lisenssiä, Inkspace -ohjelma käyttää GNU GENERAL PUBLIC LICENSE -nimistä lisenssiä ja Pydf -ohjelma käyttää PSFL -lisenssiä. Kaikista linsensseistä löytyi tietona, että ohjelmia voi jakaa maksutta, sillä ne ovat ilmaisia. Kopiointi ja esiintyminen ohjelmiston tekijöinä tosin on ehdottomasti kielletty.

### Omassa arjessani Windowsin tietokoneella käytän ahkerasti Discord -ohjelmaa (sosiaalinen viestintä ja verkostoituminen), Spotifytä (äänitiedostojen striimaus) ja Chromea (verkkoselailu). Linuxille löytyy korvikkeina Discordille Riot, joka on open-source viestintäohjelma. Spotifylle puolestaan löytyy Nuvola Player, mitä tituleerataan melkein yhtä tasokkaaksi kuin Windows-vastikkeensa. Chromelle paras Linux vastike on Mozilla Firefox.

<br />
<br />

#### Lähteet:
#### https://terokarvinen.com/2021/install-debian-on-virtualbox/
#### https://wiki.inkscape.org/wiki/index.php/Installing_Inkscape
#### https://www.howtoinstall.me/ubuntu/18-04/pydf/
#### https://snapcraft.io/install/gimp/ubuntu
#### https://en.wikipedia.org/wiki/GIMP
#### https://en.wikipedia.org/wiki/Inkscape
#### https://en.wikipedia.org/wiki/Python_Software_Foundation_License
#### https://itsfoss.com/open-source-browsers-linux/
#### https://www.addictivetips.com/ubuntu-linux-tips/discord-alternatives-for-linux-gamers/
#### https://ubunlog.com/en/nuvola-player-el-spotify-de-linux/#:~:text=Nuvola%20Player%20on%20Linux%20Spotify&text=Nuvola%20Player%20is%20a%20Streaming,nothing%20to%20send%20to%20Spotify.


