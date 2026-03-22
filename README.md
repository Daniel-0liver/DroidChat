# DroidChat 💬

> **⚠️ This project is currently under active development.**

DroidChat is an Android real-time chat application built with modern Android development best practices and technologies.

---

## 🚀 Tech Stack

| Layer | Technology |
|---|---|
| UI | [Jetpack Compose](https://developer.android.com/jetpack/compose) |
| Dependency Injection | [Dagger Hilt](https://dagger.dev/hilt/) |
| Network (REST) | [Ktor Client](https://ktor.io/docs/client-create-new-application.html) |
| Real-time messaging | [WebSocket (Ktor)](https://ktor.io/docs/client-websockets.html) |
| Architecture | Repository Pattern |
| Async | [Kotlin Coroutines](https://kotlinlang.org/docs/coroutines-overview.html) |
| Serialization | [Kotlinx Serialization](https://kotlinlang.org/docs/serialization.html) |
| Image loading | [Coil](https://coil-kt.github.io/coil/) |
| Navigation | [Navigation Compose](https://developer.android.com/jetpack/compose/navigation) |
| Local storage | [DataStore](https://developer.android.com/topic/libraries/architecture/datastore) |
| Push notifications | [Firebase Cloud Messaging](https://firebase.google.com/docs/cloud-messaging) |
| Authentication | JWT |
| Splash Screen | [SplashScreen API](https://developer.android.com/develop/ui/views/launch/splash-screen) |

---

## 🏗️ Architecture Overview

DroidChat follows the **Repository Pattern**, keeping a clean separation between data sources and the rest of the app:

```
UI (Jetpack Compose)
        │
   ViewModel
        │
   Repository
     /     \
Remote     Local
(Ktor)  (DataStore)
```

- **UI layer** – Built entirely with Jetpack Compose, providing a declarative and reactive interface.
- **ViewModel layer** – Holds UI state and exposes data streams to the composables.
- **Repository layer** – Single source of truth that coordinates between remote (Ktor REST + WebSocket) and local (DataStore) data sources.
- **Dependency Injection** – Dagger Hilt wires all layers together, simplifying testability and lifecycle management.

---

## 📡 Networking

- **REST requests** are handled by the [Ktor HTTP client](https://ktor.io/docs/client-create-new-application.html) with the CIO engine, supporting content negotiation via Kotlinx Serialization and JWT-based authentication.
- **Real-time chat** is powered by **WebSockets** through the Ktor WebSocket plugin, enabling full-duplex communication with the backend.

---

## 📋 Requirements

- Android Studio Hedgehog or later
- Android SDK 26+ (minSdk 26)
- Kotlin 2.0+
- A running backend server that exposes REST and WebSocket endpoints

---

## 🛠️ Getting Started

1. **Clone the repository**
   ```bash
   git clone https://github.com/Daniel-0liver/DroidChat.git
   cd DroidChat
   ```

2. **Open in Android Studio**
   Open the project folder in Android Studio and let Gradle sync finish.

3. **Configure the backend URL**
   Update the base URL in the network configuration to point to your backend server.

4. **Run the app**
   Select a device or emulator and click **Run ▶**.

---

## 📦 Module Structure

```
app/
├── data/
│   ├── remote/        # Ktor HTTP client, API services, WebSocket
│   ├── local/         # DataStore preferences
│   └── repository/    # Repository implementations
├── di/                # Hilt modules
├── domain/
│   ├── model/         # Domain models
│   └── repository/    # Repository interfaces
└── ui/
    ├── screens/       # Composable screens
    ├── components/    # Reusable UI components
    ├── navigation/    # Navigation graph
    └── theme/         # App theme (colors, typography, shapes)
```

---

## 🤝 Contributing

Contributions are welcome! Feel free to open an issue or submit a pull request.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
