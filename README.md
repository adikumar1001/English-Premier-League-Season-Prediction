# ⚽ English Premier League — Season Prediction (xG + Comeback Analysis)

This project predicts **relative team strength and end‑of‑season outlook** for the English Premier League by combining:
- **Expected goals (xG) profile** — average xG **for** and **against**, and **xG difference** as a performance baseline.
- **Resilience / Comeback ability** — points gained from losing positions and frequency of fight‑backs.
- (Optional) recent‑form weighting and strength‑of‑schedule adjustments.

Outputs include summary tables in Excel for easy sharing.

---

## 📂 Repository Structure
```
.
├─ Code/
│  └─ Average_xg_and_comeback_code.ipynb   # Main notebook (cleaning + metrics + export)
├─ data/
│  ├─ England CSV.csv                      # Match-level data (season 1)
│  └─ England 2 CSV.csv                    # Match-level data (season 2 / additional rounds)
├─ Output/
│  ├─ team_avg_xg.xlsx                     # Team xG for/against & xG difference
│  └─ comeback_analysis_output.xlsx        # Comeback metrics & resilience index
├─ README.md

```
> Filenames above reflect the uploaded assets; if your paths differ, update them in the notebook’s first cell.

---

## ▶️ Quickstart
### Local
```bash
# 1) Create & activate env
python -m venv .venv && source .venv/bin/activate   # (Windows) .venv\Scripts\activate

# 2) Install deps
pip install -r requirements.txt

# 3) Run
jupyter lab  # or jupyter notebook
# Open: Code/Average_xg_and_comeback_code.ipynb → Run All
```
### Google Colab
Upload the notebook and the two CSVs to Colab (or mount Drive), then run all cells.
Add at the top if needed:
```python
!pip -q install pandas numpy matplotlib openpyxl seaborn
```

---

## 📑 Data (expected columns)
Your CSVs should include typical match‑level fields such as:
- `date`, `home_team`, `away_team`, `home_xg`, `away_xg`, `home_goals`, `away_goals`
- (optional) in‑match state or event data to detect trailing periods.  
If your column names differ, adjust the mapping cell in the notebook.

---

## 📤 Outputs
- **`Output/team_avg_xg.xlsx`**  
  - Columns: `team`, `matches`, `xG_for`, `xG_against`, `xG_diff`, optional rolling metrics.
- **`Output/comeback_analysis_output.xlsx`**  
  - Columns: `team`, `trailing_games`, `comeback_wins`, `comeback_draws`, `points_from_losing_positions`, `resilience_index`.

Use these sheets to build a predicted table (sort by `xG_diff`, then `resilience_index`).

---

## ✅ Quality Checks
- Sum of home/away matches per team equals total fixtures played.
- xG totals roughly align with goal totals at league level (xG ≈ goals over large samples).
- PFLP is computed **only** from games where the team actually trailed.
- No leakage across seasons if combining multiple years (keep season key).

---

## 🚀 Ideas & Extensions
- Poisson / Dixon‑Coles simulations using **xG‑derived attack/defense ratings**.
- Elo‑style dynamic ratings seeded by xG.
- Injury/suspension and schedule density features.
- Visuals: rolling xG difference, resilience vs xG scatter, predicted table vs actual.

---

## 👤 Author
**Aditya Kumar** — Football analytics & ML.  
Questions or suggestions? Open an Issue or PR.

