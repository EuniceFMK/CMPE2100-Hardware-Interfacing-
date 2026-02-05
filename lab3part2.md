D’accord Ma Kida 🤍
On reprend **CALMEMENT**, **EN FRANÇAIS**, **STEP BY STEP**, **sans sauter d’étapes**, exactement comme tu l’écrirais à l’examen.
Je suis **strictement** l’énoncé et **le schéma que tu as envoyé**.
 
---
 
# 🟦 PARTIE A — FONCTION DE TRANSFERT (INA114)
 
## 🔹 Données imposées
 
* Entrée :
  $$
  V_{in} \in $$-0.5\ \text{V},\ 2.25\ \text{V}$$
  $$
 
* Sortie :
  $$
  V_{out} \in $$-5\ \text{V},\ 5\ \text{V}$$
  $$
 
On cherche une fonction **linéaire** :
$$
V_{out} = A \cdot V_{in} - V_{off}
$$
 
---
 
## ✅ Étape 1 — Calcul du gain (A)
 
Formule :
$$
A = \frac{\Delta V_{out}}{\Delta V_{in}}
$$
 
### Variation de sortie
 
$$
\Delta V_{out} = 5 - (-5) = 10\ \text{V}
$$
 
### Variation d’entrée
 
$$
\Delta V_{in} = 2.25 - (-0.5) = 2.75\ \text{V}
$$
 
### Gain
 
$$
A = \frac{10}{2.75} = 3.636
$$
 
✅ **Gain** :
$$
\boxed{A = 3.64}
$$
 
---
 
## ✅ Étape 2 — Calcul du décalage (V_{off})
 
On utilise **un point connu**, par exemple le minimum :
 
$$
V_{in} = -0.5\ \text{V} \quad \Rightarrow \quad V_{out} = -5\ \text{V}
$$
 
On remplace dans :
$$
V_{out} = A V_{in} - V_{off}
$$
 
$$
-5 = (3.636)(-0.5) - V_{off}
$$
 
$$
-5 = -1.818 - V_{off}
$$
 
$$
V_{off} = 3.182\ \text{V}
$$
 
✅ **Offset requis** :
$$
\boxed{V_{off} = 3.18\ \text{V}}
$$
 
⚠️ Important :
L’équation est écrite avec un **signe −**, donc **l’offset est POSITIF dans le circuit**, mais **soustrait dans la formule**.
 
---
 
## ✅ Étape 3 — Fonction de transfert finale
 
$$
\boxed{V_{out} = 3.64,V_{in} - 3.18}
$$
 
👉 C’est **exactement** ce qu’ils veulent dans la ligne :
 
```
Vout = ____ · Vin − ____ , V
```
 
---
 
# 🟦 PARTIE B — RÉSISTANCE RG (INA114)
 
## 🔹 Formule du gain INA114
 
$$
G = 1 + \frac{50,000}{R_G}
$$
 
On veut :
$$
G = 3.636
$$
 
---
 
## ✅ Étape 4 — Calcul de (R_G)
 
$$
3.636 = 1 + \frac{50,000}{R_G}
$$
 
$$
2.636 = \frac{50,000}{R_G}
$$
 
$$
R_G = \frac{50,000}{2.636}
$$
 
$$
R_G = 18,970\ \Omega
$$
 
$$
R_G \approx 19.0\ \text{k}\Omega
$$
 
✅ **Résistance théorique** :
$$
\boxed{R_G \approx 19\ \text{k}\Omega}
$$
 
👉 En pratique :
R4 (potentiomètre) + R5 (résistance fixe) ≈ 19 kΩ
 
---
 
# 🟦 PARTIE C — DIVISEUR DE TENSION (Vin)
 
On choisit :
 
* (R_2 = 10\ \text{k}\Omega) (potentiomètre)
* Alimentation : ±12 V
* Vin doit aller de −0.5 V à +2.25 V
 
---
 
## ✅ Étape 5 — Courant dans le diviseur
 
Tension totale sur le potentiomètre :
$$
\Delta V = 2.25 - (-0.5) = 2.75\ \text{V}
$$
 
Choix standard de labo :
$$
\boxed{I = 100\ \mu\text{A}}
$$
 
---
 
## ✅ Étape 6 — Calcul de (R_1)
 
Entre **+12 V** et **Vin(max) = 2.25 V** :
 
$$
R_1 = \frac{12 - 2.25}{100\mu A}
$$
 
$$
R_1 = \frac{9.75}{0.0001}
$$
 
$$
R_1 = 97.5\ \text{k}\Omega
$$
 
---
 
## ✅ Étape 7 — Calcul de (R_3)
 
Entre **Vin(min) = −0.5 V** et **−12 V** :
 
$$
R_3 = \frac{-0.5 - (-12)}{100\mu A}
$$
 
$$
R_3 = \frac{11.5}{0.0001}
$$
 
$$
R_3 = 115\ \text{k}\Omega
$$
 
---
 
## ✅ Étape 8 — Valeurs normalisées (10%)
 
On prend la **valeur inférieure la plus proche** :
 
* (R_1 = 91\ \text{k}\Omega)
* (R_3 = 110\ \text{k}\Omega)
 
✅ **Choix final** :
$$
\boxed{R_1 = 91\ \text{k}\Omega,\quad R_3 = 110\ \text{k}\Omega}
$$
 
---
 
## ✅ Étape 9 — Vérification du fonctionnement
 
Résistance totale :
$$
R_{tot} = 91k + 10k + 110k = 211k
$$
 
Courant réel :
$$
I = \frac{24}{211k} \approx 114\ \mu A
$$
 
➡️ Ce courant permet **largement** d’atteindre :
 
* (V_{in(min)} < -0.5\ \text{V})
* (V_{in(max)} > 2.25\ \text{V})
 
✅ **Conclusion** :
$$
\boxed{\text{True}}
$$
 
---
 
# 🧾 RÉSUMÉ À REMPLIR (PROPRE)
 
* Gain : **3.64**
* (R_G) : **19 kΩ**
* (V_{off}) : **3.18 V**
* Fonction :
  $$
  V_{out} = 3.64,V_{in} - 3.18
  $$
* Courant : **100 µA**
* (R_1 = 91\ \text{k}\Omega)
* (R_3 = 110\ \text{k}\Omega)
* Validation : **True**
 
---
 