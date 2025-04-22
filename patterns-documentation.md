# Documentation des Patterns d'Interface Dreamscape

Ce document présente les patterns d'interface utilisateur et les composants réutilisables qui définissent l'expérience utilisateur de Dreamscape. Ces patterns assurent la cohérence visuelle et fonctionnelle à travers toute l'application.

## Table des matières

- [Patterns de Navigation](#patterns-de-navigation)
- [Patterns de Contenu](#patterns-de-contenu)
- [Patterns de Formulaires](#patterns-de-formulaires)
- [Patterns de Feedback](#patterns-de-feedback)
- [Patterns de Mise en Page](#patterns-de-mise-en-page)
- [Patterns d'Interaction](#patterns-dinteraction)
- [Patterns d'Accessibilité](#patterns-daccessibilité)

## Patterns de Navigation

### Navigation Principale

Le pattern de navigation principale utilise une barre de navigation fixe en haut de l'écran avec un fond semi-transparent et un effet de flou.

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

**Caractéristiques:**
- Barre fixe en haut de l'écran
- Fond semi-transparent avec effet de flou
- Logo et nom de l'application à gauche
- Liens de navigation au centre (masqués sur mobile)
- Menu hamburger sur mobile
- Indication visuelle de la page active

### Navigation Secondaire

Pour les sections avec plusieurs sous-pages, utilisez des onglets ou une navigation secondaire.

```jsx
<div className="border-b border-gray-200">
  <nav className="flex space-x-8" aria-label="Tabs">
    <a href="#" className="border-b-2 border-orange-500 text-orange-500 py-4 px-1 text-sm font-medium">
      Vue d'ensemble
    </a>
    <a href="#" className="border-b-2 border-transparent text-gray-500 hover:text-gray-700 hover:border-gray-300 py-4 px-1 text-sm font-medium">
      Activités
    </a>
    <a href="#" className="border-b-2 border-transparent text-gray-500 hover:text-gray-700 hover:border-gray-300 py-4 px-1 text-sm font-medium">
      Hébergements
    </a>
    <a href="#" className="border-b-2 border-transparent text-gray-500 hover:text-gray-700 hover:border-gray-300 py-4 px-1 text-sm font-medium">
      Avis
    </a>
  </nav>
</div>
```

### Fil d'Ariane (Breadcrumbs)

Pour indiquer la hiérarchie de navigation et permettre aux utilisateurs de revenir facilement aux pages précédentes.

```jsx
<nav className="flex" aria-label="Breadcrumb">
  <ol className="flex items-center space-x-2">
    <li>
      <a href="#" className="text-gray-500 hover:text-gray-700">
        Accueil
      </a>
    </li>
    <li>
      <svg className="h-5 w-5 text-gray-400" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
        <path fillRule="evenodd" d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z" clipRule="evenodd" />
      </svg>
    </li>
    <li>
      <a href="#" className="text-gray-500 hover:text-gray-700">
        Destinations
      </a>
    </li>
    <li>
      <svg className="h-5 w-5 text-gray-400" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
        <path fillRule="evenodd" d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z" clipRule="evenodd" />
      </svg>
    </li>
    <li>
      <span className="text-gray-700 font-medium">Paris</span>
    </li>
  </ol>
</nav>
```

## Patterns de Contenu

### Grille de Cartes

Pour afficher une collection d'éléments similaires, comme des destinations ou des expériences.

```jsx
<div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
  {/* Carte de Destination */}
  <div className="relative aspect-[3/4] rounded-xl overflow-hidden group">
    <img 
      src="destination-image.jpg" 
      alt="Destination" 
      className="absolute inset-0 w-full h-full object-cover transition-transform duration-500 group-hover:scale-110"
    />
    <div className="absolute inset-0 bg-gradient-to-t from-black/80 via-black/40 to-transparent"></div>
    <div className="absolute bottom-0 p-6">
      <h4 className="text-2xl font-bold text-white mb-2">Paris</h4>
      <p className="text-gray-300 mb-4">La ville lumière</p>
      <button className="bg-white/20 hover:bg-white/30 backdrop-blur-md px-4 py-2 rounded-md transition-colors text-white">
        Découvrir
      </button>
    </div>
  </div>
  
  {/* Répéter pour d'autres destinations */}
</div>
```

### Hero Section

Pour les pages d'accueil ou les sections principales, utilisez un hero avec une image de fond et un texte accrocheur.

```jsx
<div className="relative h-[80vh] flex items-center">
  <div className="absolute inset-0">
    <img 
      src="hero-image.jpg" 
      alt="Hero" 
      className="w-full h-full object-cover"
    />
    <div className="absolute inset-0 bg-black/50"></div>
  </div>
  
  <div className="container mx-auto px-4 relative z-10">
    <h1 className="text-4xl md:text-6xl font-bold text-white mb-4">
      Explorez le monde avec Dreamscape
    </h1>
    <p className="text-xl text-gray-200 mb-8 max-w-2xl">
      Découvrez des destinations uniques et créez des souvenirs inoubliables.
    </p>
    <button className="px-6 py-3 bg-gradient-to-r from-orange-400 to-pink-600 text-white rounded-md hover:opacity-90 transition shadow-sm text-lg">
      Commencer l'aventure
    </button>
  </div>
</div>
```

### Section avec Alternance

Pour présenter des informations en alternant texte et image.

```jsx
<div className="py-16">
  <div className="container mx-auto px-4">
    <div className="flex flex-col md:flex-row items-center gap-8 md:gap-16">
      <div className="w-full md:w-1/2">
        <h2 className="text-3xl font-bold mb-4">Découvrez des expériences uniques</h2>
        <p className="text-gray-600 mb-6">
          Nos voyages sont conçus pour vous offrir des expériences authentiques et mémorables. 
          Que vous recherchiez l'aventure, la détente ou la découverte culturelle, nous avons 
          le voyage parfait pour vous.
        </p>
        <ul className="space-y-3">
          <li className="flex items-start">
            <svg className="h-6 w-6 text-orange-500 mr-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M5 13l4 4L19 7" />
            </svg>
            <span>Expériences locales authentiques</span>
          </li>
          <li className="flex items-start">
            <svg className="h-6 w-6 text-orange-500 mr-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M5 13l4 4L19 7" />
            </svg>
            <span>Guides experts et passionnés</span>
          </li>
          <li className="flex items-start">
            <svg className="h-6 w-6 text-orange-500 mr-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M5 13l4 4L19 7" />
            </svg>
            <span>Hébergements soigneusement sélectionnés</span>
          </li>
        </ul>
      </div>
      <div className="w-full md:w-1/2">
        <img 
          src="experience-image.jpg" 
          alt="Expérience" 
          className="rounded-xl shadow-lg"
        />
      </div>
    </div>
  </div>
</div>
```

## Patterns de Formulaires

### Formulaire de Recherche

Pour permettre aux utilisateurs de rechercher des destinations ou des expériences.

```jsx
<div className="bg-white rounded-xl shadow-lg p-6">
  <form className="space-y-4">
    <div className="grid grid-cols-1 md:grid-cols-4 gap-4">
      <div>
        <label className="block text-sm font-medium text-gray-700 mb-1">Destination</label>
        <input 
          type="text" 
          className="w-full px-3 py-2 border border-gray-200 rounded-lg focus:outline-none focus:ring-2 focus:ring-orange-500/20" 
          placeholder="Où voulez-vous aller?"
        />
      </div>
      <div>
        <label className="block text-sm font-medium text-gray-700 mb-1">Date de départ</label>
        <input 
          type="date" 
          className="w-full px-3 py-2 border border-gray-200 rounded-lg focus:outline-none focus:ring-2 focus:ring-orange-500/20" 
        />
      </div>
      <div>
        <label className="block text-sm font-medium text-gray-700 mb-1">Date de retour</label>
        <input 
          type="date" 
          className="w-full px-3 py-2 border border-gray-200 rounded-lg focus:outline-none focus:ring-2 focus:ring-orange-500/20" 
        />
      </div>
      <div className="flex items-end">
        <button 
          type="submit" 
          className="w-full px-4 py-2 bg-gradient-to-r from-orange-400 to-pink-600 text-white rounded-md hover:opacity-90 transition shadow-sm"
        >
          Rechercher
        </button>
      </div>
    </div>
  </form>
</div>
```

### Formulaire d'Inscription/Connexion

Pour l'inscription et la connexion des utilisateurs.

```jsx
<div className="max-w-md mx-auto bg-white rounded-xl shadow-lg p-8">
  <h2 className="text-2xl font-bold mb-6 text-center">Connexion</h2>
  
  <form className="space-y-4">
    <div>
      <label className="block text-sm font-medium text-gray-700 mb-1">Email</label>
      <input 
        type="email" 
        className="w-full px-3 py-2 border border-gray-200 rounded-lg focus:outline-none focus:ring-2 focus:ring-orange-500/20" 
        placeholder="votre@email.com"
      />
    </div>
    
    <div>
      <label className="block text-sm font-medium text-gray-700 mb-1">Mot de passe</label>
      <input 
        type="password" 
        className="w-full px-3 py-2 border border-gray-200 rounded-lg focus:outline-none focus:ring-2 focus:ring-orange-500/20" 
        placeholder="••••••••"
      />
    </div>
    
    <div className="flex items-center justify-between">
      <div className="flex items-center">
        <input 
          type="checkbox" 
          className="h-4 w-4 text-orange-600 focus:ring-orange-500 border-gray-300 rounded"
          id="remember-me"
        />
        <label htmlFor="remember-me" className="ml-2 block text-sm text-gray-700">
          Se souvenir de moi
        </label>
      </div>
      <a href="#" className="text-sm text-orange-500 hover:underline">
        Mot de passe oublié?
      </a>
    </div>
    
    <button 
      type="submit" 
      className="w-full px-4 py-2 bg-gradient-to-r from-orange-400 to-pink-600 text-white rounded-md hover:opacity-90 transition shadow-sm"
    >
      Se connecter
    </button>
  </form>
  
  <div className="mt-6 text-center">
    <p className="text-sm text-gray-600">
      Pas encore de compte? 
      <a href="#" className="text-orange-500 hover:underline ml-1">
        S'inscrire
      </a>
    </p>
  </div>
</div>
```

## Patterns de Feedback

### Notifications Toast

Pour informer l'utilisateur d'une action réussie ou d'une erreur.

```jsx
<div className="fixed bottom-4 right-4 z-50">
  <div className="bg-white rounded-lg shadow-lg p-4 max-w-sm w-full border-l-4 border-green-500">
    <div className="flex items-start">
      <div className="flex-shrink-0">
        <svg className="h-6 w-6 text-green-500" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M5 13l4 4L19 7" />
        </svg>
      </div>
      <div className="ml-3 w-0 flex-1">
        <p className="text-sm font-medium text-gray-900">Succès!</p>
        <p className="mt-1 text-sm text-gray-500">Votre réservation a été confirmée.</p>
      </div>
      <div className="ml-4 flex-shrink-0 flex">
        <button className="bg-white rounded-md inline-flex text-gray-400 hover:text-gray-500 focus:outline-none">
          <span className="sr-only">Fermer</span>
          <svg className="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
            <path fillRule="evenodd" d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z" clipRule="evenodd" />
          </svg>
        </button>
      </div>
    </div>
  </div>
</div>
```

### Modales de Confirmation

Pour demander confirmation avant une action importante.

```jsx
<div className="fixed inset-0 bg-gray-900/50 backdrop-blur-sm z-50 flex items-center justify-center">
  <div className="bg-white rounded-xl shadow-xl max-w-md w-full p-6">
    <h3 className="text-xl font-bold mb-4">Confirmer la suppression</h3>
    <p className="text-gray-600 mb-6">
      Êtes-vous sûr de vouloir supprimer cette réservation? Cette action est irréversible.
    </p>
    <div className="flex justify-end space-x-4">
      <button className="px-4 py-2 border border-gray-300 rounded-md hover:bg-gray-100 transition-colors">
        Annuler
      </button>
      <button className="px-4 py-2 bg-red-500 text-white rounded-md hover:bg-red-600 transition-colors">
        Supprimer
      </button>
    </div>
  </div>
</div>
```

### Indicateurs de Progression

Pour montrer la progression d'un processus en plusieurs étapes.

```jsx
<div className="py-8">
  <div className="max-w-3xl mx-auto">
    <div className="flex items-center justify-between mb-8">
      <div className="flex flex-col items-center">
        <div className="w-10 h-10 rounded-full bg-orange-500 text-white flex items-center justify-center">
          1
        </div>
        <span className="mt-2 text-sm font-medium">Informations</span>
      </div>
      <div className="flex-1 h-1 bg-orange-500"></div>
      <div className="flex flex-col items-center">
        <div className="w-10 h-10 rounded-full bg-orange-500 text-white flex items-center justify-center">
          2
        </div>
        <span className="mt-2 text-sm font-medium">Options</span>
      </div>
      <div className="flex-1 h-1 bg-gray-200"></div>
      <div className="flex flex-col items-center">
        <div className="w-10 h-10 rounded-full bg-gray-200 text-gray-500 flex items-center justify-center">
          3
        </div>
        <span className="mt-2 text-sm font-medium">Confirmation</span>
      </div>
    </div>
  </div>
</div>
```

## Patterns de Mise en Page

### Layout avec Sidebar

Pour les pages qui nécessitent une navigation latérale.

```jsx
<div className="flex min-h-screen">
  {/* Sidebar */}
  <div className="w-64 bg-gray-50 border-r border-gray-200 hidden md:block">
    <div className="p-6">
      <h2 className="text-lg font-bold mb-4">Mon Compte</h2>
      <nav className="space-y-1">
        <a href="#" className="flex items-center px-3 py-2 text-orange-500 bg-orange-50 rounded-md">
          <svg className="h-5 w-5 mr-3" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z" />
          </svg>
          Profil
        </a>
        <a href="#" className="flex items-center px-3 py-2 text-gray-700 hover:bg-gray-100 rounded-md">
          <svg className="h-5 w-5 mr-3" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M3 10h18M7 15h1m4 0h1m-7 4h12a3 3 0 003-3V8a3 3 0 00-3-3H6a3 3 0 00-3 3v8a3 3 0 003 3z" />
          </svg>
          Réservations
        </a>
        <a href="#" className="flex items-center px-3 py-2 text-gray-700 hover:bg-gray-100 rounded-md">
          <svg className="h-5 w-5 mr-3" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z" />
            <path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z" />
          </svg>
          Paramètres
        </a>
      </nav>
    </div>
  </div>
  
  {/* Contenu principal */}
  <div className="flex-1 p-8">
    <h1 className="text-2xl font-bold mb-6">Mon Profil</h1>
    <div className="bg-white rounded-xl shadow-sm p-6">
      {/* Contenu de la page */}
    </div>
  </div>
</div>
```

### Layout avec Grille Responsive

Pour organiser le contenu en colonnes adaptatives.

```jsx
<div className="container mx-auto px-4 py-8">
  <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
    {/* Colonne 1 */}
    <div className="bg-white rounded-xl shadow-sm p-6">
      <h3 className="text-lg font-bold mb-4">Informations de base</h3>
      <p className="text-gray-600">
        Contenu de la première colonne qui s'adapte à la largeur de l'écran.
      </p>
    </div>
    
    {/* Colonne 2 */}
    <div className="bg-white rounded-xl shadow-sm p-6">
      <h3 className="text-lg font-bold mb-4">Détails supplémentaires</h3>
      <p className="text-gray-600">
        Contenu de la deuxième colonne qui s'adapte à la largeur de l'écran.
      </p>
    </div>
    
    {/* Colonne 3 */}
    <div className="bg-white rounded-xl shadow-sm p-6">
      <h3 className="text-lg font-bold mb-4">Options avancées</h3>
      <p className="text-gray-600">
        Contenu de la troisième colonne qui s'adapte à la largeur de l'écran.
      </p>
    </div>
  </div>
</div>
```

## Patterns d'Interaction

### Accordéon

Pour afficher/masquer du contenu de manière interactive.

```jsx
<div className="space-y-4">
  <div className="border border-gray-200 rounded-lg overflow-hidden">
    <button className="w-full flex justify-between items-center p-4 bg-gray-50 hover:bg-gray-100 transition-colors">
      <span className="font-medium">Comment fonctionne la réservation?</span>
      <svg className="h-5 w-5 text-gray-500" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M19 9l-7 7-7-7" />
      </svg>
    </button>
    <div className="p-4 border-t border-gray-200">
      <p className="text-gray-600">
        Le processus de réservation est simple. Choisissez votre destination, sélectionnez vos dates,
        et suivez les étapes pour finaliser votre réservation. Vous recevrez une confirmation par email.
      </p>
    </div>
  </div>
  
  <div className="border border-gray-200 rounded-lg overflow-hidden">
    <button className="w-full flex justify-between items-center p-4 bg-gray-50 hover:bg-gray-100 transition-colors">
      <span className="font-medium">Politique d'annulation</span>
      <svg className="h-5 w-5 text-gray-500" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M19 9l-7 7-7-7" />
      </svg>
    </button>
    <div className="p-4 border-t border-gray-200">
      <p className="text-gray-600">
        Vous pouvez annuler votre réservation jusqu'à 24 heures avant votre arrivée sans frais.
        Pour les annulations moins de 24 heures à l'avance, des frais peuvent s'appliquer.
      </p>
    </div>
  </div>
</div>
```

### Carrousel d'Images

Pour présenter une collection d'images de manière interactive.

```jsx
<div className="relative">
  <div className="overflow-hidden rounded-xl">
    <div className="flex transition-transform duration-500 ease-in-out">
      <div className="w-full flex-shrink-0">
        <img 
          src="image1.jpg" 
          alt="Image 1" 
          className="w-full h-64 object-cover"
        />
      </div>
      <div className="w-full flex-shrink-0">
        <img 
          src="image2.jpg" 
          alt="Image 2" 
          className="w-full h-64 object-cover"
        />
      </div>
      <div className="w-full flex-shrink-0">
        <img 
          src="image3.jpg" 
          alt="Image 3" 
          className="w-full h-64 object-cover"
        />
      </div>
    </div>
  </div>
  
  <div className="absolute bottom-4 left-0 right-0 flex justify-center space-x-2">
    <button className="w-2 h-2 rounded-full bg-white"></button>
    <button className="w-2 h-2 rounded-full bg-white/50"></button>
    <button className="w-2 h-2 rounded-full bg-white/50"></button>
  </div>
  
  <button className="absolute left-2 top-1/2 transform -translate-y-1/2 bg-white/80 hover:bg-white rounded-full p-2">
    <svg className="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
      <path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M15 19l-7-7 7-7" />
    </svg>
  </button>
  
  <button className="absolute right-2 top-1/2 transform -translate-y-1/2 bg-white/80 hover:bg-white rounded-full p-2">
    <svg className="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
      <path strokeLinecap="round" strokeLinejoin="round" strokeWidth="2" d="M9 5l7 7-7 7" />
    </svg>
  </button>
</div>
```

## Patterns d'Accessibilité

### Navigation au Clavier

Assurez-vous que tous les éléments interactifs sont accessibles au clavier.

```jsx
<button 
  className="px-4 py-2 bg-gradient-to-r from-orange-400 to-pink-600 text-white rounded-md hover:opacity-90 transition shadow-sm focus:outline-none focus:ring-2 focus:ring-orange-500/20"
  tabIndex="0"
  aria-label="Découvrir cette destination"
>
  Découvrir
</button>
```

### Messages d'Erreur Accessibles

Pour les formulaires, assurez-vous que les messages d'erreur sont correctement associés aux champs.

```jsx
<div>
  <label htmlFor="email" className="block text-sm font-medium text-gray-700 mb-1">Email</label>
  <input 
    type="email" 
    id="email"
    aria-invalid="true"
    aria-describedby="email-error"
    className="w-full px-3 py-2 border border-red-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-red-500/20" 
    placeholder="Entrez votre email"
  />
  <p id="email-error" className="mt-1 text-sm text-red-600">Veuillez entrer un email valide</p>
</div>
```

### Contraste et Lisibilité

Assurez-vous que le texte est suffisamment contrasté avec son arrière-plan.

```jsx
<div className="bg-gray-900 text-white p-6 rounded-xl">
  <h3 className="text-xl font-bold mb-2">Texte sur fond sombre</h3>
  <p className="text-gray-300">
    Ce texte utilise un contraste suffisant pour être lisible sur un fond sombre.
  </p>
</div>
```

---

## Bonnes Pratiques pour les Patterns

1. **Cohérence**: Utilisez les mêmes patterns pour des fonctionnalités similaires à travers l'application.

2. **Accessibilité**: Assurez-vous que tous les patterns sont accessibles aux utilisateurs de technologies d'assistance.

3. **Responsive**: Concevez des patterns qui fonctionnent bien sur tous les appareils, du mobile au desktop.

4. **Performance**: Optimisez les patterns pour de meilleures performances, en particulier pour les animations et les transitions.

5. **Feedback**: Fournissez toujours un feedback visuel clair pour les actions de l'utilisateur.
