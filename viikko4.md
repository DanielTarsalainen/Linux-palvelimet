### Tehtävänanto

*a) Vuokraa oma julkinen palvelin Internetiin. Vinkkejä: Perustele tehdyt valinnat. Voit saada myös ilmaiseksi Github Education -paketilla. Jos sinulla on aiempi palvelin, tee uusi alusta lähtien ja raportoi samalla. Käytä aina hyviä salasanoja.*

*ax) Vaihtoehtotehtävä, korvaa kohdan a. Suosittelen mieluummin tekemään a-kohdan, se on paljon hyödyllisempi. Kokeile virtuaalikoneiden tekoa vagrant:lla omalla paikallisella koneellasi. Sovella muut kohdat (b, c...) siten, että ne toimivat paikallisen koneen kanssa: esim testaa weppsivut paikallisesti curlilla, simuloi hyökkäys syöttämällä väärä salasana omaan ssh-palvelimeesi jne.*

*b) Suojaa palvelin tulimuurilla. Muista ensin reikä ssh-palvelimelle.*

*c) Laita koneellesi Apache-weppipalvelin. Korvaa testisivu. Laita käyttäjän kotisivut toimimaan. Kokeile eri koneelta, esim. kännykällä, että sivut toimivat. Vinkki: tee kotisivut normaalina käyttäjänä public_html/ alle, opettelemme "name based virtual hosting" myöhemmin.*

*d) Etsi lokeistasi merkkejä murtautumisyrityksistä ja analysoi ne. Vinkki: auth.log.*






*b) `ssh root@178.128.245.233` -komentoa käytin ssh:n rei'ityykseen. Tämän jälkeen tuli varmistusviesti (yes tai no). Sitten pyydettiin palvelimen salasanaa. Sen jälkeen kun syötin salasanan oikein, päivitin saatavilla olevat paketit `sudo apt-get update` -komennolla ja päivitin saatavilla olevat paketit. Tämän jälkeen annoin `sudo apt-get upgrade` -komennon, jolla päivitin kaikki paketit. `sudo apt-get install ufw`-komennolla asensin tulimuuri. `sudo ufw allow 22/tcp` -komennolla tein ja sitten aktivoin reiän komennolla `sudo ufw enable`. Tämän jälkeen tein uuden käyttäjän 'leinad', jolle annoin admin oikeudet


