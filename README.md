# 🧠 Unified Optimization Framework + Insights

## 🎯 Objective

Design an intelligent supply chain that:
- Minimizes logistics and inventory costs
- Achieves ≥95% service level
- Is resilient to disruptions
- Aligns pricing, sourcing, and demand dynamics

---

## 🔍 Cross-Linked Insights from Data Analysis

### 1. 🎯 SKU Prioritization & Demand Focus

- **59% of SKUs account for 80% of revenue** (Pareto Rule) — mainly skincare
- **Volatile demand SKUs** coincide with **high revenue impact** — must avoid stockouts
- **High-volume SKUs** show **price-inelastic demand**, enabling margin-focused pricing

✅ **Action:**  
Apply differentiated service levels:

| SKU Type        | Policy                     |
|-----------------|----------------------------|
| High revenue    | Safety stock + priority fulfillment |
| Mid volume      | JIT or reorder-point based |
| Low margin      | Ship in consolidated low-cost batches |

---

### 2. 🛠️ Inventory–Transport Cost Optimization

#### Trade-off Principle:

- Bulk orders → ↓ transport cost but ↑ holding cost
- JIT → ↑ transport cost but ↓ working capital

#### Enhanced Safety Stock Model (includes disruption and defect buffers):

$$
SS = z \cdot \sigma_D \cdot \sqrt{LT} + \mu_D \cdot (DR + SR)
$$

Where:
- $DR$ = Defect rate  
- $SR$ = Supplier risk (delay probability × avg. delay days)

✅ **Action:**  
- Implement dynamic safety stock zones using this equation
- Reserve air shipments for SKUs with both **high $\mu_D$** and **high $SR$**

---

### 3. 🚚 Transport & Route Rebalancing

#### Cost vs. Mode:

| Mode | Avg Cost/Unit | Lead Time | Use Case                            |
|------|---------------|-----------|-------------------------------------|
| ✈️ Air | \$6.02         | 2.3 days  | High-priority SKUs, launches        |
| 🚛 Road | \$4.97         | 4.7 days  | Default for medium-sensitivity SKUs |
| 🚆 Rail | \$3.97         | 6.1 days  | Long-haul, stable demand SKUs       |
| 🚢 Sea  | \$2.15         | 9.8 days  | Bulk orders, predictable demand     |

#### Modal Optimization Function:

$$
\min Z = 0.7 \cdot \text{Cost} + 0.3 \cdot \text{Time}
$$

✅ **Action:**  
- Switch predictable SKUs from **Road → Rail/Sea**
- Enforce modal selection using urgency-cost tradeoff function

---

### 4. 🧪 Supplier Quality and Delay Mitigation

#### Supplier Scorecard (Updated from Insights):

| Metric              | Weight | Supplier 1 | Supplier 3 | Supplier 5 |
|---------------------|--------|------------|------------|------------|
| On-Time Delivery    | 35%    | 82%        | 61%        | 67%        |
| Defect Rate         | 25%    | 1.8%       | 2.3%       | 2.67%      |
| Cost Consistency    | 20%    | ±9%        | ±14%       | ±15%       |
| Disruption Risk     | 20%    | Low        | High       | Medium     |

✅ **Action:**
- Discontinue or dual-source for **Supplier 5**
- Negotiate SLAs with **Supplier 3** to mitigate lead times
- Create a **resilience buffer** by pairing high-risk suppliers with reliable logistics

---

### 5. 🏭 Manufacturing Bottlenecks

- **SKU1, SKU30, SKU0, SKU23, SKU92** delayed >30 days
- **Chennai/Bangalore**: high lead time & cost

✅ **Action:**
- Shift backlog-prone SKUs to **Mumbai/Delhi**
- Create **cross-facility flexibility** to absorb load imbalance

---

### 6. 📦 Demand-Driven Inventory Logic

#### Insight:  
Revenue negatively correlates with inventory ($r = -0.16$) → implies stockouts during peak demand

#### Improvement:

Use **lead-time-based reorder policy**:

$$
ROP = (\mu_D \cdot LT) + SS
$$

And:

- Incorporate **seasonal uplift** factors
- Use **Monte Carlo simulations** for +30% demand surge scenarios

---

### 7. 🔄 End-to-End Synchronization

- **Lead times** between manufacturing and shipping are uncorrelated ($r = -0.017$)
- Suggests siloed planning

✅ **Action:**  
- Integrate MRP (Material Requirements Planning) + TMS (Transport Management System)
- Weekly sync to align production and shipment release schedules

---

## 🧾 Summary: Unified Strategic Moves

| Domain                  | Insight                                         | Optimization Action                                      |
|------------------------|--------------------------------------------------|-----------------------------------------------------------|
| Inventory              | Revenue periods cause stock dips                | Dynamic safety stock + ROP recalibration                 |
| Transport              | Cost varies significantly by mode               | Mode optimization + urgency-based routing               |
| Suppliers              | High defects and delays                         | Scorecard-driven rationalization + dual sourcing         |
| Production             | Bottlenecks in Chennai/Bangalore                | Load balancing + facility agility                        |
| Price Strategy         | Price ≠ cost aligned                            | Cost-based or margin-focused pricing review              |
| Lead Time              | Poor sync between production and logistics      | Integrated schedule planning                             |

---

## 🧭 Next Steps (Updated)

1. Implement multi-echelon inventory model with revenue-weighted ROP
2. Establish predictive defect risk dashboard (supplier + mode-based)
3. Run disruption simulations quarterly (delay, port, demand shock)
4. Start phase-wise rollout of optimized route matrix
5. Align pricing strategy with manufacturing cost structure

---
