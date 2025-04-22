# Documentation des Composants Dreamscape

Ce document complète la charte graphique interactive (`design-system.html`) et fournit des détails techniques pour les développeurs concernant les composants UI de Dreamscape, leurs états et les animations.

## Table des matières

- [Bibliothèque de Composants](#bibliothèque-de-composants)
  - [Boutons](#boutons)
  - [Cartes](#cartes)
  - [Formulaires](#formulaires)
  - [Navigation](#navigation)
- [États des Composants](#états-des-composants)
  - [Normal](#normal)
  - [Hover](#hover)
  - [Focus](#focus)
  - [Active](#active)
  - [Disabled](#disabled)
  - [Error](#error)
- [Animations et Transitions](#animations-et-transitions)
  - [Animations Prédéfinies](#animations-prédéfinies)
  - [Transitions](#transitions)
  - [Timing et Durées](#timing-et-durées)

## Bibliothèque de Composants

### Boutons

#### Bouton Primaire
```jsx
<button className="px-4 py-2 bg-gradient-to-r from-orange-400 to-pink-600 text-white rounded-md hover:opacity-90 transition shadow-sm">
  Bouton Primaire
</button>
```

#### Bouton Secondaire (Orange)
```jsx
<button className="px-4 py-2 bg-orange-500 text-white rounded-md hover:bg-orange-600 transition shadow-sm">
  Bouton Orange
</button>
```

#### Bouton Tertiaire (Outline)
```jsx
<button className="px-4 py-2 border border-gray-300 rounded-md hover:bg-gray-100 transition-colors">
  Bouton Tertiaire
</button>
```

#### Bouton Texte
```jsx
<button className="px-4 py-2 text-orange-500 hover:underline transition">
  Bouton Texte
</button>
```

#### Bouton avec Icône
```jsx
<button className="flex items-center gap-2 px-4 py-2 bg-gradient-to-r from-orange-400 to-pink-600 text-white rounded-md hover:opacity-90 transition shadow-sm">
  <IconName className="w-4 h-4" />
  <span>Avec Icône</span>
</button>
```

### Cartes

#### Carte Standard
```jsx
<div className="p-6 bg-white rounded-xl shadow-sm hover:shadow-md transition-shadow">
  <h4 className="font-medium mb-2">Titre de la carte</h4>
  <p className="text-sm text-gray-600 mb-4">Description de la carte avec quelques détails supplémentaires.</p>
  <button className="text-sm text-orange-500 hover:underline">En savoir plus</button>
</div>
```

#### Carte avec Image
```jsx
<div className="bg-white rounded-xl shadow-sm overflow-hidden hover:shadow-md transition-shadow">
  <div className="w-full h-48 bg-gray-200 overflow-hidden">
    <img 
      src="image-url.jpg" 
      alt="Description" 
      className="w-full h-full object-cover transition-transform duration-300 hover:scale-105"
    />
  </div>
  <div className="p-4">
    <h4 className="font-medium mb-2">Titre</h4>
    <p className="text-sm text-gray-600">Description</p>
  </div>
</div>
```

#### Carte de Destination
```jsx
<div className="relative aspect-[3/4] rounded-xl overflow-hidden group">
  <img 
    src="destination-image.jpg" 
    alt="Destination" 
    className="absolute inset-0 w-full h-full object-cover transition-transform duration-500 group-hover:scale-110"
  />
  <div className="absolute inset-0 bg-gradient-to-t from-black/80 via-black/40 to-transparent"></div>
  <div className="absolute bottom-0 p-6">
    <h4 className="text-2xl font-bold text-white mb-2">Nom de la destination</h4>
    <p className="text-gray-300 mb-4">Description</p>
    <button className="bg-white/20 hover:bg-white/30 backdrop-blur-md px-4 py-2 rounded-md transition-colors text-white">
      Découvrir
    </button>
  </div>
</div>
```

### Formulaires

#### Champ de Texte
```jsx
<div>
  <label className="block text-sm font-medium text-gray-700 mb-1">Label</label>
  <input 
    type="text" 
    className="w-full px-3 py-2 border border-gray-200 rounded-lg focus:outline-none focus:ring-2 focus:ring-orange-500/20" 
    placeholder="Placeholder"
  />
</div>
```

#### Menu Déroulant
```jsx
<div>
  <label className="block text-sm font-medium text-gray-700 mb-1">Label</label>
  <select className="w-full px-3 py-2 border border-gray-200 rounded-lg focus:outline-none focus:ring-2 focus:ring-orange-500/20">
    <option>Option 1</option>
    <option>Option 2</option>
    <option>Option 3</option>
  </select>
</div>
```

#### Case à Cocher
```jsx
<div className="flex items-center">
  <input 
    type="checkbox" 
    className="h-4 w-4 text-orange-600 focus:ring-orange-500 border-gray-300 rounded"
    id="checkbox-id"
  />
  <label htmlFor="checkbox-id" className="ml-2 block text-sm text-gray-700">
    Texte de la case
  </label>
</div>
```

#### Champ avec Erreur
```jsx
<div>
  <label className="block text-sm font-medium text-gray-700 mb-1">Email</label>
  <input 
    type="email" 
    className="w-full px-3 py-2 border border-red-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-red-500/20" 
    placeholder="Entrez votre email"
  />
  <p className="mt-1 text-sm text-red-600">Veuillez entrer un email valide</p>
</div>
```

### Navigation

#### Barre de Navigation
```jsx
<nav className="fixed w-full z-50 bg-black/20 backdrop-blur-md">
  <div className="container mx-auto px-4">
    <div className="flex items-center justify-between h-16">
      <div className="flex items-center gap-2">
        <div className="h-8 w-8 rounded-full bg-orange-500 flex items-center justify-center text-white">
          D
        </div>
        <span className="text-xl font-bold">Dreamscape</span>
      </div>
      
      <div className="hidden md:flex items-center gap-6">
        <a href="#" className="text-orange-500 font-medium">Home</a>
        <a href="#" className="hover:text-orange-500 transition-colors">Destinations</a>
        <a href="#" className="hover:text-orange-500 transition-colors">Experiences</a>
        <a href="#" className="hover:text-orange-500 transition-colors">About</a>
      </div>
      
      <button className="md:hidden">
        <svg xmlns="http://www.w3.org/2000/svg" className="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M4 6h16M4 12h16M4 18h16" />
        </svg>
      </button>
    </div>
  </div>
</nav>
```

#### Menu Mobile
```jsx
<div className="fixed inset-0 bg-gray-900/50 backdrop-blur-sm z-50">
  <div className="h-full w-64 bg-white p-6">
    <div className="flex justify-between items-center mb-8">
      <div className="flex items-center gap-2">
        <div className="h-8 w-8 rounded-full bg-orange-500 flex items-center justify-center text-white">
          D
        </div>
        <span className="text-xl font-bold">Dreamscape</span>
      </div>
      <button>
        <svg xmlns="http://www.w3.org/2000/svg" className="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M6 18L18 6M6 6l12 12" />
        </svg>
      </button>
    </div>
    
    <div className="space-y-4">
      <a href="#" className="block py-2 text-orange-500 font-medium">Home</a>
      <a href="#" className="block py-2 hover:text-orange-500 transition-colors">Destinations</a>
      <a href="#" className="block py-2 hover:text-orange-500 transition-colors">Experiences</a>
      <a href="#" className="block py-2 hover:text-orange-500 transition-colors">About</a>
    </div>
  </div>
</div>
```

## États des Composants

### Normal
L'état par défaut d'un composant sans aucune interaction utilisateur.

### Hover
Appliqué lorsque l'utilisateur survole un élément avec le curseur.

**Implémentations communes:**
- Boutons: `hover:opacity-90`, `hover:bg-orange-600`, `hover:bg-gray-100`
- Liens: `hover:text-orange-500`, `hover:underline`
- Cartes: `hover:shadow-md`
- Images: `group-hover:scale-110` (avec parent ayant la classe `group`)

### Focus
Appliqué lorsqu'un élément reçoit le focus, généralement via la navigation au clavier.

**Implémentations communes:**
- Champs de formulaire: `focus:outline-none focus:ring-2 focus:ring-orange-500/20`
- Boutons: ajouter `focus:ring-2 focus:ring-orange-500/20 focus:outline-none` 

### Active
Appliqué pendant le clic actif sur un élément.

**Implémentations communes:**
- Boutons: `active:scale-95` (effet de pression)
- Onglets: `border-b-2 border-orange-500 text-orange-500` (pour l'onglet actif)

### Disabled
Appliqué aux éléments qui ne sont pas actuellement disponibles pour l'interaction.

**Implémentations communes:**
```jsx
<button 
  disabled 
  className="px-4 py-2 bg-gray-300 text-gray-500 rounded-md cursor-not-allowed"
>
  Bouton Désactivé
</button>
```

### Error
Appliqué pour indiquer une erreur dans les formulaires ou alertes.

**Implémentations communes:**
- Bordures: `border-red-300`
- Focus: `focus:ring-red-500/20`
- Texte: `text-red-600`

## Animations et Transitions

### Animations Prédéfinies

#### Rotation Lente
```jsx
<div className="animate-spin-slow">
  <!-- Contenu -->
</div>
```

```css
@keyframes spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

.animate-spin-slow {
  animation: spin 20s linear infinite;
}
```

#### Flottement
```jsx
<div className="animate-float-slow">
  <!-- Contenu -->
</div>
```

```css
@keyframes float {
  0%, 100% { 
    transform: translateY(0); 
  }
  50% { 
    transform: translateY(-20px); 
  }
}

.animate-float-slow {
  animation: float 15s ease-in-out infinite;
}
```

### Transitions

#### Transition de Base
Transition générale pour la plupart des interactions:
```css
.transition {
  transition-property: color, background-color, border-color, text-decoration-color, fill, stroke, opacity, box-shadow, transform, filter, backdrop-filter;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  transition-duration: 150ms;
}
```

#### Transition de Couleurs
Pour les changements de couleur uniquement:
```css
.transition-colors {
  transition-property: color, background-color, border-color, text-decoration-color, fill, stroke;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  transition-duration: 150ms;
}
```

#### Transition d'Opacité
Pour les effets de fondu:
```css
.transition-opacity {
  transition-property: opacity;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  transition-duration: 150ms;
}
```

#### Transition d'Ombre
Pour les effets d'ombre au survol:
```css
.transition-shadow {
  transition-property: box-shadow;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  transition-duration: 150ms;
}
```

#### Transition de Transformation
Pour les effets de zoom, rotation, etc:
```css
.transition-transform {
  transition-property: transform;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  transition-duration: 150ms;
}
```

### Timing et Durées

Les durées standard pour les transitions:

- Court (rapide): `duration-150` (150ms)
- Moyen (standard): `duration-300` (300ms)
- Long (lent): `duration-500` (500ms)
- Très long: `duration-1000` (1000ms)

Pour les animations:
- Animation de rotation lente: 20s
- Animation de flottement: 15s

#### Courbes de Timing

- Par défaut: `ease-in-out` (cubic-bezier(0.4, 0, 0.2, 1))
- Entrée douce: `ease-out` (cubic-bezier(0, 0, 0.2, 1))
- Sortie douce: `ease-in` (cubic-bezier(0.4, 0, 1, 1))
- Linéaire: `linear` (utilisé pour les rotations continues)

---

## Bonnes Pratiques

1. **Accessibilité**: Assurez-vous que tous les états sont visibles même sans survol (pour les utilisateurs navigant au clavier).

2. **Performance**: 
   - Privilégiez les propriétés CSS qui déclenchent le moins de repaints (`opacity`, `transform`).
   - Évitez d'animer plus de 3 propriétés simultanément.

3. **Cohérence**:
   - Utilisez les mêmes durées et courbes de timing pour des interactions similaires.
   - Respectez la palette de couleurs et les arrondis définis dans la charte graphique.

4. **Responsive**:
   - Assurez-vous que les animations fonctionnent correctement sur les appareils mobiles.
   - Considérez réduire ou désactiver certaines animations sur les appareils à faible puissance via `@media (prefers-reduced-motion: reduce)`.
