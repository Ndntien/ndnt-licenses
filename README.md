# NullR-GPS

### Beyond Coordinates. Toward System-Level Location Simulation.

**An advanced Android location-simulation platform built around route
dynamics, Android location APIs, GNSS interfaces, sensor data, and
modular Xposed integration.**

[![Android](https://img.shields.io/badge/Android-10%2B-3DDC84?logo=android&logoColor=white)](#requirements)
[![Kotlin](https://img.shields.io/badge/Kotlin-2.2.10-7F52FF?logo=kotlin&logoColor=white)](#technology-stack)
[![Xposed
API](https://img.shields.io/badge/libxposed-API%20101-blue)](#requirements)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

![NullR-GPS location simulation artwork](images/xposedfakelocation.webp)

------------------------------------------------------------------------

## Overview

NullR-GPS is an Android location-simulation project designed for
controlled testing, application development, and experimentation with
location-dependent Android behavior.

It combines a map-based location controller with an Xposed module and a
collection of optional system-integration hooks. The project goes beyond
setting a latitude and longitude: its architecture provides configurable
simulation across several related Android interfaces, including location
providers, Google Play Services location APIs, GNSS callbacks, NMEA
messages, motion sensors, Wi-Fi information, and telephony-related data.

The project also includes route planning and playback, route recording
and import, joystick-based movement, a time-based virtual travel
itinerary, external control, and a separate administration companion.

> **Core idea:** simulate a coherent location scenario---not just a
> single coordinate.

NullR-GPS is intended for legitimate development, QA, compatibility
testing, and controlled research on devices and applications that you
own or are authorized to test. It does not provide real satellite
signals and does not guarantee compatibility with every application,
Android build, device, or detection mechanism.

## Highlights

-   **Map-based location control** with coordinate entry, place search,
    draggable map marker, and saved favorites.
-   **Configurable location data** including accuracy, altitude, speed,
    bearing-related movement, and optional randomized position
    variation.
-   **Route simulation** with road-based routing, adjustable speed,
    pause/resume, loop mode, simulated stops, and corner-aware speed
    changes.
-   **Route recording and route-library management**, including import
    from GPX and supported JSON/GeoJSON structures.
-   **Joystick movement** with adjustable speed and quick waypoint
    generation.
-   **Virtual Travel Day**, a time-based itinerary simulator with
    places, stays, transfers, breaks, and playback.
-   **Super Pro** with 30 optional configuration switches grouped into
    six technical areas.
-   **Xposed integration** for selected application processes, with
    optional system and telephony process hooks.
## Feature Tour

### 1. Map and Location Controller

The main application provides an interactive map for choosing and
managing the simulated location.

Available controls include:

-   Select a location by tapping the map.
-   Drag the marker to refine the selected coordinate.
-   Search for a place by name.
-   Enter latitude and longitude directly.
-   Return the map to the device's current location.
-   View and edit location-related values.
-   Save frequently used places to Favorites.
-   Start or stop location simulation.

Place search currently uses **Nominatim** with **Photon** as a fallback.
Map tiles can be displayed using OpenStreetMap, Carto styles, and Mapbox
styles. Mapbox styles require a valid access token.

#### Location parameters

The location model and settings support configurable values such as:

-   Latitude and longitude.
-   Horizontal accuracy.
-   Altitude.
-   Mean-sea-level altitude and related accuracy fields where supported
    by the active path.
-   Speed and speed accuracy.
-   Optional position variation.

The values exposed by a particular Android API can vary by Android
version and by the target application's implementation.

### 2. Route Planning and Simulation

The route engine turns a list of waypoints into a continuous simulated
journey.

#### Route creation

-   Add route points on the map.
-   Reposition or remove waypoints.
-   Request a road route through a routing provider.
-   Display the route geometry on the map.
-   Save a route for later use.

The project contains route-provider implementations for:

-   **OSRM** --- the configured public demo endpoint can be used without
    an API token; it is a shared best-effort service.
-   **Mapbox Directions** --- requires a Mapbox access token.

Routing availability, coverage, response time, and usage limits depend
on the selected provider and its service terms.

#### Route playback

The route simulation engine supports:

-   Adjustable travel speed (5--120 km/h in the route panel).
-   Pause and resume.
-   Loop playback.
-   Optional simulated red-light stops.
-   Optional smooth-driving behavior with speed reduction around turns.
-   Live adjustment of supported simulation settings while a route is
    running.
-   Foreground-service operation with an ongoing notification.

The route engine calculates position along a polyline using travelled
distance and elapsed time. It is separate from the Virtual Travel Day
itinerary engine.

### 3. Route Recording and Route Library

The application includes a route-recording service and a saved-route
library.

Users can:

-   Start and stop route recording.
-   Save a recorded route.
-   Browse saved routes.
-   Load a saved route back into the map workflow.
-   Delete routes that are no longer needed.
-   Import route data from supported files.

The importer recognizes:

-   **GPX** tracks and routes, with waypoint fallback when no track or
    route is present.
-   **GeoJSON** `FeatureCollection`, `Feature`, `LineString`, and
    `MultiLineString` geometries.
-   JSON coordinate arrays and route structures.
-   A supported `recordings` JSON structure containing metadata and
    coordinate samples.

Imported points are normalized and deduplicated before a valid route is
stored. Import support is format-specific; it is not a promise that
every vendor-specific GPX or JSON extension will be understood.

### 4. Joystick and Quick Route Points

The map can display an on-screen joystick for manual movement.

-   Enable or disable the joystick.
-   Adjust its movement speed from 1 to 200 km/h.
-   Move the simulated position interactively.
-   Save joystick preferences.

The map also includes a three-finger gesture for opening the Quick Route
Points configuration. The configuration supports a selectable waypoint
count and generation radius, allowing a group of route points to be
created without adding each point individually.

### 5. Virtual Travel Day

Virtual Travel Day is a separate itinerary-based simulation engine.
Instead of following one road polyline, it builds a day plan containing
destinations, arrival and departure times, stays, transfers, and
periodic position samples.

The itinerary model includes place categories such as hotel,
sightseeing, meal, coffee, viewpoint, rest, and transfer.

Configurable itinerary behavior includes:

-   Start time.
-   Hotel-first and return-to-hotel options.
-   Hotel rest duration.
-   Lunch and dinner times and durations.
-   Sightseeing limit.
-   Coffee and viewpoint breaks.
-   Optional photo-stop behavior.
-   Walking pace.
-   Position sampling interval.
-   Playback speed.
-   Small position variation while stationary.
-   Transfer-time variation.

The travel model includes walking, slow walking, bus, taxi, and train
movement profiles. User-entered place names can be resolved through
Android's Geocoder when available; coordinates can also be supplied
directly.

Virtual Travel Day runs through its own foreground service and is
independent of the road-route simulation feature.

### 6. Favorites

Favorites provides a reusable list of saved places.

Each favorite stores a name and coordinates. Users can add, select,
edit, and delete saved locations, then return a selected favorite to the
map.

### 7. Target Apps and Xposed Scope

The Xposed module is designed to apply its application-level hooks to
selected target processes.

The manager includes a target-app screen for browsing installed
applications, searching the list, and choosing which applications should
be in scope.

The module entry point also contains dedicated initialization paths for:

-   Regular target application processes.
-   Google Play Services when included in the active scope.
-   `com.android.phone` for telephony-related hooks.
-   `system_server` when system hooks are explicitly enabled.

The actual set of active hooks depends on the selected scope, saved
preferences, Android version, process availability, and the enabled
Super Pro options.

### 8. Super Pro: 30 Advanced Switches

Super Pro organizes 30 optional switches into six groups. These options
are intended for controlled compatibility tests and advanced simulation
experiments. They are not all enabled by default, and some require
device-specific validation.
The catalog also defines presets and quick-mode configurations. The
effect of each switch depends on its implementation path and the Android
APIs available on the test device. Some GNSS, sensor, telephony, and
system-level behaviors are explicitly experimental or
hardware-dependent.

**Important:** Super Pro is a collection of optional framework-level
simulation hooks, not a guarantee that every Android application
consumes or displays the simulated data in the same way.

### 9. External Control

The application contains an optional broadcast-based control interface
for automation and integration with other tools.

The receiver is **disabled by default** and must be explicitly enabled
from the application's External Control settings. Each accepted command
must include the configured control key.

The control key is generated locally on first use and can be changed by
the user. Do not publish or share this key. `START` and automatic start
behavior are subject to the application's license state.

## Requirements

### Main NullR-GPS app

The current Gradle configuration specifies:

-   Android **10 (API 29) or newer**.
-   Rooted Android device.
-   An Xposed environment that supports **libxposed API 101**.
-   Android SDK Platform **36** for building.
-   Android NDK **27.2.12479018**.
-   CMake **3.22.1**.
-   Java/JDK **21**.
-   ARM native build targets: `arm64-v8a` and `armeabi-v7a`.

The module uses non-static scope metadata. Configure the target
applications in the Xposed manager and enable system or telephony
process scope only when required for a test scenario.

Some features additionally depend on Google Play Services, SIM/network
state, Wi-Fi permissions, sensor availability, Android API level, and
device-vendor behavior.
## Installation and Setup
NullR-GPS is an Xposed-based project, not a standalone no-root
mock-location application.

A typical test-device setup is:

1.  Install the NullR-GPS APK.
2.  Install or configure a compatible Xposed framework that implements
    the required libxposed API.
3.  Enable the NullR-GPS module in the framework manager.
4.  Select the intended target applications.
5.  Reboot or restart affected processes as required by the framework.
6.  Open NullR-GPS and grant the Android permissions requested by the
    app.
7.  Select a test location and start the simulation.
8.  Enable optional Super Pro or system-level features only when the
    test scenario requires them.

Exact framework installation and activation steps vary by device and
Android build. Back up the test device before changing system-level
module scope.

## Build from Source

### Toolchain

-   Android Studio with Android Gradle Plugin 8.10.1.
-   JDK 21.
-   Android SDK Platform 36.
-   Android NDK 27.2.12479018.
-   CMake 3.22.1.
## Localization and Appearance

The language selector contains 14 language choices plus the
system-default option:

-   English
-   Chinese
-   German
-   Russian
-   English (Singapore)
-   Malay
-   Indonesian
-   Thai
-   Vietnamese
-   Filipino
-   Khmer
-   Burmese
-   Lao
-   Japanese

Available appearance options include system default, light, dark, OLED,
Glass 50%, Glass 70%, Glass 80%, and Rainbow.

## Testing and Project Status

The repository contains unit tests for selected components, including:

-   Route simulation behavior.
-   Wi-Fi identity hook policy.
-   Trial-form validation.
-   Name-cipher behavior.

These tests cover selected logic; they do not constitute full end-to-end
validation of every Xposed hook or every supported Android device.

Some entries in the in-app Lab catalog are marked as development or
upcoming work. They should not be interpreted as completed,
production-ready features. In particular, experimental GNSS
measurements, satellite behavior, and hardware-dependent sensor or
system hooks require separate validation on the target device.

## Privacy, Security, and Responsible Use

-   Use the software only on devices and applications you own or are
    authorized to test.
-   Review the permissions and process scope before enabling a module.
-   Keep the external-control key private.
-   Keep license-signing keys, keystores, backend credentials, API
    tokens, and local configuration files out of public repositories.
-   Review all third-party map, routing, geocoding, and backend service
    terms before deployment.
-   Do not assume simulated Android API values represent actual GNSS,
    cellular, Wi-Fi, or hardware measurements.
-   Do not use this project to misrepresent physical presence, falsify
    records, violate service terms, or interfere with third-party
    systems.

NullR-GPS is provided as a development and testing tool. It does not
guarantee that a simulated scenario will be accepted by any third-party
application or service.

## License

This repository includes an MIT License. See [LICENSE](LICENSE) for the
full license text.

Third-party libraries and external services remain subject to their
respective licenses and terms.

------------------------------------------------------------------------

**NullR-GPS --- Beyond Coordinates.**

*One configurable environment for exploring Android location behavior.*

<div align="center">

# NullR-GPS
[**⬇ Download**](https://github.com/Ndntien/ndnt-licenses/releases/latest) · [issye](https://github.com/Ndntien/NT-GPS/issues/new/choose)</div>
##
- license / supporrt: **XXXXX nullrenew@gmail.com**
- [Issue](https://github.com/Ndntien/NT-GPS/issues/new/choose)
(THIRD_PARTY_NOTICES.md).
