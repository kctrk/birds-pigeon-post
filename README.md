# 🕊️ Birds — The Pigeon Post

> *Slow messaging meets virtual avian mechanics in an era of instant push notifications.*

**Birds** is a web-based slow-messaging concept inspired by historical postal pigeon systems. In modern chat apps, communication is instant and disposable. With **Birds**, letters take real time to travel, distance matters, and deliveries depend on the physical stamina and flight speed of your homing pigeons.

---

## 💡 The Philosophy Behind the Project

I built this project to explore how digital communication feels when you intentionally introduce **spatial physics, travel latency, and caretaking mechanics**. Instead of instantly hitting a socket and popping up on a screen, each letter is treated as physical cargo carried across geographic space.

---

## 🚀 Key Features

* 📍 **Geodesic Flight Calculations (Haversine Formula):**
  Uses precise coordinates for 81 Turkish provinces to compute spherical great-circle distances. Flight durations and stamina consumption scale dynamically based on real-world kilometers.
* 🕊️ **Avian Caretaking & Virtual Loft:**
  Pigeons aren't just delivery tokens; they require management. Track stats like **Energy, Satiety, Joy, and Health**. Birds get exhausted on long hauls and require feeding or roosting before taking flight again.
* ⚡ **Reactive Realtime Engine:**
  Powered by **Supabase Realtime** change data capture (CDC). Active pigeon routes update dynamically, synchronized across sender and recipient interfaces.
* 📜 **Atmospheric Vintage Aesthetic:**
  Hand-crafted retro interface inspired by antique post offices: parchment textures, daktilo typography (`Special Elite`, `Playfair Display`), animated route visualizers, custom wax seals, and theme switching.

---

## 🧮 How the Trip Mechanics Work

Distance calculation relies on the Haversine formula across latitude and longitude pairs:

$$d = 2R \cdot \arcsin\left(\sqrt{\sin^2\left(\frac{\Delta\phi}{2}\right) + \cos(\phi_1)\cos(\phi_2)\sin^2\left(\frac{\Delta\lambda}{2}\right)}\right)$$

1. **Route Mapping:** Origin and target coordinates are pulled from the city catalog (`C`).
2. **Flight Duration:** Travel time is computed against the assigned bird's baseline velocity:
   $$\text{ETA} = \frac{\text{Distance (km)}}{\text{Velocity (km/h)}} \times \text{Demo Time Scale}$$
3. **Fatigue & Delivery:** Long flights deplete bird energy. Upon reaching the ETA, Supabase RPC transitions the state atomically to `delivered`.

---

## 🛠️ Tech Stack

* **Frontend:** Vanilla JavaScript (ES6+), Semantic HTML5, CSS3 Variables & Keyframe Animations
* **Backend:** [Supabase](https://supabase.com/)
  * **Database:** PostgreSQL (with Row-Level Security policies)
  * **Realtime:** Postgres Changes (`INSERT`/`UPDATE` subscriptions)
  * **Stored Procedures:** Custom SQL RPCs for atomic operations (`send_letter`, `care_pigeon`, `sync_trips`)
* **Fonts & Icons:** Google Fonts (`Playfair Display`, `Special Elite`, `Lora`)

---

## 📦 Getting Started

### 1. Clone the Repository
```bash
git clone [https://github.com/your-username/birds-pigeon-post.git](https://github.com/your-username/birds-pigeon-post.git)
cd birds-pigeon-post
