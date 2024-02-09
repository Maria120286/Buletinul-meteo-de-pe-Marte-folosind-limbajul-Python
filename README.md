![image](https://github.com/Maria120286/Buletinul-meteo-de-pe-Marte-folosind-limbajul-Python/assets/157504181/1458af35-86f4-4dca-abea-7803c05e2775)
Introducere
Marte este a patra planetă de la Soare în Sistemul nostru Solar. Este o planetă stâncoasă care este similară în multe privințe cu Pământul, dar este mult mai rece și mai uscată. Culoarea roșie a suprafeței marțiene se datorează oxidului de fier (ruginii) de pe suprafață. Marte are două mici luni, Phobos și Deimos, despre care se crede că sunt asteroizi capturați.

Atmosfera planetei Marte este foarte rarefiată și este compusă în mare parte din dioxid de carbon. Există de asemenea o cantitate mică de azot și argon în atmosferă. Apa există pe Marte, dar este în mare parte sub formă de gheață și există foarte puțină apă lichidă pe suprafață.

În ultimii ani a existat un interes crescut pentru Marte, deoarece este considerată una dintre cele mai probabile locuri din Sistemul Solar în care să se găsească dovezi de viață trecută sau prezentă. NASA și alte agenții spațiale au trimis mai multe nave spațiale pe Marte pentru a studia planeta și a căuta semne de viață. În plus, există proiecte fezabile de a trimite oameni pe Marte în viitor.
Vremea pe Marte
Vremea de pe Marte este destul de diferită de vremea de pe Pământ. Marte este mai departe de Soare decât Pământul, deci este mult mai rece. Temperatura medie pe Marte este de aproximativ -80°F (-62°C). Cu toate acestea, temperatura poate varia foarte mult în funcție de locul în care vă aflați pe planetă și de momentul zilei.

Atmosfera planetei Marte este de asemenea mult mai subțire decât atmosfera Pământului, ceea ce înseamnă că nu există multă vreme așa cum o cunoaștem pe Pământ. Nu există nori, iar în aer este foarte puțin vapor de apă, astfel că nu există ploaie.

Există însă vânturi pe Marte care pot atinge viteze de până la 100km/oră. Aceste vânturi pot crea furtuni de praf care pot acoperi întreaga planetă și dura luni de zile. Există și furtuni mai mici numite “dust devils”, care sunt cauzate de încălzirea suprafeței de către Soare. Acestea sunt similare tornadelor de pe Pământ, dar sunt compuse din praf și nisip în loc de aer.
https://youtu.be/JKBk_Kfucs4

În ansamblu, vremea de pe Marte este foarte dură și ostilă vieții așa cum o cunoaștem. Cu toate acestea, oamenii de știință studiază în continuare planeta și caracteristicile sale meteo pentru a afla mai multe despre modul în care s-a schimbat de-a lungul timpului și pentru a vedea dacă este posibil să existe viață pe planetă ori cât de ușor ar putea-o susține.

Date meteorologice reale pe Marte
Landerul InSight al NASA efectuează măsurători continue ale vremii (temperatură, vânt, presiune) la suprafața planetei Marte în regiunea Elysium Planitia, o câmpie plată și netedă aproape de ecuator:
![image](https://github.com/Maria120286/Buletinul-meteo-de-pe-Marte-folosind-limbajul-Python/assets/157504181/60a3caa3-2a6f-4fa3-8ba0-b6e7b724f288)
API-ul oferit de NASA furnizează date sumare pentru fiecare sol disponibil din ultimele șapte soluri (zile marțiene). Pe măsură ce mai multe date de pe un anumit sol sunt descărcate de pe nava spațială (uneori cu câteva zile mai târziu), aceste valori sunt recalculate și, în consecință, se pot schimba pe măsură ce mai multe date sunt primite înapoi pe Pământ. În plus, trebuie remarcat faptul că datele privind vântul și alte date ale senzorului nu pot exista pentru anumite intervale de timp.

Datele oferite sunt furnizate sub formă de obiect în flux JSON. Să ne uităm puțin la codul Python de mai jos:

import json
import requests
url = "https://mars.nasa.gov/rss/api/?feed=weather&category=mars2020&feedtype=json"
data = requests.get(url).json()
print(data) #afisam datele brute
Important. Dacă nu ai instalate pachetele json și requests, vei obține sigur erori. Citește mai multe detalii [despre PIP].

Este o adevărată magie! Folosim doar 4 linii de cod și obținem date reale de pe Marte prin intermediul NASA:
![image](https://github.com/Maria120286/Buletinul-meteo-de-pe-Marte-folosind-limbajul-Python/assets/157504181/a369e753-c1b2-4ea4-a035-4698b48c03aa)
După cum puteți observa, variabila "data" reține un dicționar Python (clasa dict) cu toate datele primite de la API-ul NASA folosind o cerere JSON. Folosind cheia "sols", putem accesa fiecare zi din lista inclusă astfel:

print(data['sols'][0]) #ziua 1 din setul de date
print(data['sols'][1]) #ziua 2 din setul de date
...
print(data['sols'][6]) #ziua 7 din setul de date

Vom obține datele corespunzătoare pentru orice zi dorim din intervalul de timp disponibil direct de pe planeta Marte:
![image](https://github.com/Maria120286/Buletinul-meteo-de-pe-Marte-folosind-limbajul-Python/assets/157504181/29635544-3c86-42aa-bbdd-f9d62d64bdc7)
Rețineți că data[‘sols’][6] conține un dicționar la care se poate accesa ușor astfel:
![image](https://github.com/Maria120286/Buletinul-meteo-de-pe-Marte-folosind-limbajul-Python/assets/157504181/4a8ccecd-17f2-4903-95c3-54dadb86318c)
Gata! Puteți importa date reale de pe Marte în proiectele dvs. Python!

De asemenea, modulele numpy și matplotlib oferă opțiuni suplimentare pentru vizualizări interactive de date în Python și multe altele! Sunt toate gratuite și foarte interesante pentru orice persoană care învață limbajul de programare Python!

Ce observăm? Păi simplitatea lucrului în Python! Am importat rapid două module pentru a putea efectua cereri prin intermediul JSON. Am impus linkul spre API și am preluat apoi rezultatele ușor și rapid!





