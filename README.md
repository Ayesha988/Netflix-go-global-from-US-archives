# Analysis Report: The Globalisation of Netflix (2008–2021)

## 1. Technical Audit & Analytical Journey
This project was not a linear path; it was an iterative investigation. My journey involved constant cross-checking of the data against emerging visual patterns to validate Netflix's business shifts.

### Pre-Processing & Technical Hurdles
* **The Comma-Separated Data Challenge:** Early on, I observed that `cast` and `listed_in` contained nested strings. I implemented `df.explode()` to ensure that when we counted genres or actors, every single entry was accounted for, rather than just the first name in the list.
* **Data Integrity:** I chose to categorise missing values as "Unknown" rather than dropping rows. This was a critical decision to maintain the 8,800+ title volume needed for a reliable world map.
* **Temporal Cleanup:** I converted `date_added` into a standard datetime format using `pd.to_datetime()`, which allowed for the "Freshness" analysis later in the project.

---

## 2. The 9-Step Technical Narrative

### I. Content Growth (Area/Line Plot)
* **Observation:** I noticed a massive surge in TV shows starting around 2015. 
* **Cross-Check:** We validated that while Movies have the highest total count, the *velocity* of TV Show additions is higher.
* **Functions:** `sns.lineplot()`, `plt.fill_between()`.
<img width="877" height="464" alt="image" src="https://github.com/user-attachments/assets/7db0fd16-a379-4b11-b6bc-abf8bc28ff79" />


### II. Global Footprint (Geospatial Mapping)
* **Observation:** The US is the anchor, but the data showed significant "pockets" of activity in India and the UK.
* **Functions:** `geopandas.read_file()`, `.to_crs(epsg=3857)`, `.centroid`.
<img width="865" height="802" alt="image" src="https://github.com/user-attachments/assets/6de003f5-7d19-4f81-b5e3-4053cd43c2d5" />


### III. Regional Specialisation (Heatmap)
* **Observation:** I noticed different countries weren't just producing content—they were specialising. 
* **Cross-Check:** The data confirmed India leads in International Movies, while Japan and South Korea dominate the TV space with Anime and K-Dramas.
* **Functions:** `pd.pivot_table()`, `sns.heatmap(fmt='.0f')`.
<img width="877" height="617" alt="image" src="https://github.com/user-attachments/assets/a8928f39-4ee1-4c4b-864f-8e85ac3b13af" />


### IV. Seasonal Release Cycles (Count Plot)
* **Observation:** I suspected releases weren't random. 
* **Cross-Check:** Visualising the months showed clear peaks in Q3 and Q4, synchronised with global holiday seasons.
* **Functions:** `.dt.month_name()`, `sns.countplot()`.
<img width="883" height="515" alt="image" src="https://github.com/user-attachments/assets/83dc5ddb-5336-4954-a1ed-72ffe92caaa3" />


### V. The Freshness Factor (Gap Distribution)
* **Observation:** I wanted to see if Netflix was buying "old junk" or fresh content.
* **Cross-Check:** The histogram showed a heavy skew towards 0-1 year gaps, proving a "Day and Date" acquisition strategy.
* **Functions:** `sns.histplot(kde=True)`.
<img width="872" height="460" alt="image" src="https://github.com/user-attachments/assets/6292d0d1-1402-412a-9d5d-c46b869957b1" />


### VI. Audience Maturity (Categorical Bar Chart)
* **Observation:** The rating system (TV-MA, TV-14) was too messy. 
* **Cross-Check:** I mapped these into **Kids, Teens, and Adults**. The result proved Netflix is heavily weighted toward mature content to compete with "Prestige" cable.
* **Functions:** `.map()` with a custom dictionary, `ax.bar_label()`.
<img width="869" height="547" alt="image" src="https://github.com/user-attachments/assets/79e1069a-ba3e-4a86-85db-4a5a6ad19497" />


### VII. The Architects (Lollipop Chart)
* **Observation:** Certain names kept appearing in the director column.
* **Functions:** `plt.hlines()`, `sns.scatterplot()` to create a clean, modern visual.
<img width="861" height="562" alt="image" src="https://github.com/user-attachments/assets/7ea89450-baac-4825-aac9-1712768ed22a" />


### VIII. Star Power & The Indian Dominance (Bar Chart)
* **Observation:** I noted the Top 10 cast was almost exclusively Indian.
* **Cross-Check:** We discussed this and concluded it wasn't an error, but a reflection of India's high-volume production and Netflix’s aggressive acquisition of Bollywood libraries.
* **Functions:** `df.explode('cast')`, `sns.barplot()`.
<img width="882" height="571" alt="image" src="https://github.com/user-attachments/assets/6fe54945-9709-40ba-a2be-82202eb78422" />


### IX. Thematic Semantic Mapping (Word Cloud)
* **Observation:** I wanted to see the "Vibe" of the descriptions.
* **Functions:** `WordCloud()`, `plt.imshow()`.
<img width="839" height="469" alt="image" src="https://github.com/user-attachments/assets/98614c29-71ed-4517-9e47-b1575618afff" />

---

## 3. Strategic Takeaways
Through these 9 visuals, we successfully cross-checked our outcomes to form a cohesive conclusion:

Netflix is not just a tech company; it is a global "Cultural Mirror." It adapts its library's genre, maturity, and release timing to fit the world's diverse viewing habits. By focusing on universal human themes like **Love, Family, and Mystery**, they ensure that a story produced in Mumbai or Seoul can become a global hit.

### Key Summary:
1.  **Market Localisation:** Moving from US-centric archives to global hubs like India and East Asia.
2.  **Operational Agility:** Reducing the gap between release and platform addition to keep content "Fresh."
3.  **Audience Refinement:** Pivoting toward "Adult" content to secure a mature, high-value subscriber base.

---
*Analysis conducted in Python (Pandas/Seaborn/Geopandas)*
