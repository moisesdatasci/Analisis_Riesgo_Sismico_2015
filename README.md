# Chile Seismic Risk Analysis (2002-2015)

**A Data Science project to identify and visualize seismic risk zones for urban planning and construction.**

This repository, `Analisis_Riesgo_Sismico_2015`, contains the complete end-to-end workflow for analyzing seismic hazard in Chile using a 13-year dataset from the National Seismological Center (CSN).

---

### **Final Project Deliverable: Interactive Risk Map**

<p align="center">
<img width="325" height="603" alt="Mapa1" src="https://github.com/user-attachments/assets/33c3dfa1-6d5b-48a4-b55e-ac01f30362b3" />
<img width="325" height="603" alt="mapa 2" src="https://github.com/user-attachments/assets/16cf8e00-e5b2-4bd4-837c-7c214e20b4cb" />
<img width="325" height="603" alt="Mapa3" src="https://github.com/user-attachments/assets/613f1e4b-edb6-4ccd-bd53-0f3314a990a1" />
</p>


*mapa_sismicidad_chile_v3.png*
---

## 1. Project Objective & Business Problem

For a (fictional) construction firm looking to invest in Chile, the generic statement "Chile is a seismic country" is not actionable. This project was designed to answer a specific business question:

> **"Where are the zones of highest and lowest seismic risk, and how does this risk differ across the country?"**

The goal was to move beyond simple data plotting to create a strategic tool that differentiates risk by two key factors:

1.  **High-Frequency Risk:** Where does it shake *most often*? (A risk of material fatigue).
2.  **High-Severity Risk:** Where does it shake *hardest*? (A risk of catastrophic failure).

## 2. Tech Stack 🛠️

* **Language:** Python
* **Data Manipulation:** Pandas, NumPy
* **Text Cleaning (Regex):** `re`
* **Data Visualization (EDA):** Matplotlib, Seaborn
* **Geospatial Analysis:** Folium (HeatMap, GeoJSON, CircleMarkers)
* **Environment:** Google Colab / Jupyter Notebook

## 3. The Workflow & Methodology

This project followed a structured, 6-step data science process:

1.  **Problem Definition:** Defined the stakeholder (construction firm) and the key questions (risk by frequency vs. severity).
2.  **Data Acquisition:** Sourced the seismic catalog (2002-2015) from Chile's National Seismological Center (CSN).
3.  **Data Cleaning & Wrangling:** This was the most critical technical challenge.
    * **Text Surgery (Regex):** Used `re` to parse a single, reliable float value (prioritizing `Ml`) from a "dirty" magnitude column (e.g., `"2.9 Mc GUC3.1 Ml GUC"`).
    * **Type Conversion:** Converted date columns from `object` to `datetime`.
    * **Geographic Filtering:** Filtered a global dataset (58k+ rows) down to a high-quality, relevant dataset (57k+ rows) within Chile's "bounding box".
4.  **Exploratory Data Analysis (EDA):** Visualized the data to find patterns.
    * Identified the **2010 (M 8.8)** and **2014 (M 8.2)** earthquakes as massive spikes in the time-series plot.
    * Confirmed that 75% of all quakes are "background noise" (M < 3.7), validating the need to focus on the top 25%.
5.  **Advanced Geospatial Visualization:** Built the final `mapa_sismicidad_chile_v3.html` deliverable using `folium`. This map overlays:
    * **GeoJSON Layer:** Chile's regional boundaries for administrative context.
    * **HeatMap Layer:** A density map of M > 3.0 quakes to show *frequency*.
    * **Marker Layer:** Circle markers for M > 5.5 quakes to show *severity*.
    * **Layer Control:** A toggle to allow the user to explore each layer independently.
6.  **Conclusion:** Synthesized all findings into a clear, actionable insight.

## 4. Key Findings

The final interactive map clearly confirms that "seismic risk" in Chile is not uniform. We identified two distinct risk profiles:

* **FINDING 1: High-Frequency Risk (Northern Chile)**
    The Heatmap is most intense in the **Arica, Tarapacá, and Antofagasta** regions. This zone experiences *constant* seismic stress, posing a risk of material fatigue and operational disruption.

* **FINDING 2: High-Severity Risk (Central-South Chile)**
    The high-magnitude Circle Markers (M > 6.5) are most concentrated in the **Valparaíso, Maule, and Biobío** regions. This zone faces a risk of *catastrophic* (high-energy) events, even if the daily frequency is lower than in the north.

## 5. How to Run This Project

You can replicate this analysis by following these steps:

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/moisesdatasci/Analisis_Riesgo_Sismico_2015.git
    cd Analisis_Riesgo_Sismico_2015
    ```
2.  **Install dependencies:**
    *(This project was built in Google Colab. The main libraries are listed in `requirements.txt`)*
    ```bash
    pip install -r requirements.txt
    ```
3.  **Run the analysis:**
    Open the `chile_seismic_analysis.ipynb` notebook in Jupyter Lab or Google Colab.

4.  **Explore the Deliverable:**
    Run the notebook cells to generate the `mapa_sismicidad_chile_v3.html` file. Open this file in any web browser to interact with the final map.

## 6. Future Work (V2.0)

This 2002-2015 project serves as a successful **Proof of Concept (PoC)**. A new, more advanced analysis is planned (V2.0) using an updated dataset spanning **2002-2024**. This new project will explore:

* DBSCAN clustering to algorithmically identify fault lines.
* 3D risk profiling by analyzing earthquake `depth`.
* Merging seismic data with population density to create a *Human Risk Index*.

## 7. Author

* **Moisés Ortega**
* **GitHub:** [moisesdatasci](https://github.com/moisesdatasci)
* **LinkedIn:** [moisesortega-datascience](www.linkedin.com/in/moisesortega-datascience)
