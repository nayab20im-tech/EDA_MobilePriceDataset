# 📱 Mobile Price Prediction - Complete EDA

## **1. Introduction & Approach**
This project performs an extensive Exploratory Data Analysis (EDA) on a dataset of mobile phone specifications. The goal is to identify the key features (such as RAM, Storage, and Camera quality) that drive market pricing. The analysis follows a structured approach:
1.  **Data Cleaning**: Preparing the dataset for analysis.
2.  **Univariate Analysis**: Understanding individual feature distributions.
3.  **Bivariate Analysis**: Exploring relationships between features and Price.
4.  **Multivariate Analysis**: Examining complex interactions and Principal Component Analysis (PCA).

---

## **2. Data Cleaning**
Before visualizing, we ensured the data was clean and optimized:
* **Irrelevant Columns**: Dropped `Model URL` and `Image URL` as they do not affect prediction.
* **Missing Values**: Confirmed the dataset has **0 missing values**.
* **Duplicates**: Verified there are **0 duplicate rows**.
* **Data Types**: Converted categorical columns (like `Brand`, `UI`, `5G_Band`) to the `category` datatype to save memory and speed up processing.

---

## **3. Univariate Analysis**
We analyzed the distribution of **9 Numerical** and **10 Categorical** features.

### **Numerical Columns (Distributions & Outliers)**
We examined the histograms and boxplots for all numerical specs to check for skewness and outliers.

#### **1. Price (Target Variable)**
* **Observation**: Most phones are low-to-mid-priced. The distribution is right-skewed, meaning there are fewer ultra-premium phones.
![Price Histogram](images/1.png)
![Price Boxplot](images/2.png)

#### **2. Weight (grams)**
* **Observation**: Most phones weigh between 180g and 210g.
![Weight Histogram](images/3.png)
![Weight Boxplot](images/4.png)

#### **3. Refresh Rate (Hz)**
* **Observation**: Higher refresh rates (90Hz, 120Hz) are becoming common, but standard 60Hz screens still exist.
![Refresh Rate Histogram](images/5.png)

#### **4. Storage (GB)**
* **Observation**: 128 GB and 256 GB are the most common storage options.
![Storage Histogram](images/6.png)

#### **5. RAM (GB)**
* **Observation**: 8 GB and 12 GB are the market standards for multitasking.
![RAM Histogram](images/7.png)

#### **6. Main Camera (MP)**
* **Observation**: 50 MP and 108 MP cameras dominate the market.
![Main Camera Histogram](images/8.png)

#### **7. Front Camera (MP)**
* **Observation**: Most front cameras are in the medium resolution range.
![Front Camera Histogram](images/9.png)

#### **8. Battery Capacity (mAh)**
* **Observation**: There is a massive concentration around **5000 mAh**, which has become the industry standard.
![Battery Histogram](images/10.png)

#### **9. OS Distribution**
* **Observation**: Android 11 is the most frequent OS in this specific dataset.
![OS Bar Chart](images/11.png)

---

### **Categorical Columns (Count Plots)**
We visualized the frequency of different categorical features.

#### **Availability & Brands**
* **Category**: Most phones are listed as "Available".
* **Brand**: A few major brands contribute the majority of models (Market Dominance).
![Category Distribution](images/12.png)
![Brand Distribution](images/13.png)

#### **Interface & Hardware Specs**
* **UI**: Specific skins like MIUI and OneUI appear frequently.
* **GPU**: Adreno GPUs are the most common.
* **Display**: AMOLED screens are widely available, outnumbering LCDs in this dataset.
![UI Distribution](images/14.png)
![GPU Distribution](images/15.png)
![AMOLED Distribution](images/16.png)

#### **Connectivity & Features**
* **NFC**: Most phones support NFC.
* **5G Band**: A large majority of modern phones are 5G capable.
* **4K Video**: Many phones support 4K video recording.
* **Type-C**: Almost universally adopted.
![NFC Distribution](images/17.png)
![5G Distribution](images/18.png)
![4K Support Distribution](images/19.png)
![Type-C Distribution](images/20.png)
![Model Title Frequency](images/21.png)

---

### **Key Questions from Univariate Analysis**
* **Q1: Price Dominance?** Most phones fall in the 30k–90k PKR range.
![Q1 Price Plot](images/22.png)
* **Q2: Brand Leaders?** A few top brands release the most models.
![Q2 Brand Plot](images/23.png)
* **Q3: Screen Quality?** AMOLED is more common than non-AMOLED.
![Q3 Screen Plot](images/24.png)
* **Q4: RAM Standards?** Most devices cluster between 6–12 GB RAM.
![Q4 RAM Plot](images/25.png)
* **Q5: Battery Standards?** 5000 mAh is the clear standard.
![Q5 Battery Plot](images/26.png)

