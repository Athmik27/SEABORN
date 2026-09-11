#  Seaborn Module

Seaborn is a Python library used for **statistical data visualization**.

It works closely with **Pandas and Matplotlib**.

```python
import seaborn as sns
import matplotlib.pyplot as plt
import pandas as pd
```

---

# 1. Load Dataset

```python
df = pd.read_csv("sample.csv")
```

---

# 2. Basic Plot Structure

Most Seaborn plots use:

```python
sns.plot_function(
    x="column",
    y="column",
    data=df
)
```

Example:

```python
sns.scatterplot(
    x="Height",
    y="Weight",
    data=df
)
```

---

# 3. Scatter Plot

Used to show the **relationship between numerical variables**.

```python
sns.scatterplot(
    x="Height",
    y="Weight",
    data=df
)
```

With category:

```python
sns.scatterplot(
    x="Height",
    y="Weight",
    hue="Type1",
    data=df
)
```

### `hue`

```python
hue="Type1"
```

Uses a column to **differentiate data by color/category**.

---

# 4. Line Plot

```python
sns.lineplot(
    x="Height",
    y="Weight",
    data=df
)
```

---

# 5. Bar Plot

```python
sns.barplot(
    x="Type1",
    y="Weight",
    data=df
)
```

Useful for comparing categories.

---

# 6. Count Plot

Counts how many observations belong to each category.

```python
sns.countplot(
    x="Type1",
    data=df
)
```

---

# 7. Box Plot

Used to understand:

* Median
* Spread
* Quartiles
* Outliers

```python
sns.boxplot(
    x="Type1",
    y="Weight",
    data=df
)
```

---

# 8. Violin Plot

Shows distribution and density.

```python
sns.violinplot(
    x="Type1",
    y="Weight",
    data=df
)
```

---

# 9. Strip Plot

Shows individual data points.

```python
sns.stripplot(
    x="Type1",
    y="Weight",
    data=df
)
```

With category:

```python
sns.stripplot(
    x="Type1",
    y="Weight",
    hue="Type2",
    data=df
)
```

---

# 10. Histogram

Shows distribution of numerical data.

```python
sns.histplot(
    data=df,
    x="Weight"
)
```

Add KDE:

```python
sns.histplot(
    data=df,
    x="Weight",
    kde=True
)
```

---

# 11. KDE Plot

Shows a smooth estimate of a distribution.

```python
sns.kdeplot(
    data=df,
    x="Weight"
)
```

---

# 12. Pairplot

Creates relationships between multiple numerical columns.

```python
sns.pairplot(df)
```

Using selected columns:

```python
sns.pairplot(
    df[["Height", "Weight"]]
)
```

Using `hue`:

```python
sns.pairplot(
    df,
    hue="Type1"
)
```

---

# 13. Heatmap

Used to visualize matrix/correlation data.

```python
sns.heatmap(df.corr(numeric_only=True))
```

With values displayed:

```python
sns.heatmap(
    df.corr(numeric_only=True),
    annot=True
)
```

---

# 14. Catplot

Used to create categorical plots.

```python
sns.catplot(
    x="Type1",
    y="Weight",
    data=df
)
```

Change plot type:

```python
sns.catplot(
    x="Type1",
    y="Weight",
    kind="box",
    data=df
)
```

Common `kind`:

```text
strip
swarm
box
violin
boxen
bar
point
count
```

---

# 15. FacetGrid

Used to create **multiple plots based on categories**.

```python
g = sns.FacetGrid(df, col="Type1")
g.map(sns.scatterplot, "Height", "Weight")
```

Basic idea:

```text
FacetGrid → creates multiple panels
col       → creates columns
row       → creates rows
hue       → separates categories
```

---

# 16. Styling

```python
sns.set_style("whitegrid")
```

Common styles:

```text
white
dark
whitegrid
darkgrid
ticks
```

---

# 17. Palette

Controls the color palette.

```python
sns.boxplot(
    x="Type1",
    y="Weight",
    data=df,
    palette="Set2"
)
```

---

# 18. `hue_order`

Controls the order of categories used by `hue`.

```python
sns.scatterplot(
    x="Height",
    y="Weight",
    hue="Type1",
    hue_order=["Fire", "Water"],
    data=df
)
```

---

# 19. Common Parameters

```text
x           → X-axis column
y           → Y-axis column
data        → DataFrame
hue         → Separate by category
style       → Different marker/style by category
size        → Change marker size based on column
palette     → Color palette
alpha       → Transparency
marker      → Marker style
order       → Category order
hue_order   → Hue category order
kind        → Type of plot
```

---

# 20. Show Plot

```python
plt.show()
```

Complete example:

```python
sns.scatterplot(
    x="Height",
    y="Weight",
    hue="Type1",
    data=df
)

plt.title("Height vs Weight")
plt.show()
```

---

# 21. Save Plot

```python
plt.savefig("plot.png")
```

Better:

```python
plt.savefig(
    "plot.png",
    dpi=300,
    bbox_inches="tight"
)
```

---

# 22. Most Important Seaborn Functions

| Function            | Use                    |
| ------------------- | ---------------------- |
| `sns.scatterplot()` | Relationship           |
| `sns.lineplot()`    | Trend                  |
| `sns.barplot()`     | Category comparison    |
| `sns.countplot()`   | Count categories       |
| `sns.boxplot()`     | Distribution/outliers  |
| `sns.violinplot()`  | Distribution + density |
| `sns.stripplot()`   | Individual points      |
| `sns.histplot()`    | Distribution           |
| `sns.kdeplot()`     | Density                |
| `sns.pairplot()`    | Multiple relationships |
| `sns.heatmap()`     | Matrix/correlation     |
| `sns.catplot()`     | Categorical plots      |
| `sns.FacetGrid()`   | Multiple panels        |
| `sns.set_style()`   | Plot style             |

---

# CHEAT SHEET

```python
import seaborn as sns
import matplotlib.pyplot as plt

sns.scatterplot(x="Height", y="Weight", data=df)

sns.lineplot(x="Height", y="Weight", data=df)

sns.barplot(x="Type1", y="Weight", data=df)

sns.countplot(x="Type1", data=df)

sns.boxplot(x="Type1", y="Weight", data=df)

sns.violinplot(x="Type1", y="Weight", data=df)

sns.stripplot(x="Type1", y="Weight", data=df)

sns.histplot(data=df, x="Weight")

sns.kdeplot(data=df, x="Weight")

sns.pairplot(df, hue="Type1")

sns.heatmap(df.corr(numeric_only=True), annot=True)

sns.catplot(x="Type1", y="Weight", data=df)

g = sns.FacetGrid(df, col="Type1")
g.map(sns.scatterplot, "Height", "Weight")

sns.set_style("whitegrid")

plt.title("Title")
plt.show()
plt.savefig("plot.png")
```


