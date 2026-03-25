# Smart India Hackathon Workshop
# Date:25.03.2025
## Register Number:212223040039
## Name:Dhayananth.P.S
## Problem Title
SIH 1710: Enhancing Navigation for Railway Station Facilities and Locations
## Problem Description
Background: Railway stations are complex environments with numerous facilities and locations such as ticket counters, platforms, restrooms, food courts, and waiting areas. Passengers often face difficulties in navigating these spaces, especially in large or unfamiliar stations. Efficient and user-friendly navigation systems are crucial for improving passenger experience, reducing congestion, and ensuring timely travel connections. Description: The problem involves developing a comprehensive navigation solution for railway stations that assists passengers in locating various facilities and destinations within the station premises. This includes creating detailed maps, providing real-time directions, and integrating features such as accessibility options for individuals with disabilities. The solution should be intuitive, easy to use, and accessible via multiple platforms, including mobile devices and digital kiosks. Key challenges include updating navigation information in real-time, ensuring accuracy, and accommodating the diverse needs of all passengers. Expected Solution: The expected solution is a multi-platform navigation system that provides detailed, real-time directions to all facilities and locations within a railway station. This system should include: A mobile application with 3D interactive maps and step-by-step navigation. Digital kiosks located throughout the station with touch-screen interfaces. Voice-guided navigation for visually impaired passengers. Regular updates to reflect changes in station layout and facility locations. Integration with existing railway apps and services for seamless user experience. The solution should enhance the overall passenger experience by reducing confusion, saving time, and improving accessibility within the station.

## Problem Creater's Organization
Ministry of Railway

## Idea
"RailNav: An AR-Powered Indoor Positioning System (IPS)"

Traditional GPS fails indoors, making railway station navigation difficult. Our idea is to build RailNav, an integrated platform relying on an Indoor Positioning System (IPS) using a combination of Bluetooth Low Energy (BLE) beacons, Wi-Fi fingerprinting, and smartphone pedometers.

The core feature is an Augmented Reality (AR) view where passengers simply point their phone camera, and virtual arrows guide them step-by-step to their destination (Platform, Ticket Counter, Restroom). For visually impaired users, the app shifts to an audio-haptic mode, providing spatial voice cues. The system will feature an Admin Portal for station managers to block routes in real-time (e.g., if an escalator is under maintenance), dynamically recalculating paths just like Google Maps does for traffic.

## Proposed Solution / Architecture Diagram
1.The Passenger App (Mobile): Offers 3D map views, AR-based live navigation, and voice-guided routing. Supports offline routing via downloadable "Station Packs."
2.The Kiosk Interface: Touch-enabled 3D web application deployed on station displays. Users can scan a dynamically generated QR code on the kiosk to seamlessly transfer the mapped route to their mobile device.
3.The Station Master Portal (Web): A dashboard to manage points of interest (POIs), update station layouts, and broadcast emergency evacuations.
4.Hardware Layer: Strategically placed BLE (Bluetooth Low Energy) beacons around the station to ping mobile devices and calculate exact indoor location.
<img width="1024" height="559" alt="image" src="https://github.com/user-attachments/assets/8338ad1c-ef41-4b99-b4e2-29070d0a2517" />

## Use Cases
1.Locating a Platform & Coach:
Scenario: A passenger arrives 10 minutes before departure and needs to find Platform 4, Coach S-5.
Action: User enters the train number. The app queries the NTES API, finds the platform and coach position, and uses AR arrows to guide the user to the exact boarding spot.

2.Accessibility for Visually Impaired (PwD):
Scenario: A visually impaired user needs to find a restroom.
Action: User opens the app in "Accessibility Mode" and speaks their destination. The app uses BLE beacons to track their location and provides directional audio cues ("Walk 10 steps forward, turn slightly right").

3.Dynamic Route Adjustment (Admin):
Scenario: The main foot overbridge (FOB) is closed for cleaning.
Action: The station manager updates the system. The Routing Engine instantly closes those graph nodes and redirects all passenger app/kiosk queries to the secondary FOB.

4.Kiosk-to-Mobile Handoff:
Scenario: A tourist checks the station map on a digital kiosk to find the cloakroom.
Action: The kiosk calculates the route and displays a QR code. The tourist scans it with their phone, transferring the live navigation session to their mobile device.

## Technology Stack
1.Frontend (Mobile & Kiosk):
Mobile App: Flutter or React Native (for a single codebase across iOS and Android).
AR Navigation: ViroReact or Google ARCore / Apple ARKit.
Kiosk App: React.js with Three.js / Mapbox GL JS for rendering interactive 3D floor plans.
Voice Assistance: Google Cloud Speech-to-Text and Text-to-Speech APIs.

2.Backend & Cloud:
Server: Node.js (Express) or Python (FastAPI/Django) for handling concurrent routing requests.
Routing Logic: Graph-based pathfinding algorithms (A* or Dijkstra's) adapted for multi-floor indoor mapping.
Database: PostgreSQL with PostGIS extension (vital for storing spatial data and coordinates).
Hosting: AWS or Google Cloud Platform (GCP).

3.Hardware & Positioning:
BLE Beacons: Eddystone or iBeacon format hardware.
Positioning: Wi-Fi Round Trip Time (RTT) + Smartphone Accelerometer/Gyroscope data for dead reckoning.

## Dependencies
1.Hardware/Infrastructure Dependencies:
Installation and calibration of BLE Beacons every 10-15 meters across the railway station.
Access to digital Kiosk hardware at the station.

2.Software/Data Dependencies:
High-accuracy CAD blueprints or architectural floor plans of the railway stations to create the 3D maps and routing graphs.
API Access to Indian Railways (NTES/CRIS) for live train tracking, platform assignments, and coach layouts.

3.Operational Dependencies:
Cooperation from station management to keep the digital layout updated (e.g., notifying the system when a shop closes or opens).
Public internet connectivity (Wi-Fi/4G/5G), though the app should cache the station map locally for offline routing using pedometer/gyroscope data if the signal drops.
