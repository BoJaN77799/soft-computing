## Detekcija, lokalizacija i klasifikacija glumaca na isečcima iz filmova

## Tim:

- Marko Bjelica (sw-4/2018)
- Bojan Baškalo (sw-49/2018)
- Veljko Tošić (sw-55/2018)


## Asistent:

- Dragan Vidaković


## Definicija problema:
<p align="justify">
Detekcija, lokalizacija i prepoznavanje glumaca na video isečcima u realnom vremenu i prikazivanje nekih njihovih osobina kao što su starost, pol i rasa.
</p>

## Skup podataka:

<p align="justify">
Za treniranje SVM višeklasnog klasifikatora, korišćen je ručno kreiran skup podataka, koji se sastoji od 924 slike. Taj skup čini 9 glumaca (Angelina Jolie, Benedict Cumberbatch, Brad Pitt, Chadwick Boseman, Emma Watson, Keanu Reeves, Robert Downey-Junior, Scarlett Johansson i Tom Holland), uslikanih pod različitim uglovima i situacijama.
Klasifikatori starosti i pola su pretrenirani modeli dubokih neuronskih mreža trenirani od strane <a href="https://talhassner.github.io/home/projects/Adience/Adience-data.html">Tal Hassner i Gil Levi</a>.
Klasifikator za rasu je pretrenirana neuronska mreža koja se nalazi u DeepFace pajton radnom okviru.
</p>

## Metodologija:
<p align="justify">
Prepoznavanje jeste proces sastavljen od više koraka, počevši od detekcije face. Za detekciju face na slici korišćen je pretrenirani <a href="https://towardsdatascience.com/hog-histogram-of-oriented-gradients-67ecd887675f">Haar Cascade Classifier</a>, jer je pogodan za detektciju u realnom vremenu zbog brzine. Zarad boljeg treniranja vrši se centralizacija detektovane face na osnovu pretreniranog modela koji detektuje 68 specifičnih tačaka na licu. Centralizovana lica ekstraktuje 
 <a href="https://towardsdatascience.com/hog-histogram-of-oriented-gradients-67ecd887675f">HOG</a> (Histogram of Oriented Gradients) ekstraktor obeležja, koji redukuje nepotrebne piksele i čuva informacije bitne SVM klasifikatoru koji vrši prepoznavanje. 
Klasifikatori za prepoznavanje pola, starosti i rase ne koristi ekstraktovana lica, nego direktno isečena sa slike.
Za prepoznavanje pola i godina korišćeni su pretrenirani modeli duboke neuronske mreže koji su istrenirani od strane <a href="https://talhassner.github.io/home/projects/Adience/Adience-data.html">Tal Hassner i Gil Levi</a>. 
Za prepoznavanje rase korišćen je DeepFace pajton radni okvir koji u sebi sadrži pretreniranu neuronsku mrežu.
</p>

## Evaluacija:
<p align="justify">
Za klasifikaciju korišćene su mere performanse kao što su preciznost, tačnost, odziv i F mera, a za lokalizaciju mAP (mean Average Precision). Mereni su odnosi tih vrednosti kroz broj frejmova po sekundi koje model može da obradi.
</p>

## Poster
![poster](https://user-images.githubusercontent.com/59332786/150903764-fce53217-b197-498d-a5c7-8f4187e76b6d.jpg)
<p align="right">
 Klikom na <a href="https://github.com/BoJaN77799/soft-computing/files/7930321/poster.pdf">link</a> možete preuzeti poster ovog projekta.
</p>

## Demo:
![Scarlett_Downey_video2_demo_1](https://user-images.githubusercontent.com/58345648/150875341-4c40b093-dec0-4325-ac4e-22a2728d253d.gif)

## Potrebne biblioteke:
Projekat pokretan sa [Python 3.6].
Potrebne biblioteke:
 - [numpy] - [1.19.5+]
 - [opencv] - [4.3.0+]
 - [matplotlib] - [3.2.2+]
 - [dlib] - [19.22.0]
 - [scikit-learn] - [0.22.1]
 - [deepface] - [0.0.72]

Za implementaiju korišćeno [Jupyter] okrženje verzije 1.0.0.

## Proces pokretanja u Anaconda3 virtuelnom okruženju:

1. Potrebno je da preuzmete projekat sa github repozitorijuma.
2. Nakon što ste instalirali [Anaconda3] virtuelno okruženje, potrebno je da kreirate sopstveno virtuelno orkuženje tako što se pozicionirate na putanju projekta "soft-computing" u (base) conda prompt-u i pokrenete komande:
    ```sh
    - conda create --name soft
    - conda activate soft
    ```
3. Potom je potrebno da pokrenete sledece komande (Srećno :) 
    ```sh
    - conda install ipykernel
    - conda install python=3.6
    - conda install -c conda-forge opencv=4.3.0
    - conda install -c conda-forge dlib
    - conda install -c anaconda numpy
    - conda install -c conda-forge scikit-learn
    - python -m ipykernel install --user --name soft --display-name “Soft”
    - conda install jupyter
    - pip install deepface
    - conda install -c conda-forge matplotlib
    - jupyter notebook
    ```
[Jupyter]: https://jupyter.org/install
[Python 3.6]: https://www.python.org/downloads/release/python-360/
[numpy]: https://pypi.org/project/numpy/
[opencv]: https://pypi.org/project/opencv-python/
[matplotlib]: https://pypi.org/project/matplotlib/
[dlib]: https://pypi.org/project/dlib/
[scikit-learn]: https://pypi.org/project/scikit-learn/
[deepface]: https://pypi.org/project/deepface/
[Anaconda3]: https://www.anaconda.com/products/individual
