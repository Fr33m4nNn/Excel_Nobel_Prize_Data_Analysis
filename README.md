# Nobel Prize Data Analysis

## 🌍 Introduction
This Nobel Prize analytics dashboard was developed to uncover key insights into award distribution, laureate achievements, and institutional affiliations across more than a century of Nobel history. It highlights patterns such as:

Median prize values (adjusted) by category

- **The youngest and oldest recipients by awarded age**

- **Most affiliated universities and repeat laureates**

- **Comparisons between individual and organizational achievements**

- **The dashboard is fully interactive, with slicers for gender, country, continent, and recipient type, enabling dynamic filtering and deeper analysis.**

🧠 This project was primarily focused on mastering **Power Pivot**, **Power Query**, and **DAX** within Excel. It involved advanced data cleaning, transformation, and modeling techniques to build calculated columns, measures, and responsive visuals.

🔗 Data Source: [All Nobel Prize winners from 1901-2025.03 on Kaggle](https://www.kaggle.com/datasets/jehanbhathena/all-nobel-prize-winners-from-1901-2024)

### Questions to Analyze

To explore the trends and patterns within Nobel Prize history, I asked the following questions:

1. **How do median prize amounts vary across Nobel categories?**
2. **What’s the timeline of Nobel Prize distribution over the years?**
3. **Who are the youngest and oldest laureates across different categories?**
4. **What are the most affiliated universities and institutions with laureates?**
5. **Which organizations and individuals have received multiple Nobel Prizes?**

### Excel Skills Used

- **📊 Pivot Tables**
- **📈 Pivot Charts**
- **🧮 DAX (Data Analysis Expressions)**
- **🔍 Power Query**
- **💪 Power Pivot**

### All Nobel Prize winners from 1901-2025 Dataset (2025-03-25)

This dataset compiles historical records of Nobel Prize awards. It contains data on the award year, prize category, and prize amounts (both original and inflation-adjusted). The dataset includes detailed information on laureates such as their names, birth and death details, and professional affiliations. For organizational award recipients, it also provides founding information and native names. This resource supports analyses of trends in Nobel Prize history and profiles of both individual and institutional awardees.


### 🔍 Skill: Power Query (ETL)

#### 📥 Extract

- I first used Power Query to extract the original data (`nobel.csv`) and create two queries:
    - 🗃️ First one with all the nobel prize laureates information.
    - 🔧 The second listing the affiliated institutions for each nobel ID.

#### 🔄 Transform

- Then, I transformed each query by changing column types, removing unnecessary columns, cleaning incomplete birth dates, extracting founding years for organizations, filling missing values with "Organization", and removing rows with errors or null IDs.
    - 📊 nobel

        ![1](/images/1.png)

    - 🛠️ nobel_affiliation

        ![2](/images/2.png)

#### 🔗 Load

- Finally, I loaded both transformed queries into the workbook, setting the foundation for my subsequent analysis.
    - 📊 nobel

        ![3](/images/3.png)

    - 🛠️ nobel_affiliation

        ![4](/images/4.png)


### 🧮 Skills: PivotTables & DAX

#### 📈Pivot Table

- 🔢 I created a PivotTables using the Data Model I created with Power Pivot.

#### 🧮 DAX

- 📊 I added new measures to calculate the median prize and median prize adjusted awarded to laureates.

```
  Median Prize := MEDIAN(nobel[prizeAmount])
```

- 🧮 I formatted the `dateAwarded` column to remove timestamps

```
	= FORMAT(nobel[dateAwarded], "yyyy-mm-dd")
```
- 🧮 then used the `awardYear` column to fill in missing dates, ensuring every laureate had a complete award date.

```
=IF(
ISBLANK([dateAwarded]),
DATE([awardYear], 1, 1),
[dateAwarded]
)
```

### 🔧 Skill: Power Pivot

#### 💪 Power Pivot

- 🔗 I created a data model by integrating the `nobel` and `nobel_affiliation` tables into one model.
- 🧹 Since I had already cleaned the data using Power Query; Power Pivot created a relationship between these two tables.

#### 🔗 Data Model

- I created a relationship between my two tables using the `nobel_id` column.

    ![5](/images/5.png)

#### 📃 Power Pivot Menu

- The Power Pivot menu was used to refine my data model and makes it easy to create measures.

    ![6](/images/6.png)



## 1️⃣ How do median prize amounts vary across Nobel categories?

#### 💡 Insights


- 💵 Economic Sciences has the highest median prize value, both in original and inflation-adjusted amounts, followed by Peace and Physics.

- 📉 Literature consistently receives the lowest median prize, even after adjusting for inflation.

- 💰 Adjusted prize values highlight that all categories have experienced significant value erosion over time, especially visible in fields like Chemistry and Literature.

![1_1](/images/1_1.png)

#### 🤔 So What

-These patterns reveal historical funding priorities and may reflect how different fields are valued economically or politically. Adjusted values also underscore the importance of context when comparing award amounts across decades.

## 2️⃣ What’s the timeline of Nobel Prize distribution over the years?



## 3️⃣ Who are the youngest and oldest laureates across different categories?



## 4️⃣ What are the most affiliated universities and institutions with laureates?



## 5️⃣ Which organizations and individuals have received multiple Nobel Prizes?




## Conclusion

