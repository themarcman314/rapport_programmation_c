# Conception
## Presentation Hardware
### Le MCU : STM32F401RE
#### Le CPU
32 bits -> entrées opérations ALU sur 32 bits
ARM Cortex-M4 + single precision FPU (Floating Point Unit)
FPU : 
- additions
- soustractions
- multiplications
- divisions
- multiplication-accumulation
- operations avec racine carrée
- conversions entre virgule fixe and virgule flotante
- instructions pour des constantes virgule-flotante

DMIPS : Dhrystone MIPS -> spécifique pour comparer dans la même architecture
    https://www.elektroda.com/rtvforum/topic2908657.html
    https://en.wikipedia.org/wiki/Dhrystone

CoreMark : Métrique du Embedded Microprocessor Benchmark Consortium (EEMBC).
- manipulation de matrices
- operations mathematiques
- manipulations de pointeurs
- cyclic redundancy checks (CRC)

#### Les peripheriques
(Images DS)

### Bouton
(schema electrique bouton avec pullup/pulldown)

(explication du choix composant)

On a choisi d'utiliser le peripherique GPIO... (voir partie Mise en oeuvre)
### Buzzeur (Passif)
(photo/schema electrique bouton)

(explication du choix composant)

On a choisi d'utiliser le peripherique TIMER...
### Matrice LED
(photo/schema registre a decalage)

(explication du choix composant)

On a choisi d'utiliser le peripherique GPIO (avec Bit Banging)...

On pourra eventuellement utiliser SPI...
### Mesure du temps (heure/calendrier)
(explication du choix de ce peripherique par rapport a une autre methode genre HAL_Delay ou timeur classique)

On a choisi d'utiliser le peripherique RTC...
### Mesure de temperature
(photo/schema electrique capteur)

(explication du choix composant)

On a choisi d'utiliser le peripherique I2C...
### Economie d'energie
(explication de l'interet du mode basse conso)

On a choisi d'utiliser le peripherique PWR...

# Workflow de programmation systemes embarques
- STM32Cube
    - HAL et LL
    - Bare Metal
- DS 
La datasheet contient les informations qui sont specifiques au composant (en l'occurence MCU).
On trouve jamais des informations de programmation sur la datasheet.
- RM 
Le Reference Manual contient les informations des modes d'utilisation de chaque peripherque pour un ensemble de MCU de la meme famille. Il indique aussi comment programmer en BM (Bare Metal) c-a-d en utilisant les registres.
- UM
Le User Manual donne a l'utilisateur (au programmeur) les informations necessaires pour mettre en oeuvre les fonctionalites du MCU avec les librairies HAL et LL mises a disposition.

# Mise en oeuvre
## Pas de lien direct avec le projet
### Blinky
### Sortie UART
### GPS

## Fonctionalites **pour le projet**
J'ai fait expres de mettre uniquement les noms des peripheriques ici.
C'est fait expres pour montrer exactement le choix technologique.
Les parties de mise en oeuvre sont dans le meme ordre que celles qui explique les compostants choisi

### GPIO (IN) lecture bloquante et avec systick (HAL_GetTick)
### TIMER (OC/PWM)
### Bit Banging avec GPIO (OUT) / NVIC Interruptions / SPI
### RTC
### I2C
### PWR

**Mettez un maxxx de captures d'ecran pour justifier le code/cablage**
