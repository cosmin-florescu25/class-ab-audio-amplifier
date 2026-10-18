# Amplificator Audio Clasa AB (4 Etaje)

Un proiect complet de amplificator audio de putere in clasa AB: de la schema si simulare in LTspice, pana la montajul fizic testat pe breadboard si conectat la laptop.

---

## Despre proiect

Am vrut sa construiesc un amplificator audio functional folosind tranzistoare discrete si componente usor de gasit. Tot circuitul este gandit sa mearga pe o alimentare simpla de 5V (plus baterii pentru etajul de intrare) si sa duca un difuzor obisnuit de 8 ohmi.

Semnalul vine direct din mufa jack a laptopului. Pentru ca semnalul nativ e stereo, am combinat canalele stanga/dreapta cu rezistente de 1k pentru a scoate un semnal mono curat inainte de amplificare.

---

## Cum functioneaza (cele 4 etaje)

1. **Buffer / Repetor cu Amplificator Operational (LM358):**  
   Are impedanta mare la intrare, deci protejeaza placa de sunet sau iesirea laptopului si preia semnalul fara sa-l incarce.
2. **Preamplificator in Emitor Comun (2N2222):**  
   Tranzistorul Q1 mareste amplitudinea semnalului (gain in tensiune in jur de -9) si il inverseaza. Condensatoarele de cuplaj blocheaza componenta continua ca sa treaca doar sunetul.
3. **Driver si Polarizare / Bias:**  
   Tranzistorul Q2 actioneaza ca sursa de curent, iar cele doua diode inseriate asigura o cadere de tensiune de aproximativ 1.2V - 1.35V. Asta tine tranzistoarele finale usor deschise si scapa complet de distorsiunile de cross-over.
4. **Etajul final Push-Pull (2N2222 + 2N2907):**  
   Lucrul pe rand: NPN-ul se ocupa de alternanta pozitiva a semnalului, iar PNP-ul de alternanta negativa. Ambele sunt in colector comun pentru a da curentul necesar difuzorului de 8 ohmi prin condensatorul de iesire de 220uF.

---

## Ce am invatat / Probleme practice rezolvate

- **Firele de la casti:** Dupa ce am taiat cablul jack, nu aveam deloc semnal pentru ca firele aveau un strat protector de smalt; a trebuit sa le ard smaltul cu bricheta/cositor ca sa faca contact.
- **Brum si zgomot de fundal:** Am redus bazaitul parazit adaugand condensatoare suplimentare de filtrare/decuplare (2x 104nF in paralel) direct spre masa.
- **Punct static echilibrat:** In simularea DC (.op), tensiunea dintre emitoarele etajului final a iesit la ~2.34V, aproape de jumatatea alimentarii (Vcc/2), ceea ce permite semnalului sa oscileze simetric.

---

## Fisiere in repo

- `AmplificatorAudio.asc` – Schema completa pentru rulat direct in LTspice.
- `Proiect.pdf` – Raportul original cu calcule, liste de preturi si grafice.
- `assets/` – Poze cu montajul pe breadboard si capturi dupa osciloscop/simulari.
