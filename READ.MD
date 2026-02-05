Parfait Eunice, on fait **tous les calculs calmement, étape par étape**, en reliant chaque résistance à la **fonction de transfert demandée**.
On suit exactement ce que l’énoncé te guide à faire 👍

---

## 1️⃣ Comprendre le montage (super important)

Le 741 est câblé en **amplificateur inverseur avec offset**.

La forme générale du montage est :

$$
V_{out} = -\frac{R6}{R4+R5} , V_{in}
;;-;;
\frac{R6}{R2+R3} , V_{ref}
$$

👉 donc :

* **R4 + R5** règle le **gain**
* **R2 + R3** règle l’**offset**
* **R6** est déjà fixé
* **Vref** vient du **REF02 = 5 V**

---

## 2️⃣ Données imposées

* Fonction voulue :

$$
V_{out} = -1.18,V_{in} - 2.12
$$

* (R6 = 22;k\Omega)
* (V_{ref} = 5;V)
* R1 = **le plus grand potentiomètre multitours du kit**

👉 dans les kits ETC, c’est **100 kΩ**

✅ **R1 = 100 kΩ**

---

## 3️⃣ Calcul du gain → R4 + R5

On compare :

$$
-1.18 = -\frac{R6}{R4+R5}
$$

Donc :

$$
R4+R5 = \frac{R6}{1.18}
$$

$$
R4+R5 = \frac{22k}{1.18}
\approx 18.64;k\Omega
$$

✅ **R4 + R5 ≈ 18.6 kΩ**

---

## 4️⃣ Calcul de l’offset → R2 + R3

Offset voulu :

$$
-2.12 = -\frac{R6}{R2+R3} \cdot 5
$$

On simplifie :

$$
2.12 = \frac{22k}{R2+R3} \cdot 5
$$

$$
R2+R3 = \frac{22k \cdot 5}{2.12}
$$

$$
R2+R3 \approx 51.9;k\Omega
$$

✅ **R2 + R3 ≈ 52 kΩ**

---

## 5️⃣ Choix de R4 et R5 (gain)

Règles :

* potentiomètre ≈ **50–80%** de la valeur totale
* R5 = résistance **10% standard**

### Choix logique

* **R4 = 20 kΩ potentiomètre**
* On veut 18.6 kΩ total → on enlève un peu avec R5

$$
R5 = 2.2;k\Omega ;(\text{valeur 10% standard})
$$

Plage :
$$
R4+R5 = 2.2 \rightarrow 22.2;k\Omega
$$

✅ 18.6 kΩ est **dans la plage** ✔️

✅ **R4 = 20 kΩ (pot)**

✅ **R5 = 2.2 kΩ**

---

## 6️⃣ Choix de R2 et R3 (offset)

On vise ≈ 52 kΩ

### Choix logique

* **R2 = 50 kΩ potentiomètre**
* **R3 = 4.7 kΩ** (valeur standard)

Plage :
$$
R2+R3 = 4.7 \rightarrow 54.7;k\Omega
$$

✅ 51.9 kΩ est bien **dans la plage**

✅ **R2 = 50 kΩ (pot)**
✅ **R3 = 4.7 kΩ**

---

## 7️⃣ Récapitulatif FINAL (à remplir dans le tableau)

| Composant   | Valeur              |
| ----------- | ------------------- |
| **R1**      | **100 kΩ (pot)**    |
| **R6**      | **22 kΩ**           |
| **R4 + R5** | **18.6 kΩ (idéal)** |
| **R2 + R3** | **51.9 kΩ (idéal)** |
| **R4**      | **20 kΩ (pot)**     |
| **R5**      | **2.2 kΩ**          |
| **R2**      | **50 kΩ (pot)**     |
| **R3**      | **4.7 kΩ**          |

---

Si tu veux, prochain step 👉
🔹 on vérifie la **plage réelle de Vout**
🔹 ou je t’aide à **ajuster les pots sur la breadboard**
🔹 ou je te refais ça en **version rapport de labo** 📄
