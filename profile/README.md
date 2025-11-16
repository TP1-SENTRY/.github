## Sentry Mobile — Weapon Detection Client (Flutter)

[![Flutter](https://img.shields.io/badge/Flutter-02569B?logo=flutter&logoColor=white)](https://flutter.dev)
[![Dart](https://img.shields.io/badge/Dart-0175C2?logo=dart&logoColor=white)](https://dart.dev)
[![Firebase](https://img.shields.io/badge/Firebase-FFCA28?logo=firebase&logoColor=black)](https://firebase.google.com)
[![Firebase Auth](https://img.shields.io/badge/Firebase_Auth-FFCA28?logo=firebase&logoColor=black)](https://firebase.google.com/docs/auth)
[![go_router](https://img.shields.io/badge/go__router-4A148C?logo=flutter&logoColor=white)](https://pub.dev/packages/go_router)
[![Lottie](https://img.shields.io/badge/Lottie-00D1B2?logo=lottie&logoColor=white)](https://pub.dev/packages/lottie)
[![Google Fonts](https://img.shields.io/badge/Google%20Fonts-4285F4?logo=google&logoColor=white)](https://pub.dev/packages/google_fonts)

Aplicación móvil de Sentry para onboarding, autenticación y selección de rol, integrada con Firebase y construida con Flutter.

### Características
- Onboarding animado (Lottie) y branding consistente.
- Autenticación lista para integrar (Firebase).
- Selección de rol con navegación a `AdminDashboard` y `SecurityDashboard`.
- Tema oscuro y tipografía Raleway.
- Assets organizados (íconos, imágenes, animaciones).

### Tech stack
- Flutter + Dart
- Routing: `go_router`
- Firebase: `firebase_core`, `firebase_auth`
- UI: `lottie`, `google_fonts`, `flutter_svg` (si aplica)

### Estructura
- `lib/main.dart`: inicialización de Firebase y rutas.
- `lib/screens/`: `loading`, `service1`, `service2`, `login`, `signup`, `roles`, `admin_dashboard`, `security_dashboard`.
- `lib/theme/theme.dart`, `lib/utils/constants.dart`, `lib/widgets/custom_text_field.dart`.
- `lib/firebase_options.dart` (FlutterFire).

### Rutas
- `/loading` → `/service1` → `/service2` → `/login`
- `/signup`
- `/roles`
- `/adminDashboard`
- `/securityDashboard`

### Requisitos
- Flutter (stable) y Dart (ver `pubspec.yaml`, `sdk: ^3.9.2`)
- Proyecto Firebase configurado (Android/iOS/macOS)

### Quick start
```bash
flutter pub get
# si falta firebase_options.dart
flutterfire configure
flutter run -d android   # o -d ios
```

### Firebase
`main.dart` ya inicializa Firebase:
```dart
WidgetsFlutterBinding.ensureInitialized();
await Firebase.initializeApp(
  options: DefaultFirebaseOptions.currentPlatform,
);
```

### Autenticación
- Botones de Google/Microsoft en `Login` y `SignUp`.
- Sugerido: implementar `AuthService` con `firebase_auth` + `google_sign_in`.
- Microsoft (MSAL) opcional.

### Notificaciones (opcional, alineado con backend)
Suscripción a tópico `alerts` usando `firebase_messaging`:
```dart
final FirebaseMessaging messaging = FirebaseMessaging.instance;
await messaging.requestPermission();
await messaging.subscribeToTopic('alerts');
FirebaseMessaging.onMessage.listen((RemoteMessage message) {
  // Manejar notificación en foreground
});
```

### Roadmap
- Auth real (Google/Microsoft) y logout.
- Protección de rutas según sesión/rol.
- Suscripción FCM + UI de notificaciones.
- Manejo de errores con `SnackBar`/`Dialog`.

### Convenciones
- Commits: `feat:`, `fix:`, `chore:`, `docs:`, `refactor:`
- Ramas: `feature/<nombre>`, `fix/<nombre>`
- PRs con título/descr. claros; checklist y screenshots si aplica.

### Autores y organización
- Autores: **Julio Elsner** y **FourFive 4-5 Alarcón**
- Asesor especializado: **Elio Navarrete**
- Organización: **Universidad Peruana de Ciencias Aplicadas (UPC)**

### Licencia
Definir según lineamientos de la organización (MIT/Apache 2.0, etc.).
