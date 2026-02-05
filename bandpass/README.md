# MÉRÉSI JEGYZŐKÖNYV

**Intézmény:** Miskolci SZC Kandó Kálmán Informatikai Technikum  
**Helyszín:** Miskolc, V3 Labor  
**Dátum:** 2026. 02. 02.

---

## 1. A mérés adatai

* **Mérést végezte:** Vass Viktor
* **Mérés tárgya:** Aktív sávszűrő vizsgálata (LM324)
* **Alkalmazott mérőrendszer:** NI myDAQ (National Instruments) – Bode Analyzer

---

## 2. A mérés célja
LM324 típusú műveleti erősítővel felépített aktív sávszűrő (Bandpass Filter) áramkör vizsgálata. A szűrő rezonanciafrekvenciájának ($f_0$) és az ott mérhető feszültségerősítésnek ($A_0$) meghatározása, valamint az átviteli karakterisztika (Bode-diagram) felvétele.

---

## 3. Felhasznált alkatrészek

A kapcsolás egy műveleti erősítős, többszörös visszacsatolású (vagy ahhoz hasonló topológiájú) sávszűrő.

| Pozíciószám | Alkatrész | Érték (Kapcsolási rajz) | Funkció |
| :--- | :--- | :--- | :--- |
| **IC1** | LM324 | - | Műveleti erősítő (Quad Op-Amp) |
| **R1** | Ellenállás | **220 Ω** | Bemeneti osztó / szűrő tag |
| **R2** | Ellenállás | **220 Ω** | Szűrő tag (Föld felé) |
| **R3** | Ellenállás | **11,91 kΩ** | Visszacsatoló ellenállás |
| **C1** | Kondenzátor | **470 nF** | Csatoló/Szűrő kapacitás |
| **C2** | Kondenzátor | **470 nF** | Csatoló/Szűrő kapacitás |

<img width="720" height="516" alt="image" src="https://github.com/user-attachments/assets/ec496cc4-c921-4841-9855-5d04b10f6f24" />   
A végleges kapcsolás az eredetitől eltérő, kisebb átalakítást kellett elvégezni 

---

## 4. Elméleti számítások

Az áramkör egy sávszűrő, amely egy adott frekvenciatartományt enged át, míg az alacsonyabb és magasabb frekvenciákat csillapítja.

A rezonanciafrekvencia ($f_0$) elméleti meghatározása az alkalmazott passzív alkatrészek ($R$, $C$) értékeitől függ. A kapcsolás topológiája alapján a középfrekvencia közelítőleg:

$$f_0 = \frac{1}{2\pi C} \sqrt{\frac{R_1 + R_2}{R_1 R_2 R_3}}$$

**Várt viselkedés:**
1. A kimeneti jel amplitúdója a rezonanciafrekvencián ($f_0$) éri el a maximumot.
2. A fázisgörbe a rezonanciafrekvenciánál jellemzően előjelet vált vagy 0°/180°-on halad át (az áramkör invertáló jellegétől függően).

---

## 5. Mérési eredmények

A méréshez az NI myDAQ *Bode Analyzer* műszerét használtam 10 Hz és 20 kHz közötti tartományban.

**Mért értékek a kurzor alapján:**
* **Rezonanciafrekvencia ($f_0$):** 309,68 Hz
* **Erősítés a csúcson ($Gain$):** 29,17 dB
* **Fázis ($Phase$):** 177,14° (Invertáló jellegre utal a rezonancia közelében)

<img width="924" height="740" alt="image" src="https://github.com/user-attachments/assets/a1582458-42de-4354-b486-a8ed26c3d856" />   

---

## 6. Kiértékelés

A mérés során az LM324-es IC-vel felépített kapcsolás sávszűrőként viselkedett. A Bode-diagramon jól látható a kiemelés a 300 Hz-es tartományban.

* A **29,17 dB-es erősítés** jelentős feszültségerősítést jelent a rezonanciafrekvencián ($A_u \approx 28,7$).
* A fázisgörbe menete igazolja a frekvenciafüggő fázistolást, amely a rezonancia környezetében éles változást mutat.
* Az áramkör szelektíven emeli ki a ~310 Hz körüli jeleket, míg a 10 Hz-es és 10 kHz-es tartományban a jelet jelentősen csillapítja (negatív dB értékek a grafikon szélein).

**Aláírás:**

__________________________
**Vass Viktor**
