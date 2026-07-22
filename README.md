# Smart Mobility Demo
Minibuses are the main form of public transport in major African Cities like Nairobi and Lagos. These are typically operated by SACCOs along fixed routes and informal time schedules.

**The Problem:** Major African cities are set to experience rapid growth over the coming decade. The existing public transport system is not responsive to changing commuter demands costing passengers time and money from multiple changes. This also has an opportunity cost for the operators who may benefit from running buses on new routes.

**The Solution:** We dynamically suggest 'flexiroutes' to bus operators to meet real-time commuter demand. We also learn commuter travel patterns over time.

## Key Features

* **Advance Scheduling:** Commuters can book their journeys in advance to depart or arrive within a time window
* **Route Optimisation:** Buses are dynamically assigned to 'flexiroutes' to efficiently meet commuter demand subject to time and cost constraints
* **Dynamic Pricing:** Flexi-routes and prices are such that journeys are cost-effective for the bus drivers and for the commuters compared to existing alternatives (???)
* **Pattern Recognition:** Commuter travel patterns are modelled allowing the bus operators to plan their operations better  

## Stack

* **Backend:** Python3+, FastAPI / Pydantic

## The Win-Win

Suppose a set of people wish to commute from town A to town C at roughly the same time. Suppose that the current transport network requires them to first travel to town B and then to change to another bus to get to town C. Let $m$ denote the maximum occupancy of the vehicle; $p$ a fraction of the maximum occupancy; $w$ the cost per passenger for a given journey and $d$ the distance between two given towns (indexed by the endpoints). We define the *Revenue per mile* $R$ as the key metric the operators wish to maximise whilst the individual passenger wishes to minimise cost. Here are some simplifying assumptions we make

### Assumptiions:
* The operation cost per mile is constant
* The average speed along any two routes is the same
* Existing routes are popular and buses are always at maximum occupancy

Suppose a bus takes $pm$-many passengers directly from town A to town C. A win for the operator means
$$
\frac{pmw_{AC}}{d_{AC}} \leq \frac{mw_{AB}}{d_{AB}} + \frac{mw_{BC}}{d_{BC}}
$$

whereas a win for the passenger means saving money

$$
w_{AC} \leq w_{AB} + w_{BC}
$$

A win-win is thus feasible provided

$$
d_{AC}\left(\ \frac{w_{AB}}{d_{AB}} + \frac{w_{BC}}{d_{BC}}\right) \leq pw_{AC} \leq p(w_{AB} + w_{BC})
$$

equivalently,

$$ 
\frac{d_{AC}}{w_{AB} + w_{BC}}\left(\ \frac{w_{AB}}{d_{AB}} + \frac{w_{BC}}{d_{BC}}\right) < p \leq 1
$$