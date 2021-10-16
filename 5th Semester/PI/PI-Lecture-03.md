##### Prototip
Nije sustav koji radi

##### Inkrementalni razvoj
- Sustav se u djelovima isporučuje korisniku
- Početkom rada na cjelini, njezini zahtjevi se zamrzavaju
- Može proći kroz nekoliko iteracija

###### Prednosti
- Prioritizacija cijelina
- Fazna podjela funkcionalnosti
- Smanjuje rizik

##### Spiralni razvoj
Inkrementalni vodopadni razvoj
- SWOT - Strengths Weaknesses Opportunities Threats



...

##### Unificirani proces
###### Dimenzije
- Vertikalna
	- statika: opis procesa: aktivnosti, discipline, uloge, artefakti
- Horizontalna
	- dinamika: ciklusi, faze, iteracije i ključne točke

###### Faze
1. Početna faza (inception)
2. Faza razrade (elaboration)
3. Faza izgradnje (construction)
4. Faza prijenosa (transition)

###### Pregled procesa razvoja
- [[PI-Lecture-03#Faze]]
- [[Iteracije]]
- [[Ključne točke]]

###### Formalna struktura UP
![[Pasted image 20211014174232.png]]

###### Aktivnost zahtjeva
- engl. requirements workflow
- prije razvoja proizvoda, nužno je prikupiti sve potrebne informacije
- prikupljanjem funkcionalnih zahtjeva i ograničenjimadobiti što točnijusliku

###### Aktivnosti analize i oblikovanja
- engl. analysis and design workflow
- Cilj je izgradnja modela koji pomaže programerima precizirati i strukturirati funkcionalne zahtjeve zabilježene unutar modela obrasca uporabe
- Izgradnja modela oblikovanja  
	- sadrži detalje obrazaca uporabe koji se mogu oblikovati i implementirati
	- opisuje fizičke realizacije obrazaca uporabe
	- u početku se može napraviti samo osnovna skica oblikovanja bez puno detalja

###### Aktivnost implementacije  
- engl. implementation workflow
- Cilj aktivnosti implementacije usmjeren je na izgradnjumodela implementacije koji opisuje kako se elementimodela oblikovanja pakiraju u konkretne programske komponente  
	- npr. datoteke izvornog koda, biblioteke dinamičkih veza (DLL)

###### Aktivnost ispitivanja  
- engl. test workflow  
- Primarne aktivnosti ispitivanja usmjerene su naizgradnju ispitnog modela  
- Ispitni model sadrži ispitne slučajeve koji sečesto izvodeizravno iz obrazaca uporabe 
- Ispitivanje se provodi metodom crne kutijepomoćuizvornog teksta za obrasce uporabe
- Ispitivanje se mora provoditi tijekom cijelog projektana iterativan način

###### Modeliranje aktivnosti
![[Pasted image 20211014175220.png]]

###### Unificirani proces i obrasci uporabe  
- UP se zasniva se na obrascima uporabe (tj. predlošku scenarija)  
- Obrasci uporabe koriste se kroz svefaze, pokrećuaktivnosti i sinkroniziraju sadržaj različitihmodela

###### Obrasci uporabe - pokretačiiteracija  
- Obrasci uporabe pokreću brojne aktivnosti u životnomciklusu oblikovanja programske potpore

###### Najbolja praksa svojstvena UP-u  
1. Iterativan razvoj  
2. Upravljanje zahtjevima  
3. Uporaba komponentno zasnovane arhitekture  
4. Vizualno modeliranje (UML)  
5. Kontinuirana verifikacija kvalitete  
6. Upravljanje promjenama programske potpor

###### Sažetak značajki UP-a  
- UP posjeduje značajke iterativnog iinkrementalnogoblikovanja programske potpore  
- U središtuUP procesa su obrasci uporabe sustava kojisemantički povezuju sve aktivnosti  
- UP definira i međusobno povezuje faze i aktivnostiprocesa  
- Za opis pojedinih aktivnosti koriste seodgovarajući modeli  
- Modeli su dokumentirani jednim ili višedijagrama  
- Dijagrami su definirani normomUML  
- Arhitektura sustava sadrži skuppogleda u modele (tj. skup dijagrama)

##### Agilni razvoj
- Ubrzani, žustrirazvoj (engl. Agile development)  
- Grupa metoda za razvoj programske potpore kojima je zajednički iterativni razvoj uz male inkremente te koje podržavaju brzi odziv na korisničke zahtjeve  
- Ovaj model razvoja programske potpore koristi se za brzi razvoj manjih i srednjih projekata u stalnoj interakciji sklijentima putem stalnog predočavanja novih poboljšanja, uz relativno slabo dokumentiranje 
- Fokus je na talentu i vještini pojedinaca u projektnomtimu

###### Problemi modela procesa prog. inž.
- Većina procesnih modela ima puno administrativnog tereta  
	- velik naglasak izvan stvarnog programiranja  
- Tradicionalni procesni modeli su previšekruti  
	- ne funkcioniraju za nepotpune i nestabilnezahtjeve  
	- nisu prikladni kada su potrebne česteobjave i kratke razvojne  
iteracije  
- Kupci bi trebali aktivnije sudjelovati  
	- manji fokus na proces i većinaglasak na ljude

Načela agilnog razvoja  
- Zadovoljstvo kupaca kroz ranu i neprekidnu isporuku  
- Zahtjevi za promjenom dobrodošli, čak i u kasnim fazama  
- Često isporučivanje inačica
- Agilni procesi promoviraju održivirazvoj

 

##### Ekstremno programiranje
- engl. eXtreme Programming – XP
- Kontinuirano poboljšanje koda
- Sudjelovanje korisnika u razvojnom timu
- Programiranjuuparu(engl.pairwiseprogramming)
