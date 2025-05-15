# 1. Conception
## 1.1. Cahier des Charges
## 1.2. Presentation Hardware
### 1.2.1. Le MCU : STM32F401RE
#### 1.2.1.1. Le CPU
32 bits -> entrées opérations ALU sur 32 bits
ARM Cortex-M4 + single precision FPU (Floating Point Unit)

**FPU :**

- additions
- soustractions
- multiplications
- divisions
- multiplication-accumulation
- operations avec racine carrée
- conversions entre virgule fixe and virgule flotante
- instructions pour des constantes virgule-flotante

**DMIPS :** Dhrystone MIPS -> spécifique pour comparer dans la même architecture
    https://www.elektroda.com/rtvforum/topic2908657.html
    https://en.wikipedia.org/wiki/Dhrystone

**CoreMark :** Métrique du Embedded Microprocessor Benchmark Consortium (EEMBC).

- manipulation de matrices
- operations mathematiques
- manipulations de pointeurs
- cyclic redundancy checks (CRC)

#### 1.2.1.2. Les peripheriques

(Images DS)

### 1.2.2. Bouton
(schema electrique bouton avec pullup/pulldown)

(explication du choix composant)

On a choisi d'utiliser le peripherique GPIO... (voir partie Mise en oeuvre)

### 1.2.3. Buzzeur (Passif)
(photo/schema electrique bouton)

(explication du choix composant)

On a choisi d'utiliser le peripherique TIMER...
    
### 1.2.4. Matrice LED
(photo/schema registre a decalage)

(explication du choix composant)

On a choisi d'utiliser le peripherique GPIO (avec Bit Banging)...

On pourra eventuellement utiliser SPI...

### 1.2.5. Mesure du temps (heure/calendrier)
(explication du choix de ce peripherique par rapport a une autre methode genre HAL_Delay ou timeur classique)

On a choisi d'utiliser le peripherique RTC...

### 1.2.6. Mesure de temperature
(photo/schema electrique capteur)

(explication du choix composant)

On a choisi d'utiliser le peripherique I2C...

### 1.2.7. Economie d'energie
(explication de l'interet du mode basse conso)

On a choisi d'utiliser le peripherique PWR...

# 2. Workflow de programmation systemes embarques
## 2.1 SDK/API
- STM32Cube
    - HAL et LL
    - Bare Metal

## 2.2 Ressources 
- DS 
La datasheet contient les informations qui sont specifiques au composant (en l'occurence MCU).
On trouve jamais des informations de programmation sur la datasheet.
- RM 
Le Reference Manual contient les informations des modes d'utilisation de chaque peripherque pour un ensemble de MCU de la meme famille. Il indique aussi comment programmer en BM (Bare Metal) c-a-d en utilisant les registres.
- UM
Le User Manual donne a l'utilisateur (au programmeur) les informations necessaires pour mettre en oeuvre les fonctionalites du MCU avec les librairies HAL et LL mises a disposition.
- (videos? bof...)

## 2.3 STM32CubeIDE
**Roudy et sa partie sur l'IDE**

# 3. Langague c
Etapes "compilation" (c-a-d passage de code source c vers langague machine):

- Pre-compilation
- Compilation
- ~~Assemblage~~ (car c'est relatif a l'assembleur uniquement mais les programmes comme gcc font aussi)
- Liaison

Courte explication :
- Syntaxe fonction
- Structures
- Pointeurs

# 4. Mise en oeuvre
## 4.1. Pas de lien direct avec le projet
### 4.1.1. Blinky
### 4.1.2. Sortie UART
Photo st-link explication conversion UART - USB
### 4.1.3. GPS
### 4.1.4. Memoire Flash

## 4.2. Fonctionalites **pour le projet**
J'ai fait expres de mettre uniquement les noms des peripheriques ici.
C'est fait expres pour montrer exactement le choix technologique.
Les parties de mise en oeuvre sont dans le meme ordre que celles qui explique les compostants choisi

### 4.2.1. GPIO (IN) lecture bloquante et avec systick (HAL_GetTick)
### 4.2.2. TIMER (OC/PWM)
### 4.2.3. Bit Banging avec GPIO (OUT) / NVIC Interruptions / SPI
### 4.2.4. RTC
### 4.2.5. I2C
### 4.2.6. PWR

**Mettez un maxxx de captures d'ecran pour justifier le code/cablage**
