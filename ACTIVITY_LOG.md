# Activity Log - Smart Farm IoT Platform

This log tracks all significant changes and development milestones.

## [2025-12-29] - Repository Separation & Multi-platform Setup

### Added
- **smartfarm-docs**: Created a dedicated documentation repository using MkDocs with Material theme.
  - Migrated hardware guides (ESP32, STM32, Power, Water, AI) to standard Markdown.
  - Added GitHub Actions for automatic deployment to GitHub Pages.
- **smartfarm-iot-library**: Established a separate Arduino library repository.
  - Organized source code into `src/` and examples into `examples/`.
  - **Hybrid Failover**: Implemented Secondary MQTT Broker support (`allowHybrid`) to ensure reliability when the cloud is offline.
  - **Reference Examples**: Created 3 standardized examples (`BasicEnvironment`, `SmartIrrigation`, `OffGridPower`) demonstrating modular sensor usage and hybrid connectivity.
  - Added README and proprietary license agreement.
- **Mobile App Strategy (Dual-track)**:
  - **smartfarm-mobile-basic**: Initialized with **React Native (Expo)** for efficiency and speed.
  - **smartfarm-mobile-premium**: Dedicated to **Flutter** for advanced UI/UX and animations (Paid users).
- **Smart Home & Urban Farming**: 
  - Created a dedicated page for indoor gardening automation.
  - Integrated smart home climate and energy monitoring concepts.
- **Documentation CI/CD Flow**:
  - Documented the GitHub Actions to GitHub Pages deployment pipeline using Mermaid diagrams.
  - Provided a guide for setting up repository permissions for automatic publishing.
- **Premium Dashboard UI Overhaul**:
  - Implemented a professional Dashboard Shell with Sidebar and Topbar navigation.
  - Integrated **Recharts** for real-time environmental data visualization.
  - Added "Activity & Alerts" system to track local automation events.
- **Marketplace & Monetization**:
  - Implemented a **Multi-Theme System** (CSS Variable based) for selling templates.
  - Created the **Marketplace Page** for selling Premium Extensions and Themes.
  - Developed a mock **Installation Engine** for addons and extensions.
- **Localization & Accessibility**:
  - Added **Bilingual Support (Thai/English)** to the Dashboard UI.
  - Created a comprehensive **User Manual** in both languages within MkDocs.
  - Standardized the use of **Universal Icons** for better accessibility for non-technical users.
- **Repository Code Separation**:
  - Reorganized the workspace into 5 distinct repositories: `smartfarm-platform`, `smartfarm-iot-library`, `smartfarm-mobile-basic`, `smartfarm-mobile-premium`, and `smartfarm-docs`.
  - Moved hardware examples to `smartfarm-iot-library/examples`.
  - Initialized basic structure and "Hello World" examples for both Expo (Basic) and Flutter (Premium) mobile apps.
- **Local Infrastructure Documentation**:
  - Created a detailed **Edge Hub Installation Guide** for Raspberry Pi and PC.
  - Provided **Docker Compose** configurations for rapid deployment of local MQTT and Logic Engine.
  - Documented manual installation steps for Node.js and Mosquitto environments.
- **Admin & Automation**:
  - Created an **Admin Manual** with technical references, MQTT topic structures, and port definitions.
  - Developed a **One-Click Installer Script (`setup-edge-hub.sh`)** for Linux/Raspberry Pi.
  - Implemented automated dependency checking and Docker configuration within the setup script.
  - Defined a **Backup and Disaster Recovery Strategy** for Edge Hub deployments to ensure business continuity.
  - Created a **Themes & Extensions Guide** for marketplace developers to expand the ecosystem.
  - Updated the **Supabase Database Schema** with new tables for Marketplace Items and User Installations.
  - Documented the **Marketplace Import Procedure** for system administrators.
- **Marketplace Content Demo**:
  - Created the **Midnight OLED Theme** as a template for high-contrast dashboard designs.
  - Developed the **AI Crop Health Extension** featuring Edge-AI simulation and dynamic scanning animations.
  - Integrated the new content into the **Marketplace Page** and **Live Dashboard** for demonstration.
- **Mobile Application Development**:
  - Defined the **Two-Tier Mobile Strategy** (Basic vs Premium) in the documentation.
  - Initialized **Smart Farm Basic** (React Native/Expo) with a clean, functional dashboard layout.
  - Initialized **Smart Farm Premium** (Flutter) with high-end visuals and AI insights placeholder.
  - Implemented **MQTT Services** for both platforms to handle real-time sensor data.
  - Developed **Device Management Screens** (Add/List/Remove) to allow users to provision hardware from their phones.
  - Integrated **Supabase Services** into mobile apps for persistent data sync and authentication.

### Changed
- **PROJECT_STRUCTURE.md**: Updated the entire system architecture documentation to reflect the 4-repository structure and the switch to Flutter for mobile.
- **task.md**: Updated task tracking to include new infrastructure milestones.

### System Maintenance
- **JDK Installation**: Initiated installation of Microsoft OpenJDK 17 via `winget` to support Flutter development.

---
*End of Session Log*
