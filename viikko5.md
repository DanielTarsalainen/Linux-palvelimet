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

### c) Hello Flask! Tee Python Flask hei maailma kehitysympäristössä. Voit siis käyttää tuotantoon sopimatonta app.run(debug=True) ajoa.

### d) d) Tuotanto-Flask. Tee tuotantotyyppinen asennus Flaskista käyttäen Apachen WSGI-modulia. Kokeile, että pystyt muokkaamaan koodia ilman sudoa ja saat uuden version käyttöön käynnistämättä Apachea uudelleen. ('touch foo.wsgi')




