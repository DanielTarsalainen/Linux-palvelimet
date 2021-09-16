### Tehtävänanto

*a) Vuokraa oma julkinen palvelin Internetiin. Vinkkejä: Perustele tehdyt valinnat. Voit saada myös ilmaiseksi Github Education -paketilla. Jos sinulla on aiempi palvelin, tee uusi alusta lähtien ja raportoi samalla. Käytä aina hyviä salasanoja.*

*b) Suojaa palvelin tulimuurilla. Muista ensin reikä ssh-palvelimelle.*

*c) Laita koneellesi Apache-weppipalvelin. Korvaa testisivu. Laita käyttäjän kotisivut toimimaan. Kokeile eri koneelta, esim. kännykällä, että sivut toimivat. Vinkki: tee kotisivut normaalina käyttäjänä public_html/ alle, opettelemme "name based virtual hosting" myöhemmin.*

*d) Etsi lokeistasi merkkejä murtautumisyrityksistä ja analysoi ne. Vinkki: auth.log.*

c) Tämän jälkeen tein sudo apt-get update komennon, jolla päivitin saatavilla olevat paketit. Tämän jälkeen asensin apache2 -palvelimen: sudo apt-get install apache2. Vielä tarvitsi tehdä reikä tulimuuriin, jotta sivulle pääsy olisi mahdollista. Lopuksi käynnistin apache2 palvelimen sudo systemctl start apache2 -komennolla. Apachen oletussivu tuli onnistuneesti näkyviin. Alla kuva kyseisestä tapahtumasta.

Tämän jälkeen lähdin muuttamaan Apache2 oletussivun omaksi nettisivukseni. Tein kopion etc/apache2/sites-available kansion 000-default.conf tiedostosta --> leinadsite.conf. leinadsite.conf sivulla muutin asetuksia: 

Tämän jälkeen otin uudet configuraatiot käyttöön: Käynnistin apache2 palvelimen uudestaan sudo systemctl start apache2 -komennolla, jonka jälkeen päivitin palvelimen sudo systemctl reload apache2 -komennolla. 

Tämän jälkeen tein omaan kotihakemistoon uuden kansion nimeltä public_html ja loin sinne tiedoston nimellä index.html. Sinne kirjotin tekstin "Palvelin toimii juhuu!" 





*b) `ssh root@178.128.245.233` -komentoa käytin ssh:n rei'ityykseen. Tämän jälkeen tuli varmistusviesti (yes tai no). Sitten pyydettiin palvelimen salasanaa. Sen jälkeen kun syötin salasanan oikein, päivitin saatavilla olevat paketit `sudo apt-get update` -komennolla ja päivitin saatavilla olevat paketit. Tämän jälkeen annoin `sudo apt-get upgrade` -komennon, jolla päivitin kaikki paketit. `sudo apt-get install ufw`-komennolla asensin tulimuuri. `sudo ufw allow 22/tcp` -komennolla tein ja sitten aktivoin reiän komennolla `sudo ufw enable`. Tämän jälkeen tein uuden käyttäjän 'leinad', jolle annoin admin oikeudet


