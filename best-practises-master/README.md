# Best Practises
<details>
 <summary> Označavanje Trello kartica </summary> 
  </br>
  
Važno je da sve Trello kartice/korisničke priče budu jedinstveno označene. Identifikatori kartica će biti u formatu <b>TIMX.Y</b>, gdje će TIM biti oznaka tima, X oznaka sprinta, a Y oznaka funkcionalnosti. <br> 
Oznake timova na koje smo se odlučili biće sledeće:
* WEB - Tim za Web aplikaciju
* IA - Tim za integracione adaptere
* GR - Tim za grafički editor
* DEV - DevOps tim
<br>
Dodatno, u oznaku ulaziće brojevi sprinta i funkcionalnosti, pa prema tome npr. <br> 
  - 5. funkcionalnost na kojoj web tim radi u okviru 2. sprinta imala bi oznaku <b>WEB2.5</b>. <br> 
  - 4. funkcionalnost na kojoj tim za integracione adaptere radi u okviru 3. sprinta imala bi oznaku <b>IA3.4</b> itd.<br>
<br>Nakon toga slijedi naziv funkcionalnost koji će timovi sami odrediti.
</details>

<details>
 <summary> Imenovanje grana </summary> <br>
  
Grane imenovati u formatu <b>Tim_TipPromjene/Opis</b>, gdje je:
</br>
* **Tim** je oznaka tima iz sekcije za Trello kartice
* **TipPromjene** je neka od mogućih riječi:
<br> - *feature* za rad na funkcionalnosti
<br> - *bugfix* za ispravku bagova
<br> - *hotfix* za jako hitne ispravke
<br> - *refactor* za refaktorisanje
<br> - *docs* za dodavanje dokumentacije
<br> Po potrebi možemo dodati još prefiksa (npr. za dodavanje testova ili tako nešto).
* **Opis** je minimalan opis funkcionalnosti na kojoj će se raditi. Opis ima maksimalno par riječi, obavezno na engleskom.

Pisati čitavo ime grane malim slovima, i kao separator riječi u opisu koristiti **-**. 
<br>Primjer: **ia_feature/isa-integration**
</details>

<details>
 <summary> Pisanje commit poruke </summary> <br>
  
Commit message pisati u formatu **[Oznaka] TipPromjene:Opis**, gdje je:
</br>
* **Oznaka** je oznaka kartice iz sekcije za Trello kartice
* **TipPromjene** nešto od:
 <br> - *feature* - izmjena ili dodavanje koda koji direktno doprinosi nekoj funkcionalnosti
 <br> - *bugfix* - rad na ispravci bagova
 <br> - *hotfix* - brze i sitne ispravke, do 5 linija koda
 <br> - *refactor* - refaktorisanje koda
 <br> - *style* - stilske ispravke, formatiranje koda i slično
 <br> - *test* - izmjena ili dodavanje testova
 <br> - *chore* - izmjena pomoćnih fajlova, kao što je gitignore i slične stvari
 <br> - *docs* za dodavanje dokumentacije
* **Opis** je kratak opis napravljenih izmjena, obavezno na engleskom

Primjer: **[IA1.4] feature: Added code for integrating with ISA projects**
</details>

<details>
	<summary> Kreiranje Pull Request-a </summary> <br>

Kada otvarate Pull Request, važno je dati dobar opis šta je njegov cilj, kako bi bilo ko od članova tima koji treba da koristi ili pregleda taj kod imao što manje problema da shvati šta se tu zapravo dešava. Šablon nećemo imati, ali ispod navodimo primjer dobrog i lošeg PR-a.  

