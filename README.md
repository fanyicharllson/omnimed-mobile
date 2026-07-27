# OmniMed AI - Mobile Client Application 📱

The client-facing mobile application for OmniMed AI, built with Flutter. This application provides patient and clinician interfaces, manages local caching, handles hardware camera features, and streams high-resolution clinical imaging directly to backend microservices using native gRPC channels over HTTP/2.

## ✨ Key Features & User Experience (UX)

The mobile app enforces structural boundaries on data collection to ensure high AI diagnostic reliability:

* **Skin Diagnostic Pipeline:** Guides the user to take a stabilized, macro photo of a single skin lesion.
* **Oral Diagnostic Pipeline:** Automatically enforces the camera hardware flash to illuminate the oral cavity when scanning for tongue or inner-cheek sores.
* **Breast Diagnostic Pipeline (Scan Diagnostic):** Restricts the camera viewport to a flat bounding box, forcing the user to snap a perfectly aligned, non-skewed picture of a printed lab **Breast Ultrasound sheet** or upload a digital file.

## 🛠️ Mobile Tech Stack

* **Frontend Engine:** Flutter (Dart SDK 3.x)
* **Network Protocol:** `grpc-dart` (Native HTTP/2 streaming pipeline instead of REST)
* **State Management:** BLoC / Riverpod (Clean architecture separation)
* **Local Storage:** Hive / Isar (Fast, encrypted offline caching for patient medical profiles)

## 📁 Core Directory Structure

```text
lib/
├── core/
│   ├── network/      # gRPC client initialization & HTTP/2 channels
│   └── theme/        # Enterprise clinical UI/UX design tokens
├── features/
│   ├── auth/         # JWT-based login, signup, and clinician role validation
│   ├── diagnostics/  # Custom camera viewports for Skin, Oral, and Ultrasound inputs
│   └── medical_logs/ # History reports and exportable PDF generation
└── generated/        # Auto-generated gRPC Dart protobuf stubs
```

## 🏗️ Getting Started

### 1. Fetch Dependencies & Stubs
Ensure you have the Flutter SDK installed on your system. Run:
```bash
flutter pub get
```

### 2. Point App to the Backend Environment
For local network debugging (e.g., testing in hospital clinics via local network hotspots or Ngrok tunnels), update your environment variables configuration:
```dart
// lib/core/network/config.dart
const String backendHost = "192.168.1.50"; // Laptop Local IP or Ngrok TCP address
const int backendPort = 50051;
```

---
*Developed as a Final Year Project at The ICT University.*
