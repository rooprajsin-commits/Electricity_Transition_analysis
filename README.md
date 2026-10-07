# ⚡ Global Electricity Transition Analysis (2015–2025) | Microsoft Excel

An end-to-end data analysis project in **Microsoft Excel** that looks at how 212 countries generated electricity between 2015 and 2025, how fast the world is moving from fossil fuels to renewables, and where **India** stands.

![Dashboard](images/dashboard.png)

---

## 📌 Business Questions

1. How has the global electricity mix changed in the last decade?
2. Where does India stand versus the world on renewables and coal?
3. Which large power systems have the highest renewable share?
4. Which countries added solar and wind the fastest?
5. Which countries still depend most on coal?

## 📂 Dataset

| | |
|---|---|
| **Source** | [Our World in Data – Energy dataset](https://github.com/owid/energy-data) (release of 1 Oct 2026), built on Ember and the Energy Institute Statistical Review |
| **Licence** | CC BY 4.0 |
| **Scope** | 2015–2025 · 212 countries + World total · 2,202 clean records |
| **Columns used** | 16 of 130: generation by source (TWh), population, carbon intensity |

## 🛠️ Approach

`Extract → Clean → Model → Analyse → Visualise → Present`

| Step | What I did |
|---|---|
| **Extract** | Pulled 3,030 rows (2015–2025) and 16 relevant columns |
| **Clean** | Removed aggregates and invalid rows, filled blank source fields, logged every step |
| **Model** | Added 11 calculated columns: fossil, renewable and low-carbon totals, shares, kWh per person, validation check |
| **Analyse** | Built formula-driven rankings and a country summary using SUMIFS, INDEX/MATCH and LARGE |
| **Visualise** | Created a KPI dashboard and an interactive country profile with dynamic charts |
| **Present** | Wrote 7 insights with live figures and a LinkedIn presentation |

### Data cleaning log

| Cleaning step | Affected |
|---|---|
| Removed regions and income groups (they would double-count countries) | 750 rows |
| Removed country-years with no total generation | 67 rows |
| Removed reports of exactly 0 TWh (Lesotho, Niue) | 11 rows |
| Filled blank source fields with 0 when a total existed | 507 cells |
| Validated that sources add up to 100% of the total | 0 failures |

> **Data quality catch:** A validation column flagged 11 rows where the generation mix did not add up. Lesotho and Niue were reporting 0 TWh. These were reporting gaps, not real zeros, so I removed them and documented the reason.

## 📊 Key Insights

- **Renewables grew from 23.0% to 33.8%** of world electricity (2015 → 2025), while coal fell from 38.7% to 33.0%.
- **Solar output grew 10.9x** (256 → 2,779 TWh). Solar and wind covered **57% of the rise in global demand** since 2015.
- Coal output in TWh is still roughly flat, because total demand grew 32%. New renewables are mostly covering growth, not yet replacing coal.
- **India's renewable share rose from 14.6% to 24.1%** and its solar output grew 27.6x, but coal still supplies about **71%** of its electricity.
- **25 of 83 large power systems** (≥ 20 TWh) got at least half their electricity from renewables in 2024. Most leaders are hydro-rich (Paraguay, Ethiopia, Norway).
- **Fastest solar + wind gains** (2015 → 2024): Netherlands (+37.3 pp), Chile (+30.1 pp), Greece (+25.0 pp).

![World electricity mix](images/world_mix.png)
![India vs World](images/india_vs_world.png)

## 🧮 Excel Skills Used

- **Functions:** SUMIFS, COUNTIFS, INDEX/MATCH, LARGE, IFERROR, IF/AND, ISNUMBER, CAGR formula
- **Lookups on a text key** (`Country|Year`) for multi-criteria matching
- **Formula-driven Top-N rankings** with tie-breaking, no manual sorting
- **Data validation** dropdown for an interactive country profile
- **Input parameters:** change the analysis year and the whole workbook recalculates
- **Conditional formatting:** colour scales, data bars, error flags
- **Excel Tables**, stacked column, bar and line charts, and a KPI dashboard

![Country profile](images/country_profile.png)

## 📁 Workbook Structure

| Sheet | Purpose |
|---|---|
| `README` | Project overview and sheet guide |
| `Dashboard` | KPI cards and 4 charts |
| `Inputs` | Editable parameters (base year, analysis year, minimum size, target) |
| `Country_Profile` | Pick any country from the dropdown; table and charts update |
| `Global_Trends` | World electricity mix by source, 2015–2025 |
| `Rankings` | Top 15 by renewable share, top 15 by solar + wind gain, top 10 coal-dependent |
| `Insights` | Written findings with live figures |
| `Country_Summary` | One row per country: base vs analysis year, change and growth rate |
| `Clean_Data` | Analysis-ready Excel Table with calculated columns |
| `Raw_Data` | Untouched extract from the source |
| `Cleaning_Log` | Every cleaning step and rows affected |
| `Data_Dictionary` | Definitions and units for every column |

## ▶️ How to Use

1. Download [`workbook/Electricity_Transition_Analysis.xlsx`](workbook/Electricity_Transition_Analysis.xlsx).
2. Open the **Dashboard** sheet for the summary.
3. Go to **Country_Profile** and choose a country from the yellow dropdown cell.
4. Change the years on the **Inputs** sheet to re-run the rankings for a different period.

The presentation is in [`presentation/`](presentation/) as both PDF and PowerPoint.

## ⚠️ Limitations

- Covers electricity only. Transport and heating energy are not included.
- 2025 country data is preliminary (90 countries reported, against 195 for 2024), so country rankings use 2024. World totals use 2025.
- Bioenergy is counted as renewable, following Our World in Data and Ember conventions.
- Generation share is not the same as installed capacity.

## 📬 Contact

Feedback and questions are welcome. Feel free to open an issue or connect with me on LinkedIn.
