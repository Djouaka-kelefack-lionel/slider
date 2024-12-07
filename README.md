# Slider 3D avec Effet Carrousel

Un slider 3D créé en HTML et CSS pur, présentant un effet de carrousel rotatif avec des images qui tournent dans un espace 3D.

## Structure du Projet

```

├── index.html
├── style.css
├── pira.jpg (image d'arrière-plan)
└── img/
├── 1.jpg
├── 2.jpg
├── 3.jpg
├── 4.jpg
├── 5.jpg
├── 6.jpg
└── 7.jpg

```

## Fonctionnalités

- Rotation automatique des images en 3D
- Pause de la rotation au survol
- Effet de zoom et d'amélioration visuelle au survol des images
- Arrière-plan avec effet de superposition dégradé
- 7 images disposées en cercle dans l'espace 3D

## Détail du Code

### 1. HTML Structure

html


```css
/* Exemple de code CSS */

<div class="container">
<div class="slider">
<div class="slider-item">
<img src="/img/1.jpg" alt="Image 1">
</div>
<!-- Répété pour les 7 images -->
</div>
</div>

```


### 2. CSS Expliqué

#### Configuration de Base

css
{
margin: 0;
padding: 0;
box-sizing: border-box;
}



#### Arrière-plan et Overlay

css

```

body {
background: url('/pira.jpg') no-repeat center center fixed;
background-size: cover;
}
body::before {
/ Overlay avec dégradé pour améliorer le contraste /
background: linear-gradient(45deg, rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.4));
}

```

#### Configuration du Slider


css

```
.slider {
width: 200px;
height: 300px;
transform-style: preserve-3d;
animation: rotate 30s linear infinite;
}

```

### 3. Explication des Positions des Images (nth-child)

Le positionnement des images utilise une combinaison de `rotateY` et `translateZ` pour créer un cercle 3D :


css

```
.slider-item:nth-child(1) { transform: rotateY(0deg) translateZ(500px); }
.slider-item:nth-child(2) { transform: rotateY(51.43deg) translateZ(500px); }
.slider-item:nth-child(3) { transform: rotateY(102.86deg) translateZ(500px); }
.slider-item:nth-child(4) { transform: rotateY(154.29deg) translateZ(500px); }
.slider-item:nth-child(5) { transform: rotateY(205.71deg) translateZ(500px); }
.slider-item:nth-child(6) { transform: rotateY(257.14deg) translateZ(500px); }
.slider-item:nth-child(7) { transform: rotateY(308.57deg) translateZ(500px); }

```

#### Calcul des Angles :
- 360° divisé par 7 images = 51.43° entre chaque image
- 1ère image : 0°
- 2ème image : 51.43°
- 3ème image : 102.86° (2 × 51.43°)
- etc.

#### Effet de Survol :

css

```
.slider-item:hover {
transform: scale(1.3) translateZ(700px);
filter: brightness(1.2) contrast(1.1);
z-index: 2;
}

```

### 4. Animation


css

```
@keyframes rotate {
from { transform: rotateY(0deg); }
to { transform: rotateY(360deg); }
}

```


## Personnalisation

### Ajustements Possibles :
1. **Vitesse de Rotation**
   - Modifier la durée dans `animation: rotate 30s linear infinite`

2. **Taille des Images**
   - Ajuster `width` et `height` dans `.slider`

3. **Rayon du Cercle**
   - Modifier la valeur de `translateZ` dans les positions des images

4. **Effet de Survol**
   - Ajuster `scale` et `translateZ` dans `.slider-item:hover`

5. **Couleurs et Effets**
   - Modifier le gradient de l'overlay
   - Ajuster les valeurs de `brightness` et `contrast`

## Installation

1. Créez la structure de dossiers comme indiqué
2. Placez vos images dans le dossier `img/`
3. Assurez-vous que les chemins dans le HTML correspondent à vos images
4. Ouvrez index.html dans un navigateur moderne

## Compatibilité

- Fonctionne sur les navigateurs modernes supportant CSS3
- Nécessite le support des transformations 3D CSS
- Recommandé : Chrome, Firefox, Safari, Edge récents
