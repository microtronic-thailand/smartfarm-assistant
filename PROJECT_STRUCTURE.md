# Smart Farm Platform - Project Structure

## Overview

Smart Farm Platform consists of **4 separate repositories** for clear separation of concerns and team collaboration.

---

## Repository Structure

```
SmartFarm/
├── smartfarm-platform/          # Main platform (Next.js)
├── smartfarm-iot-library/       # Arduino library (Core Engine)
├── smartfarm-hw-env-monitor/    # Environment Monitoring Firmware
├── smartfarm-hw-irrigation/     # Smart Irrigation Firmware
├── smartfarm-hw-power/          # Off-Grid Power Firmware
├── smartfarm-mobile-basic/      # Basic mobile app (React Native/Expo)
├── smartfarm-mobile-premium/    # Premium mobile app (Flutter)
└── smartfarm-docs/              # Documentation site (MkDocs)
```

---

## 1. smartfarm-platform (Main Platform)

**Repository:** `https://github.com/GridsMicro/smartfarm-platform`

### Purpose
- Web dashboard
- Backend API
- Database management
- User authentication
- Device management
- Smart Home & Urban Farming integration

### Tech Stack
- **Frontend:** Next.js 15 + Tailwind CSS v4
- **Backend:** Next.js API Routes
- **Database:** Supabase (PostgreSQL)
- **Real-time:** Supabase Realtime
- **MQTT:** EMQX Bridge

### Team Roles
- **Frontend Developers:** Dashboard UI/UX
- **Backend Developers:** API, Database, MQTT integration
- **DevOps:** Deployment, monitoring

### Directory Structure
```
smartfarm-platform/
├── app/
│   ├── (auth)/              # Authentication pages
│   ├── dashboard/           # Dashboard pages
│   ├── docs/                # Documentation
│   ├── api/                 # API routes
│   └── page.tsx             # Homepage
├── components/
│   ├── layout/              # Layout components
│   ├── ui/                  # UI components
│   └── dashboard/           # Dashboard-specific components
├── lib/
│   ├── supabase.ts          # Supabase client
│   ├── mqtt.ts              # MQTT client
│   └── utils.ts             # Utilities
├── types/
│   └── telemetry.ts         # TypeScript types
└── design_docs/
    ├── PROTOCOL.md          # Communication protocol
    ├── ARCHITECTURE.md      # System architecture
    └── API.md               # API documentation
```

### Environment Variables
```env
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
SUPABASE_SERVICE_ROLE_KEY=
MQTT_BROKER_URL=
```

---

## 2. smartfarm-iot-library (Hardware Library)

**Repository:** `https://github.com/GridsMicro/smartfarm-iot-library`

### Purpose
- Arduino library for ESP32/ESP8266/STM32
- Sensor integration
- MQTT communication
- Protocol implementation

### Tech Stack
- **Language:** C++ (Arduino)
- **Dependencies:** PubSubClient, ArduinoJson, DHT

### Team Roles
- **Embedded Developers:** Core library development
- **Hardware Engineers:** Sensor integration
- **QA:** Testing on different boards

### Directory Structure
```
smartfarm-iot-library/
├── src/
│   ├── SmartFarmIoT.h           # Main library header
│   ├── SmartFarmIoT.cpp         # Main library implementation
│   ├── SmartFarmSensors.h       # Sensor library header
│   └── SmartFarmSensors.cpp     # Sensor library implementation
├── examples/
│   ├── BasicNode/               # Basic example
│   ├── CompleteFarmNode/        # Complete example
├── library.properties           # Arduino library metadata
├── README.md                    # Library documentation
└── LICENSE.md                   # Proprietary license
```

### Versioning
- **Major.Minor.Patch** (e.g., 1.0.0)
- Semantic versioning
- Changelog maintained

---

## 3. Hardware Module Repositories

Each hardware module has its own dedicated repository for versioning and deployment flexibility.

### 3.1 smartfarm-hw-env-monitor
**Purpose:** Firmware for temperature, humidity, and light monitoring.
- **Microcontroller:** ESP32 / ESP8266
- **Sensors:** DHT22, BH1750

### 3.2 smartfarm-hw-irrigation
**Purpose:** Automated watering system with soil moisture feedback.
- **Logic:** Local autonomous control + Cloud override
- **Sensors:** Soil Moisture, Water Flow

### 3.3 smartfarm-hw-power
**Purpose:** Off-grid energy management for remote farms.
- **Monitoring:** Solar panel voltage, Battery SOC, Load current
- **Alerts:** Low battery notification via MQTT

### 4. Mobile Applications

### 4.1 smartfarm-mobile-basic (General Users)
**Tech Stack:** React Native + Expo
**Purpose:** Core features, basic monitoring, and device control for free/general users.

**Directory Structure:**
```
smartfarm-mobile-basic/
├── src/
│   ├── components/
│   ├── screens/
│   ├── services/
│   └── store/
├── assets/
├── App.js
└── package.json
```

### 4.2 smartfarm-mobile-premium (Paid Users)
**Tech Stack:** Flutter
**Purpose:** Advanced visualizations, AI-driven insights, premium UI/UX, and complex animations for paid subscribers.

**Directory Structure:**
```
smartfarm-mobile-premium/
├── lib/
│   ├── main.dart
│   ├── screens/
│   ├── models/
│   └── services/
├── assets/
├── pubspec.yaml
└── README.md
```

