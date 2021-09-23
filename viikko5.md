## H5


*Tee kukin tehtävä alusta lähtien ja kirjaa samalla, vaikka olisit kokeillut tunnilla. Jos pidät propellihattua, katso kohta x.*

- [ ]  a) Leikkinimi. Tee Apachelle uusi Name Based Virtual Host, ja testaa sitä simuloimalla nimipalvelua hosts-tiedoston avulla.

- [ ] b) Julkinen nimi. Laita julkiselle palvelimellesi julkinen domain-nimi. Käytä oikeaa nimeä (joko vuokrattua tai ilmaispalvelusta). Tee Apachelle Name Based Virtual Host tälle nimelle. Kokeile eri laitteelta (esim. kännykältä), että nimi oikeasti toimii.

- [ ] c) Hello Flask! Tee Python Flask hei maailma kehitysympäristössä. Voit siis käyttää tuotantoon sopimatonta app.run(debug=True) ajoa.

- [ ] d) Tuotanto-Flask. Tee tuotantotyyppinen asennus Flaskista käyttäen Apachen WSGI-modulia. Kokeile, että pystyt muokkaamaan koodia ilman sudoa ja saat uuden version käyttöön käynnistämättä Apachea uudelleen. ('touch foo.wsgi')


### a) Leikkinimi. Tee Apachelle uusi Name Based Virtual Host, ja testaa sitä simuloimalla nimipalvelua hosts-tiedoston avulla.

*Päivitin paketit `sudo apt-get update` -komennolla. Sitten loin `sudo nano index.html` komennolla uuden html tiedoston `var/www/html` -hakemistoon. Seuraavaksi kirjotin `echo "Default" | sudo tee /var/Www/html/index.html` -komennolla kyseiselle sivulle tekstin "Default". Sitten lähdin luomaan uutta nimen sisältävää virtuaalista hostia. Tähän käytin komentoa $ sudoedit /etc/apache2/sites-available/danieltars.com.conf (kuva1).

/
</br>

Tämän jälkeen otin konfiguroinnit käyttöön `sudo a2ensite danieltars.com.conf` -komennolla ja latasin apache2 palvelimen uudestaan `systemctl reload apache2` -komennolla. (kuva2)

`mkdir -p /home/danskubansku/publicsites/danieltars.com` -komennolla tein uuden hakemiston publicsites hakemistoon. 

`echo hei sinä! > /home/danskubansku/publicsites/danieltars.com/index.html` -komennolla tein uuden index.html -tiedoston ja kirjotin siihen tekstin "hei sinä". 


*Lopuksi vielä käynnistin Apache palvelimen uudestaan `sudo systemctl restart apache2` -komennolla.*

*Sitten kokeilin vielä tulostaa nettisivuni sisällön komennolla `curl -H 'Host: danieltars.com' localhost`(kuva3)

*Lopuksi vielä simuloin nettisivulle halutun nimen, eli "danieltars.com". Tein sen "/etc/hosts" -polussa komennolla `sudoedit /etc/hosts`
(kuva4)

Lopuksi hain sekä localhost nimellä, että danieltars.com nimellä. Kummallakin tavalla sain auki halutun sivun. "Sinä" -sana muutti sen takia muotoa, koska index.html tiedostossa ei ole minkäänlaista dokumentin siällön määrittävää dokumenttityyppiä. 


### b) Julkinen nimi. Laita julkiselle palvelimellesi julkinen domain-nimi. Käytä oikeaa nimeä (joko vuokrattua tai ilmaispalvelusta). Tee Apachelle Name Based Virtual Host tälle nimelle. Kokeile eri laitteelta (esim. kännykältä), että nimi oikeasti toimii.

*Vuokrasin namecheapista xyz-loppuisen domainin*
![kuva](https://user-images.githubusercontent.com/77921212/134465546-c5e388dc-57b5-473a-a3a1-47956ad09ed7.png).
*Tämän jälkeen tein "Add a domain kohdasta" -kohdasta uuden domainin digital oceanin sivulla. Nimeksi annoin vuokratun domainin nimen, eli danieltarsalainen.xyz* 
![kuva](https://user-images.githubusercontent.com/77921212/134468600-83188c40-f137-4cb4-964c-f2931dd0205a.png)
*Tämän jälkeen menin tarkastelemaan digital oceanin domain-näkymää, joka näytti seuraavanalaiselta.*
![kuva](https://user-images.githubusercontent.com/77921212/134468854-760d43eb-d827-4471-acc7-0d21314d017a.png)
*Sitten noudatin domain -sivulla näkyviä ohjeita nimipalvelinten muuttamiseen.*
*https://www.digitalocean.com/community/tutorials/how-to-point-to-digitalocean-nameservers-from-common-domain-registrars -ohjeessa neuvottiin vaihtamaan digital oceanin nameservers kohta seuraavanlaiseksi*
![kuva](https://user-images.githubusercontent.com/77921212/134466271-eb778e0f-da39-4ad3-ab0d-d4b251e52d37.png)
*Muutosten tultua voimaan tuli seuraavanlainen viesti.*
![kuva](https://user-images.githubusercontent.com/77921212/134466373-4f7726da-0b9e-4a4e-8880-23418d31e0c9.png)
*Digital oceanin ohjesivulla tosin luki, että muutoksissa voi mennä vain 30 minuttia*

### c) Hello Flask! Tee Python Flask hei maailma kehitysympäristössä. Voit siis käyttää tuotantoon sopimatonta app.run(debug=True) ajoa.



### d) d) Tuotanto-Flask. Tee tuotantotyyppinen asennus Flaskista käyttäen Apachen WSGI-modulia. Kokeile, että pystyt muokkaamaan koodia ilman sudoa ja saat uuden version käyttöön käynnistämättä Apachea uudelleen. ('touch foo.wsgi')




