# Maritime Chokepoints Under Conflict

We combine weekly conflict data (ACLED) with shipping traffic (IMF PortWatch) to study how chokepoints in the Middle East respond to conflict.

## Research questions

1. What is the quantitative and temporal impact of elevated regional conflict activity on weekly transit counts (`n_total`) and deadweight tonnage (DWT) capacity through the Strait of Hormuz, and what is the recovery period required to return to pre-escalation baselines?
2. At what threshold of conflict intensity is there a significant diversion of maritime traffic from the Suez Canal and Bab el-Mandeb toward the Cape of Good Hope, and to what extent does this rerouting behavior persist after regional conflict intensity subsides?
3. How does transit resilience to regional conflict escalation vary across commercial vessel classifications (container ships, tankers, and dry bulk carriers), as measured by the retention of baseline transit shares through the Strait of Hormuz and the Bab el-Mandeb?

## Contributions

| Team member | Contribution |
|---|---|
| Jan Marcan | Data collection |
| Benjamin Jud | Data filtering |
| Liudmyla Marcan | Data visualization |

## Results

- **RQ1:** The largest conflict escalation in our data, in March 2026, cut Hormuz transits by 97.5% and capacity by 98.7%. Traffic had not recovered 30 weeks later, when our data ends. The smaller escalation of June 2025 (war between Israel and Iran) shows no clear effect.
- **RQ2:** Attacks on ships in the Red Sea began in November 2023. In December 2023, ships started going around Africa instead, at about 7 conflict events at sea per week. The share of traffic using the Cape route stayed at 49.9% or more from March 2024, even in the calmest weeks.
- **RQ3:** In high-conflict weeks, dry bulk carriers keep the most of their normal traffic at both straits: 41.7% at Hormuz and 60.3% at Bab el-Mandeb. The ranking at Hormuz is uncertain, because the ship types are close together.

Written answers are in notebook 03. Figures and result tables are in `figures/`.

## Limitations

- ACLED records all events at sea in one region, so we cannot tell exactly where they happened. We use them as an approximate measure of Red Sea attacks.
- Traffic in consecutive weeks is related, so the significance tests make results look more certain than they are.
- A ship using the Red Sea route is often counted twice, at both Bab el-Mandeb and Suez, while a ship using the Cape is counted once. This makes Cape share lower than the true share.

## Running the project

ACLED's licence restricts sharing its data, so the repository contains no ACLED data files. Its API was not available for our account, so we downloaded the file manually.

1. Run `pip install -r requirements.txt` (Python 3.12).
2. Download *Middle East aggregated data* from the ACLED website and save it as `data/raw/acled/Middle-East_aggregated_data_up_to_week_of-2026-09-26.xlsx`.
3. From the repository root, run the notebooks in order: 01, 02, 03.

## ACLED attribution

Source: Armed Conflict Location & Event Data (ACLED), www.acleddata.com, accessed on 11 October 2026.

Citation: Raleigh, C., Kishi, R. and Linke, A. (2023). Political instability patterns are obscured by conflict dataset scope conditions, sources, and coding choices. *Humanities and Social Sciences Communications*. https://doi.org/10.1057/s41599-023-01559-4

We filtered the data, summed it to weekly totals, filled weeks without events with zeros, separated events at sea, added rolling means and a High/Low conflict label, and merged it with PortWatch data. These changes and any errors they introduce are our own.