---

## 5. smartfarm-docs (Documentation)

**Repository:** `https://github.com/GridsMicro/smartfarm-docs`

### Purpose
- Public documentation
- API reference
- Tutorials
- Hardware guides

### Tech Stack
- **Framework:** MkDocs + Material for MkDocs
- **Hosting:** GitHub Pages
- **Deployment:** GitHub Actions

### Team Roles
- **Technical Writers:** Documentation
- **Developers:** API docs, code examples

### Directory Structure
```
smartfarm-docs/
├── docs/
│   ├── hardware/           # Hardware specific guides
│   ├── api/                # API reference
│   ├── library/            # Arduino library docs
│   ├── index.md            # Home page
│   └── introduction.md     # Getting started
├── mkdocs.yml              # MkDocs configuration
└── .github/workflows/      # Deployment workflow
```

---

## Development Workflow

### 1. Feature Development

**Platform (smartfarm-platform):**
```bash
git checkout -b feature/dashboard-charts
# Develop feature
git commit -m "feat: add real-time charts to dashboard"
git push origin feature/dashboard-charts
# Create PR → Review → Merge
```

**Library (smartfarm-iot-library):**
```bash
git checkout -b feature/bh1750-sensor
# Add sensor support
git commit -m "feat: add BH1750 light sensor support"
# Update version in library.properties
git tag v1.1.0
git push origin v1.1.0
```

### 2. Release Process

**Platform:**
- Continuous deployment via Vercel
- Automatic on merge to `main`

**Library:**
- Tag release: `git tag v1.x.x`
- Publish to Arduino Library Manager
- Update documentation

**Mobile:**
- Build via Expo EAS
- Submit to App Store / Play Store

---

## Team Collaboration

### Roles & Responsibilities

| Role | Platform | Library | Mobile | Docs |
|------|----------|---------|--------|------|
| **Frontend Dev** | ✅ | ❌ | ❌ | ❌ |
| **Backend Dev** | ✅ | ❌ | ❌ | ❌ |
| **Embedded Dev** | ❌ | ✅ | ❌ | ✅ |
| **Mobile Dev** | ❌ | ❌ | ✅ | ❌ |
| **DevOps** | ✅ | ✅ | ✅ | ✅ |
| **Tech Writer** | ❌ | ✅ | ❌ | ✅ |

### Communication

- **Platform Issues:** GitHub Issues in `smartfarm-platform`
- **Library Issues:** GitHub Issues in `smartfarm-iot-library`
- **General Discussion:** GitHub Discussions
- **Team Chat:** Slack / Discord

---

## Version Compatibility

### Platform ↔ Library

| Platform Version | Library Version | Compatible |
|------------------|-----------------|------------|
| v1.0.x | v1.0.x | ✅ |
| v1.0.x | v1.1.x | ✅ |
| v1.0.x | v2.0.x | ❌ |
| v2.0.x | v2.0.x | ✅ |

**Rule:** Major version must match, minor versions are backward compatible.

---

## CI/CD Pipeline

### Platform (smartfarm-platform)
```yaml
# .github/workflows/deploy.yml
on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: npm install
      - run: npm run build
      - run: npm run test
      - uses: vercel/deploy@v1
```

### Library (smartfarm-iot-library)
```yaml
# .github/workflows/test.yml
on:
  push:
    branches: [main]
  pull_request:

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: arduino/setup-arduino-cli@v1
      - run: arduino-cli lib install PubSubClient ArduinoJson DHT
      - run: arduino-cli compile --fqbn esp32:esp32:esp32 examples/BasicNode
```

---

## Getting Started for Developers

### Clone All Repositories

```bash
mkdir SmartFarm
cd SmartFarm

# Clone platform
git clone https://github.com/GridsMicro/smartfarm-platform.git

# Clone library
git clone https://github.com/GridsMicro/smartfarm-iot-library.git

# Clone mobile (optional)
git clone https://github.com/GridsMicro/smartfarm-mobile.git

# Clone docs (optional)
git clone https://github.com/GridsMicro/smartfarm-docs.git
```

### Setup Development Environment

**Platform:**
```bash
cd smartfarm-platform
npm install
cp .env.local.example .env.local
# Edit .env.local with your credentials
npm run dev
```

**Library:**
```bash
cd smartfarm-iot-library
# Copy to Arduino libraries folder
cp -r . ~/Arduino/libraries/SmartFarmIoT/
# Open Arduino IDE and test examples
```

---

## Repository Access Control

### Public Repositories
- ✅ `smartfarm-docs` - Public documentation
- ✅ `smartfarm-iot-library` - Public library (but proprietary license)

### Private Repositories
- 🔒 `smartfarm-platform` - Private (core business logic)
- 🔒 `smartfarm-mobile` - Private

---

## Summary

**Benefits of Separation:**
1. ✅ **Clear Ownership** - Each team owns their repo
2. ✅ **Independent Development** - No conflicts
3. ✅ **Easier Onboarding** - New devs focus on one repo
4. ✅ **Better CI/CD** - Separate pipelines
5. ✅ **Scalability** - Can scale teams independently

**Next Steps:**
1. Create separate GitHub repositories
2. Move library code to `smartfarm-iot-library`
3. Setup CI/CD for each repo
4. Document inter-repo dependencies

---

**Last Updated:** 2025-12-29  
**Maintained by:** Smart Farm Platform Team
