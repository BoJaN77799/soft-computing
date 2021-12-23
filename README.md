## Detekcija, lokalizacija i klasifikacija glumaca na isečcima iz filmova

## Tim:

- Marko Bjelica (sw-4/2018)
- Bojan Baškalo (sw-49/2018)
- Veljko Tošić (sw-55/2018)


## Asistent:

- Dragan Vidaković


## Definicija problema:

Detekcija, lokalizacija i prepoznavanje glumaca kao i njihovih osobina (starost, pol i rasa) na isečcima iz filmova, s tim da će se detekcija, lokalizacija i prepoznavanje glumca vršiti u realnom vremenu.


## Skup podataka:

Slike glumaca ćemo prikupiti ručno, odnosno prikupićemo dovoljnu količinu raznovrsnih slika (drugačiji ugao fotografisanja, različita životna dob, osvetljenje,...).

## Metodologija:

Za detekciju i lokalizaciju koristićemo pretrenirani HAAR klasifikator. Zatim će detektovana lica biti procesirana (centralizacija i poravnavanje ključnih tačaka lica) i prosleđena odgovarajućem ekstraktoru obeležja kao što je HOG, te će potom biti klasifikovana korišćenjem SVM-a i/ili neuronskih mreža.

## Evaluacija:

Za klasifikaciju koristićemo mere performanse kao što su preciznost, tačnost, odziv i F mera, dok ćemo za lokalizaciju koristiti mAP (mean average precision). Kao mera performanse za rad u realnom vremenu koristićemo odnos broja frejmova po sekundi koje model može da obradi, mAP-a i F mere.
