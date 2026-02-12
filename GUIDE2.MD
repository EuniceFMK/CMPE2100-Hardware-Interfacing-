Parfait 👍 on va faire ça **étape par étape**, comme si tu n’avais jamais utilisé LabVIEW.
Je vais te guider exactement dans l’ordre demandé par l’énoncé.

On va construire ton VI progressivement.

---

# 🔵 PARTIE 1 – Créer la structure de base

## ✅ 1️⃣ Créer un nouveau VI

1. Ouvre **LabVIEW**
2. Clique sur **File → New VI**
3. Tu verras :

   * 🟦 Front Panel (interface)
   * 🟨 Block Diagram (Ctrl + E pour basculer)

---

# 🔵 PARTIE 2 – Créer l’interface (Front Panel)

On va créer les indicateurs exactement comme sur l’image.

## ✅ 2️⃣ Ajouter les indicateurs numériques

Dans le **Front Panel** :

### ➤ Clic droit → Numeric → Vertical Pointer Slide

Ajoute :

1. **V_SCC**
2. **Vdiff**
3. **V+**
4. **RSens (kΩ)**
5. **Relative Humidity (%)**

Renomme-les :

* Clique droit → Rename

---

## ✅ 3️⃣ Régler les formats d’affichage

### Pour :

* V_SCC
* Vdiff
* V+
* RSens

➡ Clic droit → Format & Precision
➡ Choisir **3 digits after decimal**

---

### Pour Relative Humidity :

➡ Format & Precision
➡ 1 digit after decimal

---

# 🔵 PARTIE 3 – Ajouter les LEDs

## ✅ 4️⃣ Ajouter les voyants LED

Dans Front Panel :

Clic droit → Boolean → Round LED

Ajoute 3 LEDs :

* 🔴 HIGH
* 🟢 GOOD
* ⚫ LOW

Renomme-les.

---

# 🔵 PARTIE 4 – Ajouter la While Loop

Passe au **Block Diagram** (Ctrl + E)

## ✅ 5️⃣ Ajouter la boucle principale

Clic droit → Structures → While Loop

Encadre tout avec la souris.

---

## ✅ 6️⃣ Ajouter le bouton STOP

Retour au Front Panel :

Clic droit → Boolean → Stop Button

Retour Block Diagram :
Relie le bouton STOP au terminal rouge de la boucle.

---

# 🔵 PARTIE 5 – Ajouter un délai de 250 ms

Dans Block Diagram :

Clic droit → Programming → Timing → Wait (ms)

Place-le dans la boucle.

Créer une constante 250 :
Clic droit sur l’entrée → Create Constant → mettre 250

---

# 🔵 PARTIE 6 – Lire l’Analog Discovery (AD2)

## ✅ 7️⃣ Ajouter le VI d’acquisition

Clic droit → Instrument I/O → Digilent → Analog Discovery → AI Configure / AI Read

(Si tu ne le vois pas, dis-moi, je t’expliquerai comment l’ajouter.)

Configure :

* Channel 1
* Continuous

---

# 🔵 PARTIE 7 – Convertir la tension ADC en Vout

Ton ADC mesure la sortie de ton ampli.

Tu dois juste connecter la sortie AI Read à ton indicateur :

➡ Relier la sortie tension à **V_SCC**

---

# 🔵 PARTIE 8 – Calculer Vdiff

Tu as trouvé que :

Gain = 23.2
Offset = -2.16

Formule donnée :

[
V_{out} = 23.2 (V+ - V-) - 2.16
]

On inverse :

[
Vdiff = (Vout + 2.16) / 23.2
]

---

## ✅ 8️⃣ Implémenter la formule

Dans Block Diagram :

Clic droit → Programming → Numeric

Ajoute :

* Add
* Divide

Construire :

```
Vdiff = (V_SCC + 2.16) / 23.2
```

Relier à l’indicateur Vdiff

---

# 🔵 PARTIE 9 – Calculer V+

D’après ton lab :

[
V+ = 2.5 + Vdiff
]

(2.5 V est le point milieu du pont)

Ajouter :

* Add

Relier à indicateur V+

---

# 🔵 PARTIE 10 – Calculer RSens

Formule du pont diviseur :

[
V+ = 5 \times \frac{R_{sens}}{R_{sens} + 33k}
]

On isole Rsens :

[
R_{sens} = \frac{33k \times V+}{5 - V+}
]

---

## ✅ Implémenter

Ajouter :

* Multiply
* Subtract
* Divide

Créer constante 33000

Relier à indicateur RSens

---

# 🔵 PARTIE 11 – Convertir RSens → Humidité %

Tu as trouvé :

Sensitivity = -8.67 %/kΩ
Offset ≈ +? (selon ton calcul)

Forme :

[
RH = -8.67 \times R_{sens} + Offset
]

Implémente avec :

* Multiply
* Add

Relier à indicateur Relative Humidity

---

# 🔵 PARTIE 12 – Configurer les LEDs

Selon l’énoncé :

* 🔴 HIGH : RH > 60%
* 🟢 GOOD : 25% < RH < 60%
* ⚫ LOW : RH < 25%

---

## Ajouter comparateurs :

Clic droit → Programming → Comparison

* Greater?
* Less?
* AND

### LOW :

RH < 25 → LED LOW

### HIGH :

RH > 60 → LED HIGH

### GOOD :

(RH > 25) AND (RH < 60)

Relier aux LEDs.

---

# 🔵 PARTIE 13 – Tester

1. Clique Run
2. Vérifie :

   * Les valeurs ont 3 décimales
   * RH a 1 décimale
   * LEDs changent correctement

---

# 🚀 Si tu veux, on peut maintenant :

* ✔ vérifier tes formules
* ✔ faire un schéma clair des connexions
* ✔ faire une version optimisée
* ✔ ou je peux te faire un résumé ultra simple spécial débutant

Dis-moi où tu bloques exactement 👌
