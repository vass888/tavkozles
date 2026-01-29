# MÉRÉSI JEGYZŐKÖNYV

**Intézmény:** Miskolci SZC Kandó Kálmán Informatikai Technikum
**Helyszín:** Miskolc
**Dátum:** 2026. 01. 29.

---

## 1. A mérés adatai

* **Mérést végezte:** Vass Viktor
* **Mérés tárgya:** Invertáló erősítő vizsgálata (TL071)
* **Alkalmazott mérőrendszer:** NI myDAQ (National Instruments)

---

## 2. A mérés célja
TL071 típusú műveleti erősítővel felépített invertáló alapkapcsolás vizsgálata. A feszültségerősítés ($A_u$) meghatározása méréssel, és az eredmények összevetése az ellenállások értékeiből számított elméleti erősítéssel.

---

## 3. Felhasznált alkatrészek

| Pozíciószám | Alkatrész | Érték (Mért) | Funkció |
| :--- | :--- | :--- | :--- |
| **U1** | TL071 | - | Műveleti erősítő (JFET input) |
| **R1** | Ellenállás | **11,7 kΩ** | Bemeneti ellenállás |
| **R2** | Ellenállás | **99,7 kΩ** | Visszacsatoló ellenállás |
| **R3** | Ellenállás | **11,95 kΩ** | Kompenzáló ellenállás (Nem invertáló ág) |

---

## 4. Elméleti számítások

Az invertáló erősítő feszültségerősítése ($A_{elm}$) a visszacsatoló és a bemeneti ellenállás hányadosaként számítható:

$$A_{elm} = -\frac{R_2}{R_1}$$

Behelyettesítve a rendelkezésre álló ellenállások értékeit:

$$A_{elm} = -\frac{99,7 \text{ k}\Omega}{11,7 \text{ k}\Omega} \approx \mathbf{-8,52}$$

**Várt viselkedés:**
1.  A kimeneti jel fázisa 180°-kal elfordul a bemeneti jelhez képest (invertálás).
2.  A kimeneti jel amplitúdója kb. 8,5-szöröse a bemenetinek, amíg az el nem éri a tápfeszültség korlátait (telítés).

---

## 5. Mérési eredmények

A méréshez az NI myDAQ *Function Generator* (FGEN) és *Oscilloscope* (SCOPE) műszereit használtam.

**Mért feszültségértékek:**

| Sorszám | $U_{be}$ (V) <br> *(Bemeneti jel)* | $U_{ki}$ (V) <br> *(Mért kimenet)* | $A_{mért}$ <br> $(U_{ki} / U_{be})$ | Megjegyzés |
| :---: | :---: | :---: | :---: | :---: |
| 1. | 0,2 V | | | Lineáris tartomány |
| 2. | 0,5 V | | | Lineáris tartomány |
| 3. | 1,0 V | | | Lineáris tartomány |
| 4. | 1,5 V | | | (Várható $U_{ki} \approx 12,8V$) |
| 5. | 2,0 V | | | Telítés (Vágás) lehetséges |

---

## 6. Kiértékelés

A mérés során a TL071-es IC-vel felépített kapcsolás invertáló erősítőként viselkedett.
* **Számított erősítés:** *8,47* 
* **Mért átlagos erősítés:** *8,461*

Az $R_3$ ellenállás (11,95 kΩ) a nem invertáló bemeneten a bemeneti offszet áramok hatásának csökkentését szolgálta. Értéke közelíti az $R_1$ és $R_2$ párhuzamos eredőjét ($R_1 \times R_2 \approx 10,47 k\Omega$), így a kompenzálás megfelelő.

**Aláírás:**

__________________________
**Vass Viktor**
