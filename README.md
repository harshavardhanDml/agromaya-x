🌾 BioChar Connect

Smart satellite-based agricultural residue collection platform

BioChar Connect connects **farmers**, **Gram Panchayats**, and **biochar manufacturing companies** through satellite crop monitoring, residue procurement, farmer incentives, and logistics management. The goal is to reduce crop residue burning and give biochar producers a reliable feedstock supply chain.

> ⚠️ Prototype notice: This is a hackathon demo. All data is fictional, satellite imagery and detections are stimulated, environmental figures are **illustrative estimates (not verified carbon credits)**, and cashback is simulated/pending. No real payment or bank transfer takes place.

---
 ✨ Features

 🏭 Biochar Company Dashboard
- Map view:field polygons coloured by status, with a legend and district filter
  - 🟢 Growing
  - 🟡 Possibly harvest-ready (needs manual verification)
  - 🔴 Verified / priority collection
- Field details: farmer, village, Panchayat, area, crop, harvest period, simulated satellite preview (NDVI)
- **Harvest-ready detection:** verify a field, then send a feedstock request
- **Request tracker:** Pending → Accepted / Rejected → Harvesting → Delivered
- **Farmer management:** contact details, land, crop, supply history, credits
- **Panchayat management:** stock per Panchayat, **Schedule Pickup**
- **Logistics tracking:** Pickup Requested → Scheduled → Vehicle Dispatched → Collected → Delivered to Factory
- **Inventory:** stock by crop, monthly collection, estimated biochar potential, collection history
- **Analytics:** farmers participating, Panchayats connected, quintals collected, estimated burning avoided, estimated CO₂e avoided, monthly trend chart

👨‍🌾 Farmer Portal
- Registration with an auto-generated Farmer ID
- Dashboard: land, crop, harvest status, supplied quantity, credits, cashback
- Accept or reject company feedstock requests
- Submit delivery notifications to the registered Gram Panchayat
- Rewards: total and redeemable credits, cashback (pending), loyalty level (Bronze / Silver / Gold / Platinum), transaction history

 🏛️ Gram Panchayat Operator
- View registered farmers and incoming deliveries
- Verify identity, enter actual weight, select feedstock type, attach a delivery photo
- Confirm delivery, which automatically:
  - increases Panchayat inventory
  - updates the farmer's credits and cashback
  - updates company inventory and analytics
- Approve and coordinate company pickups
- Configure reward rates

---

🔄 End-to-End Workflow

1. Satellite monitoring flags a field that may be mature (simulated)
2. The field is matched to a registered farmer
3. The company sees it as *potentially* harvest-ready
4. Company staff **verify manually**, then send a procurement request
5. Farmer accepts and harvests
6. Farmer delivers the residue to the Gram Panchayat
7. Operator verifies identity, type and actual weight
8. Credits and cashback are calculated
9. Panchayat inventory updates automatically
10. Company schedules a vehicle pickup
11. Panchayat confirms handover, company confirms collection
12. Feedstock reaches the factory and analytics update

---

🎁 Reward Logic (configurable)

| Rule | Default |
|---|---|
| Credits per verified quintal | 100 |
| Regular supplier bonus (2 or more earlier verified deliveries) | +10% credits |
| Cashback per eligible quintal (simulated / pending) | ₹5 |

Loyalty levels by total supplied quantity: Bronze (under 20 q), Silver (under 60 q), Gold (under 120 q), Platinum (120 q and above).

---

 🚀 Getting Started

No build step or dependencies are needed.


You can also deploy it as-is with **GitHub Pages**: Settings → Pages → deploy from the `main` branch.

Demo logins
Choose a role on the first screen. No registration is needed.

| Role | What to try |
|---|---|
| Biochar Company Admin | Map → Harvest-ready → verify a field → send request |
| Farmer | Requests → accept → Delivery → submit notification |
| Gram Panchayat Operator | Deliveries → tick ID, enter weight → Confirm |

Farmers and Panchayats can be switched with the dropdown at the top of those views.

---

 🧱 Tech Stack (current prototype)

- Vanilla HTML, CSS and JavaScript in a single file
- Inline SVG for the map and charts
- In-memory state (resets on page reload)

Business logic (reward calculation, inventory updates, status transitions) is kept in plain functions so it can be moved behind a real API.

🗄️ Planned Data Model (PostgreSQL)

`users` · `farmers` · `companies` · `gram_panchayats` · `agricultural_fields` · `satellite_observations` · `harvest_detections` · `feedstock_requests` · `feedstock_deliveries` · `panchayat_inventory` · `farmer_credit_ledger` · `cashback_transactions` · `pickup_schedules` · `logistics_records`

Key relationships:
- A farmer has many fields and belongs to one Gram Panchayat.
- A field has many satellite observations and harvest detections.
- A company sends feedstock requests to farmers for a field.
- A request leads to a delivery, which is verified by a Panchayat operator.
- A verified delivery writes to the credit ledger and increases Panchayat inventory.
- A pickup schedule links a company to a Panchayat and has logistics records.

---

 🛣️ Roadmap

- [ ] React, TypeScript, Tailwind and shadcn/ui front end
- [ ] Node.js or Go REST API with PostgreSQL and JWT role-based auth
- [ ] Leaflet or Mapbox with real farm boundaries
- [ ] Real satellite imagery (e.g. Sentinel-2 NDVI) for maturity detection
- [ ] SMS / WhatsApp notifications in Kannada and English
- [ ] Payment gateway integration for cashback payouts
- [ ] Pickup scheduling by date and vehicle
- [ ] Verified carbon accounting methodology

---

⚠️ Disclaimers

- Yellow-colour detection only **indicates possible maturity**. It does not guarantee harvest readiness, so a manual verification step is required before a request is confirmed.
- Carbon and burning-avoided numbers are **illustrative estimates**, not verified carbon credits.
- Cashback is **simulated**. No real money is transferred.
- All farmers, companies and Panchayats shown are **fictional demo data**.