---

## **4. Bivariate Analysis**
Here, we explored how features relate to **Price**.

### **Numerical Features vs. Price**
* **RAM vs Price**: Strong positive correlation. Higher RAM = Higher Price.
![RAM vs Price Scatter](images/27.png)
* **Storage vs Price**: Clear tiers; 256GB/512GB phones cost significantly more.
![Storage vs Price Scatter](images/28.png)
* **Battery vs Price**: Weak correlation. 5000mAh batteries are found in both cheap and expensive phones.
![Battery vs Price Scatter](images/29.png)

### **Categorical Features vs. Price**
* **Brand Pricing**: Some brands have a much higher median price (Premium positioning) than others.
![Price by Brand Boxplot](images/30.png)

### **Price Range Analysis (Low / Mid / High / Premium)**
We binned prices into 4 categories to see clear trends.
1.  **Model Count**: Most phones are Low/Mid range.
    ![Models by Price Range](images/31.png)
2.  **RAM by Range**: Low-end phones have 4-6GB; Premium have 12GB+.
    ![RAM by Price Range](images/32.png)
3.  **Camera by Range**: Camera quality steps up linearly with price.
    ![Camera by Price Range](images/33.png)
4.  **AMOLED by Range**: Low-end phones rarely have AMOLED; Premium phones almost always do.
    ![AMOLED by Price Range](images/34.png)

### **Feature vs. Feature Interaction**
* **RAM vs Storage**: Higher RAM phones almost always have higher storage.
![RAM vs Storage](images/35.png)
* **Battery vs Weight**: Larger batteries slightly increase phone weight.
![Battery vs Weight](images/36.png)

### **Key Questions from Bivariate Analysis**
* **Q1: Is High RAM always expensive?** Generally yes, 12GB+ is rare in low tiers.
![Q1 Bivariate](images/37.png)
* **Q2: Best Camera Segment?** High and Premium segments offer the biggest camera upgrades.
![Q2 Bivariate](images/38.png)
* **Q3: Brand Strategy?** Some brands stick to low price ranges, others span the full spectrum.
![Q3 Bivariate](images/39.png)

---

## **5. Multivariate Analysis**
We combined multiple variables to find deeper patterns.

### **Correlations & Interactions**
* **Correlation Matrix**: Price is most strongly correlated with **RAM, Storage, and Camera MP**.
![Correlation Heatmap](images/40.png)
* **Pairplot**: Shows clustering of "Premium" phones (orange/red points) in the top-right of scatter plots (High Specs).
![Pairplot](images/41.png)

### **Faceted Analysis**
* **RAM vs Storage by Price**: The "Low" price facet shows a tight cluster of low specs; "Premium" shows high specs.
![Faceted Scatter](images/42.png)
* **Price vs Camera Trend**: In the Low segment, better cameras don't raise the price much. In Premium, they do.
![Faceted Regression](images/43.png)

### **Custom Insights**
* **AMOLED & Brand**: High-end brands use AMOLED almost exclusively in their top tiers.
![Brand AMOLED Heatmap](images/44.png)
* **Median Price Impact**: Phones with AMOLED cost significantly more on average.
![Median Price Heatmap](images/45.png)
* **Violin Plot**: Shows the density of Camera MP across price ranges, split by Screen Type.
![Violin Plot](images/46.png)

### **PCA (Principal Component Analysis)**
* **Clustering**: We reduced the dimensions (RAM, Storage, Camera, Battery) into two components (PC1, PC2).
* **Result**: The plot shows clear separation. **Premium phones** cluster on the right, while **Low-range phones** cluster on the bottom-left.
![PCA Cluster Plot](images/47.png)

### **Key Questions from Multivariate Analysis**
* **Q1: Feature Combination?** (Pairplot view)
![Q1 Multivariate](images/48.png)
* **Q2: Screen & Camera Link?** Phones with premium screens usually bundle premium cameras.
![Q2 Multivariate](images/49.png)
* **Q3: The "Premium Package"?** (PCA View) The data confirms that Premium status is a combination of High RAM + High Storage + Great Camera.
![Q3 Multivariate / Final PCA](images/50.png)

---

## **6. Conclusion**
From the full analysis, we determined that **RAM, Internal Storage, and Main Camera MP** are the three strongest predictors of mobile phone prices.
* **Premium Phones**: defined by the "Total Package" (High RAM + AMOLED + High MP Camera).
* **Battery Life**: Increases with price but is not a strong differentiator (cheap phones also have big batteries).
* **Display**: AMOLED is a key indicator of a higher price tier.

---
*Notebook Analysis by Nayab Nasir.*
