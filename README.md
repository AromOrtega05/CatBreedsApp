🐱 Cat Breeds App
Explora, descubre y aprende sobre diferentes razas de felinos de manera visual y atractiva.

Una aplicación iOS desarrollada en Swift (UIKit) que permite a los usuarios explorar razas de gatos, ver detalles completos, registrarse e iniciar sesión usando Firebase, y consumir datos desde TheCatAPI.

✨ Características Destacadas
🔐 Autenticación Avanzada
Inicio de sesión con correo electrónico y contraseña.

Registro de nuevos usuarios con validación en tiempo real.

Recuperación de contraseña mediante enlace por correo.

Gestión de sesión persistente con Firebase Auth.

🐈 Exploración de Razas
Listado completo de razas de gatos con imágenes.

Búsqueda en tiempo real por nombre u origen.

Pull-to-refresh para actualizar datos.

Estados visuales (cargando, vacío, error).

Navegación fluida a vista de detalle.

📄 Detalles Completos
Imagen representativa de alta calidad.

Información detallada: origen, temperamento, descripción.

Datos prácticos: peso y esperanza de vida.

Interfaz optimizada para lectura.

👤 Perfil Personalizado
Visualización de datos del usuario.

Información persistente en Firestore.

Cierre de sesión seguro.

🎨 Experiencia de Usuario Premium
Diseño moderno con Swift UIKit.

Animaciones sutiles en interacciones.

Extensiones reutilizables para componentes UI.

Manejo robusto de estados y errores.

🏗 Arquitectura del Proyecto


MVC + Servicios Especializados

┌─────────────────────────────────────────┐
│           ViewControllers               │
│   • UI Logic & Navigation               │
│   • User Interaction Handling           │
└─────────────────────────────────────────┘
                   ↓
┌─────────────────────────────────────────┐
│            Services Layer               │
│   • APICaller (Generic Network Layer)   │
│   • CatService (TheCatAPI Integration)  │
│   • AuthService (Firebase Auth/DB)      │
│   • BreedFetcher (State Management)     │
└─────────────────────────────────────────┘
                   ↓
┌─────────────────────────────────────────┐
│             Models                      │
│   • Breed, Weight, BreedImage           │
│   • FetchState (Loading/Success/Error)  │
└─────────────────────────────────────────┘

Principios de Diseño Aplicados
Separación de Responsabilidades: Cada capa tiene una responsabilidad única.

Reutilización: Extensiones para UI components.

Estado Predecible: FetchState para manejo consistente.

Inyección de Dependencias: Servicios compartidos.

📁 Estructura del Proyecto

UNO/
├── 📁 Models/
│   ├── Breed.swift          # Modelo principal de raza
│   └── Weight.swift         # Modelo de peso
├── 📁 Services/
│   ├── APICaller.swift      # Capa genérica de red
│   ├── CatService.swift     # Servicio de API de gatos
│   ├── AuthService.swift    # Autenticación con Firebase
│   └── BreedFetcher.swift   # Gestor de estado de datos
├── 📁 Extensions/
│   ├── UIImageView+Ext.swift
│   ├── UILabel+Ext.swift
│   ├── UIView+Ext.swift
│   ├── UIButton+Ext.swift
│   ├── UITextField+Ext.swift
│   └── UIActivityIndicator+Ext.swift
├── 📁 Controllers/
│   ├── LoginViewController.swift
│   ├── RegisterViewController.swift
│   ├── BreedListViewController.swift
│   ├── BreedDetailViewController.swift
│   └── ProfileViewController.swift
├── 📁 Views/
│   └── BreedTableViewCell.swift
├── 📁 Resources/
│   ├── Assets.xcassets
│   └── Storyboards/XIBs
├── AppDelegate.swift
└── SceneDelegate.swift

🚀 Tecnologías y Herramientas
Tecnología	Propósito
Swift 5	Lenguaje principal de desarrollo
UIKit	Framework para interfaces
Firebase Auth	Autenticación de usuarios
Firebase Firestore	Base de datos NoSQL para perfiles
TheCatAPI	Fuente de datos de razas felinas
URLSession	Comunicación de red nativa
MVC + Services	Patrón arquitectónico
XIBs	Interfaces visuales
Cocoapods	Gestor de dependencias


🛠 Configuración del Proyecto
Requisitos Previos
macOS con Xcode 13+

iOS 13.0 o superior

Cuenta en Firebase Console

API Key de TheCatAPI

Pasos de Instalación
Clona el repositorio

git clone https://github.com/tu-usuario/cat-breeds-app.git
cd cat-breeds-app

Instala dependencias

pod install

Configura Firebase

Crea un proyecto en Firebase Console.

Agrega una app iOS.

Descarga GoogleService-Info.plist.

Colócalo en la raíz del proyecto Xcode.

Configura TheCatAPI

Obtén tu API Key en thecatapi.com.

Reemplázala en CatService.swift:

private let apiKey = "Privado"

Ejecuta la aplicación

Abre UNO.xcworkspace.

Selecciona un simulador o dispositivo.

Presiona Cmd + R.

graph TD
    A[Pantalla de Login] -->|Usuario registrado| B[Lista de Razas]
    A -->|Nuevo usuario| C[Registro]
    B -->|Selecciona raza| D[Detalle de Raza]
    B -->|Perfil| E[Perfil de Usuario]
    C --> B
    D --> B
    E -->|Cerrar sesión| A