<br>Primjer lošeg PR-a:
![image](https://miro.medium.com/max/3160/1*K_0EmQc6rz3Hdo1ZTRJc0g.png)
<br>Primjer dobrog PR-a:
![image](https://blog.axosoft.com/wp-content/uploads/2019/05/Open-Pull-Request-URL.png)

</details>





## Git instrukcije

U instrukcijama je kod naredbi koje treba da se izvrše na tačno određenoj grani napisano ime grane u zagradi ispred naredbe (onako kako Git Bash označava na kojoj grani se nalazite). Na primjer, ako je napisano <code> (develop) git pull </code> to znači da treba da se izvrši naredba git pull na develop grani.

<details>
 <summary> Kloniranje repozitorijuma
 </summary> 

<br>

1. Klonirati repozitorijum: 

	```sh 
	git clone https://github.com/PSW-2020-ORG5/HealthCare-Clinic.git
	```

2. Prebaciti se u folder u kom se nalazi repozitorijum </br>
3. Prebaciti develop granu:

	* Ako ne postoji <br>	```sh
  	git checkout -b develop
  	```
  
 	ili
  
	* Ako postoji <br>```sh
  	git checkout develop
  	```
 
</details>

<details>
 <summary> Pravljenje nove grane
 </summary> 
  
  </br>
  
1. Pozicionirati se na develop:
	<br>
	
	```sh
	git checkout develop
	```
2. Napraviti novu granu:
	<br>
	
	```sh
	(develop) git checkout -b nova-grana
	```
3. Poslati novu granu na repozitorijum na GitHubu:
	<br>
	
	```sh
	(nova-grana) git push -u origin nova-grana
	```
<br>Nije moguće otvoriti pull request čim se napravi grana jer neće još imati razlika u odnosu na develop, ali treba otvoriti pull request što je ranije moguće. Dobar trenutak za to je posle završetka prve veće cjeline date funkcionalnosti.

 
</details>

<details>
 <summary> Pravljenje commitova
 </summary> 
  
1. Provjeriti da li ste na tačnoj grani, i ako niste prebaciti se na nju:

	```sh
	git checkout neka-grana
	```
	
2. Napraviti izmjene u kodu

3. Dodati fajlove u staging zonu. Ako se dodaju svi fajlovi, koristiti

	```sh
	(neka-grana) git add . 
	```
	
	Može se koristiti i <code>git add putanja_do_fajla</code>, ali preporučuje se prvi način.

4. Napraviti commit, pri čemu commit message treba da bude u skladu sa konvencijom:

	```sh
	(neka-grana) git commit -m "commit message"
	```
	
5. Poslati izmjene na remote repozitorijum na GitHubu:
	
	```sh
	(neka-grana) git push origin neka-grana
	```

Ukoliko to nije ranije urađeno, ovo je dobar trenutak za otvaranje pull requesta za granu. Ako je već napravljen pull request, na njemu će se moći vidjeti i novi commit (i ako je ranije već odrađen review pull requesta i dat approval, poništiće se approval i svakako ponovo raditi review).

 
</details>

<details>
 <summary> Otvaranje pull requesta </summary> 
  </br>
  
Jedan mogući način za otvaranje pull requesta je:

1. Ući u repozitorijum na GitHubu 
2. Izabrati karticu Pull requests
3. Ići na New pull request
4. Postaviti tako da je base develop, a compare grana koja treba da se spoji u develop 
5. Ići na Create pull request
6. Napisati dobar description, dodati review-era i sve ostalo što ide uz pravljenje PR-a
7. Kliknuti na Create pull request dugme
8. Kreirani pull request povezati sa karticom na Trello boardu preko GitHub powerupa

 
</details>

<details>
 <summary> Spajanje grane / zatvaranje pull requesta </summary> 
  
  </br>
  
Kada završite izmjene na grani, ona se spaja u develop opcijom Merge pull request na njenom pull requestu na GitHubu. To je moguće uraditi pod sledećim uslovima:

1. Grana je up to date sa developom
2. Prolaze sve provjere na Azure
3. Ima minimalno dva odobravajuća reviewa od DevOps tima
4. Niko nije tražio izmjene na pull requestu (opcija Request changes pri pravljenju reviewa) - ukoliko je neko tražio izmjene, neće se moći spojiti pull request dok ta osoba ne stavi approval, ili neko iz DevOps tima odbaci zahtjev za izmjenama

Kada je zatvoren pull request, grana na repozitorijum na GitHubu će se automatski obrisati. Granu na lokalnom repozitorijumu možete obrisati sa:

	git branch -d ime-grane
	
</details>


<details>
 <summary> Povlačenje izmjena sa developa na drugu granu
 </summary> 
  
Kako bi se mogao zatvoriti pull request potrebno je da grana bude up to date sa developom, odnosno da sve izmjene sa developa budu već intergrisane u granu na kojoj se radi. 
Prvo je potrebno povući izmjene sa develop na GitHubu na develop granu u lokalnom repozitorijumu:

1. Prebaciti se na develop

	```sh
	git checkout develop
	```
	
2. Povući izmjene
	```sh
	(develop) git pull origin develop
	```
 
	Zatim je potrebno spojiti lokalnu develop granu u granu na kojoj radite:

1. Prebaciti se na granu na kojoj se trenutno radi:

	```sh
	git checkout neka-grana
	```

2. Spojiti develop:

	```sh
	(neka-grana) git pull origin develop
	```

	<br>Ovo je jedini korak u workflow-u u kom može doći do konflikta. Ukoliko se desi konflikt, može se vidjeti u kojim je fajlovima pomoću naredbe <code> git status </code> ili kada se otvori Visual Studio. Potrebno je riješiti konflikt, a zatim commitovati napravljene izmjene na uobičajeni način (za TIpPromjene u commit message-u pri rješavanju konflikta staviti merge).

</details>

<details>
 <summary> 
 Generalno korisne naredbe </summary> 
  
* <code>git log</code>
	<br>Prikazuje Git istoriju prethodnih commit-ova, gdje možete provjeriti da li je vaša grana up-to-date sa remote granom.
* <code>git status</code>
	<br>Prikazuje trenutno stanje grane na kojoj se izvrši, npr. koji su fajlovi izmjenjeni, da li su dodati u staging area, koji su fajlovi u konfliktu ako se radi spajanje, i slično.
* <code>git branch</code>
	<br>Za prikazivanje i rad sa granama, neki od korisnih dodatnih argumenata za prikazivanje grana su:
	<br><code>-a</code>  - prikazuje i remote grane, po defaultu će prikazati samo lokalne
	<br><code>-vv</code> - prikazuje više detalja o granama, npr. koju granu sa GitHuba prate, na kom su commitu, i slično

 
</details>



## Pravila u radu
Poučeni iskustvom sa prvog sprinta, odlučili smo da se vodimo sledećim pravilima:
* Sve što se uradilo na funkcionalnostima i u okviru Pull Request-a do **petka posljednje nedelje** sprinta, uradilo se.
<br>   - Ovim postižemo to da imamo vikend samo za brze promjene koje će review-eri iz DevOps ili vašeg tima predložiti
<br>   - Izbjegavamo situaciju merge conflict-a nedeljom u 23:50
* **Pull Request ne smije imati više od 1000 izmjenjenih linija koda**.
<br>   - Ovim postižemo to da će review-ovanje ići brže i biti kvalitetnije
<br>   - Smanjujemo šansu za merge conflict, jer je manji broj izmjena nad zajedničkim kodom
<br>   - Lakše nalazimo bagove iz prethodnih komitova
* **Svaka grana je vezana za jedan feature** i jednu karticu na Trello-u, pa tako i za jedan PR
