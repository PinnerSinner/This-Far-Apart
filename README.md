This Far Apart 🌍
## 👉[Feeling needy? Come over for a hug](http://thisfarapart.s3-website-us-east-1.amazonaws.com) 👈

This Far Apart is an interactive, browser-based project that calculates and visualises the distance between a visitor and a fixed point in Copacabana, Brasil. It converts that distance into approximate travel times and various equivalents from footsteps to pizzas. The project serves both as a technical demonstration and an accessible teaching example for static web hosting
<img width="973" height="1091" alt="image" src="https://github.com/user-attachments/assets/29db1bdf-8a54-4a03-9371-ba23493243b8" />


## Technical Bits n bobs 

### Geolocation

The project uses the [ipapi.co](https://ipapi.co) API to obtain the visitor’s approximate latitude and longitude. This is achieved through IP-based geolocation, which estimates physical location from publicly routable network data. It does not rely on GPS or device permissions, which makes it ideal for a lightweight, serverless web application. The API response provides a JSON object containing the user’s city, region, country, and coordinates. Only the latitude and longitude are used for further computation.

While IP geolocation is not perfectly accurate (particularly when users are on VPNs or mobile networks), it is more than sufficient for showing how a browser client can integrate external data sources securely and asynchronously.

---

### Computation

Once both coordinate pairs are known (the user’s and the fixed Copacabana reference point), the page calculates the great-circle distance between them using the Haversine formula. This formula determines the shortest distance between two points on a sphere, accounting for the Earth’s curvature. The JavaScript implementation uses standard trigonometric functions and assumes an Earth radius of approximately 6,371 kilometres.

The resulting distance is expressed in kilometres, from which several derived values are calculated. Namely steps, assuming an average human stride length of 0.78 metres. Walking, running, and horseback time are stimates based on speeds of 5 km/h, 10 km/h, and 20 km/h respectively. 

---

### Mapping

The map interface is powered by [Leaflet.js](https://leafletjs.com), a lightweight open-source JavaScript library for interactive mapping. It renders a world map using OpenStreetMap tiles and plots two markers: one at the user’s detected location and another at Copacabana. 
A polyline connects these points, creating a visual line-of-sight across the Earth’s surface. The map is fully interactive so users can pan, zoom, or drag to inspect the geography of their connection. The view automatically adjusts to fit both points within the viewport using Leaflet’s `fitBounds` method. This component demonstrates how a static webpage can incorporate spatial visualisation without any proprietary GIS backend or paid API.


