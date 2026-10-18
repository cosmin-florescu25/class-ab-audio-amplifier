# Amplificator Audio Clasa AB (4 Etaje)

Un proiect complet de amplificator audio de putere in clasa AB: de la schema si simulare in LTspice, pana la montajul fizic testat pe breadboard si conectat la laptop[cite: 1, 2, 5].

---

## Despre proiect

Am vrut sa construiesc un amplificator audio functional folosind tranzistoare discrete si componente usor de gasit[cite: 1, 4, 5]. Tot circuitul este gandit sa mearga pe o alimentare simpla de 5V (plus baterii pentru etajul de intrare) si sa duca un difuzor obisnuit de 8 ohmi[cite: 1, 2, 4, 5].

Semnalul vine direct din mufa jack a laptopului[cite: 2]. Pentru ca semnalul nativ e stereo, am combinat canalele stanga/dreapta cu rezistente de 1k pentru a scoate un semnal mono curat inainte de amplificare[cite: 2].

---

## Cum functioneaza (cele 4 etaje)

1. **Buffer / Repetor cu Amplificator Operational (LM358):**  
   Are impedanta mare la intrare, deci protejeaza placa de sunet sau iesirea laptopului si preia semnalul fara sa-l incarce[cite: 2].
2. **Preamplificator in Emitor Comun (2N2222):**  
   Tranzistorul Q1 mareste amplitudinea semnalului (gain in tensiune in jur de -9) si il inverseaza[cite: 3]. Condensatoarele de cuplaj blocheaza componenta continua ca sa treaca doar sunetul[cite: 3].
3. **Driver si Polarizare / Bias:**  
   Tranzistorul Q2 actioneaza ca sursa de curent, iar cele doua diode inseriate asigura o cadere de tensiune de aproximativ 1.2V - 1.35V[cite: 4, 7]. Asta tine tranzistoarele finale usor deschise si scapa complet de distorsiunile de cross-over[cite: 2, 4, 7].
4. **Etajul final Push-Pull (2N2222 + 2N2907):**  
   Lucrul pe rand: NPN-ul se ocupa de alternanta pozitiva a semnalului, iar PNP-ul de alternanta negativa[cite: 4, 5]. Ambele sunt in colector comun pentru a da curentul necesar difuzorului de 8 ohmi prin condensatorul de iesire de 220uF[cite: 4, 5].

---

## Ce am invatat / Probleme practice rezolvate

- **Firele de la casti:** Dupa ce am taiat cablul jack, nu aveam deloc semnal pentru ca firele aveau un strat protector de smalt; a trebuit sa le ard smaltul cu bricheta/cositor ca sa faca contact[cite: 6].
- **Brum si zgomot de fundal:** Am redus bazaitul parazit adaugand condensatoare suplimentare de filtrare/decuplare (2x 104nF in paralel) direct spre masa[cite: 6].
- **Punct static echilibrat:** In simularea DC (.op), tensiunea dintre emitoarele etajului final a iesit la ~2.34V, aproape de jumatatea alimentarii (Vcc/2), ceea ce permite semnalului sa oscileze simetric[cite: 6].

---

## Fisiere in repo

- `AmplificatorAudio.asc` – Schema completa pentru rulat direct in LTspice[cite: 1].
- `Proiect.pdf` – Raportul original cu calcule, liste de preturi si grafice[cite: 2, 5, 7].
- `assets/` – Poze cu montajul pe breadboard si capturi dupa osciloscop/simulari[cite: 5, 6, 7].
