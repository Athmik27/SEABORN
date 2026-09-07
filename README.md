
1. What is Seaborn?
Seaborn is a Python library used for data visualization.
It is built on top of Matplotlib and is especially useful for visualizing Pandas DataFrames.
Seaborn makes it easier to create attractive and statistical graphs.
Common Seaborn graphs
Scatter plot
Line plot
Bar plot
Count plot
Box plot
Violin plot
Strip plot
Swarm plot
Histogram
KDE plot
Heatmap
Pair plot
Cat plot
FacetGrid
2. Basic Seaborn Structure
The basic structure is:
import seaborn as sns
import matplotlib.pyplot as plt
import pandas as pd

df = pd.read_csv("sample.csv")

sns.scatterplot(
    data=df,
    x="Height",
    y="Weight"
)

plt.title("Height vs Weight")

plt.tight_layout()

plt.savefig("scatter.png")
Mental model
Think of Seaborn like this:
Pandas DataFrame
       ↓
Choose Seaborn plot
       ↓
Choose x and y columns
       ↓
Add hue/style/order
       ↓
Customize
       ↓
Save graph
3. Seaborn vs Matplotlib
Matplotlib
Matplotlib gives you more control over individual graph elements.
plt.plot(x, y)
Seaborn
Seaborn makes statistical and DataFrame-based visualization easier.
sns.scatterplot(
    data=df,
    x="Height",
    y="Weight"
)
Simple difference
Matplotlib → More control
Seaborn    → Easier statistical visualization
Seaborn is built on Matplotlib, so they can be used together.
4. Basic Dataset
For many examples, assume we have:
import pandas as pd

df = pd.read_csv("sample.csv")
Suppose our CSV contains:
No
Name
Type1
Type2
Height
Weight
Legendary
Example:
No    Name       Type1    Type2    Height    Weight
1     Bulbasaur  Grass    Poison   0.7       6.9
2     Ivysaur    Grass    Poison   1.0       13.0
3     Venusaur   Grass    Poison   2.0       100.0
5. Import Seaborn
The standard import is:
import seaborn as sns
Usually you also use:
import matplotlib.pyplot as plt
because Seaborn works together with Matplotlib.
6. Setting the Theme
Seaborn provides built-in themes.
Basic theme
sns.set_theme()
Example:
import seaborn as sns
import matplotlib.pyplot as plt

sns.set_theme()

sns.scatterplot(
    data=df,
    x="Height",
    y="Weight"
)

plt.savefig("graph.png")
7. sns.set_style()
Used to change the visual style.
Syntax
sns.set_style("style")
Common styles:
"white"
"dark"
"whitegrid"
"darkgrid"
"ticks"
Example:
sns.set_style("ticks")
8. What are Axis Spines?
Spines are the lines/borders around the plotting area.
Conceptually:
        Top Spine
    ┌───────────────┐
    │               │
Left│    Graph      │Right
Spine              Spine
    │               │
    └───────────────┘
       Bottom Spine
You can remove unnecessary spines using:
sns.despine()
Example:
sns.set_style("ticks")

sns.scatterplot(
    data=df,
    x="Height",
    y="Weight"
)

sns.despine()

plt.savefig("graph.png")
9. Scatter Plot
A scatter plot shows the relationship between two numerical variables.
Syntax
sns.scatterplot(
    data=df,
    x="column1",
    y="column2"
)
Example:
sns.scatterplot(
    data=df,
    x="Height",
    y="Weight"
)

plt.savefig("scatter.png")
10. Scatter Plot with hue
hue separates data into different categories using color.
Example:
sns.scatterplot(
    data=df,
    x="Height",
    y="Weight",
    hue="Type1"
)

plt.savefig("scatter_hue.png")
If Type1 contains:
Grass
Fire
Water
Electric
Seaborn gives different colors to those categories.
Mental model
x     → horizontal variable
y     → vertical variable
hue   → category/color
11. hue
hue is one of the most important Seaborn parameters.
Example:
sns.scatterplot(
    data=df,
    x="Height",
    y="Weight",
    hue="Type1"
)
It tells Seaborn:
"Use this column to divide the data into categories."
12. hue_order
hue_order controls the order of categories in hue.
Example:
sns.scatterplot(
    data=df,
    x="Height",
    y="Weight",
    hue="Type1",
    hue_order=["Fire", "Water", "Grass"]
)
Without hue_order, Seaborn chooses the category order automatically.
Important
hue       → which category to use
hue_order → order of those categories
13. style
style changes the marker shape according to a category.
Example:
sns.scatterplot(
    data=df,
    x="Height",
    y="Weight",
    hue="Type1",
    style="Type2"
)

plt.savefig("style.png")
Mental model:
hue   → color
style → marker shape
14. size
size changes the marker size based on a variable.
Example:
sns.scatterplot(
    data=df,
    x="Height",
    y="Weight",
    size="Weight"
)

plt.savefig("size.png")
Now different values of Weight can have different marker sizes.
15. alpha
alpha controls transparency.
Range:
0 → transparent
1 → fully visible
Example:
sns.scatterplot(
    data=df,
    x="Height",
    y="Weight",
    alpha=0.5
)
Use:
alpha=0.5
rather than:
alpha="0.5"
16. marker
Controls the shape of points.
Example:
sns.scatterplot(
    data=df,
    x="Height",
    y="Weight",
    marker="o"
)
Common markers:
o → circle
s → square
^ → triangle
* → star
x → x
+ → plus
17. edgecolor
Controls the border color of markers.
Example:
sns.scatterplot(
    data=df,
    x="Height",
    y="Weight",
    edgecolor="red"
)
18. linewidth
Controls the thickness of the marker border or line.
Example:
sns.scatterplot(
    data=df,
    x="Height",
    y="Weight",
    linewidth=1
)
19. Line Plot
Used to show trends.
Syntax
sns.lineplot(
    data=df,
    x="column1",
    y="column2"
)
Example:
sns.lineplot(
    data=df,
    x="Height",
    y="Weight"
)

plt.savefig("line.png")
20. Line Plot with hue
sns.lineplot(
    data=df,
    x="Height",
    y="Weight",
    hue="Type1"
)

plt.savefig("line_hue.png")
This creates separate lines according to Type1.
21. Bar Plot
A bar plot compares categories.
Syntax
sns.barplot(
    data=df,
    x="category",
    y="value"
)
Example:
sns.barplot(
    data=df,
    x="Type1",
    y="Weight"
)

plt.savefig("bar.png")
Important
Seaborn's barplot() generally shows an estimated value for each category, commonly the mean, along with an uncertainty interval.
22. countplot
A count plot counts how many observations belong to each category.
Syntax
sns.countplot(
    data=df,
    x="column"
)
Example:
sns.countplot(
    data=df,
    x="Type1"
)

plt.savefig("count.png")
If the data contains:
Grass
Grass
Fire
Water
Grass
the graph counts:
Grass → 3
Fire  → 1
Water → 1
23. countplot with hue
sns.countplot(
    data=df,
    x="Type1",
    hue="Type2"
)

plt.savefig("count_hue.png")
This allows you to compare categories within categories.
24. Box Plot
A box plot shows:
Median
Quartiles
Distribution
Possible outliers
Syntax
sns.boxplot(
    data=df,
    x="category",
    y="value"
)
Example:
sns.boxplot(
    data=df,
    x="Type1",
    y="Weight"
)

plt.savefig("boxplot.png")
25. Box Plot with hue
sns.boxplot(
    data=df,
    x="Type1",
    y="Weight",
    hue="Type2"
)

plt.savefig("box_hue.png")
26. Violin Plot
A violin plot combines ideas from:
Box plot
Distribution/KDE plot
It shows how the data is distributed.
Example:
sns.violinplot(
    data=df,
    x="Type1",
    y="Weight"
)

plt.savefig("violin.png")
27. Strip Plot
A strip plot displays individual observations.
Syntax
sns.stripplot(
    data=df,
    x="category",
    y="value"
)
Example:
sns.stripplot(
    data=df,
    x="Type1",
    y="Weight"
)

plt.savefig("strip.png")
28. Strip Plot with jitter
jitter slightly moves points horizontally to prevent them from overlapping.
Example:
sns.stripplot(
    data=df,
    x="Type1",
    y="Weight",
    jitter=True
)
You can also specify a numeric amount:
jitter=0.2
Mental model
Without jitter:
•
•
•
•
•
With jitter:
  •
•   •
   •
 •    •
It makes individual observations easier to see.
29. Strip Plot with Marker
sns.stripplot(
    data=df,
    x="Type1",
    y="Weight",
    marker="<"
)
30. Strip Plot with Transparency
sns.stripplot(
    data=df,
    x="Type1",
    y="Weight",
    alpha=0.5
)
31. Strip Plot — Important Parameters
sns.stripplot(
    data=df,
    x="Type1",
    y="Weight",
    hue="Type2",
    jitter=True,
    marker="o",
    alpha=0.5,
    edgecolor="red",
    linewidth=1
)
Important parameters:
Parameter	Meaning
data	DataFrame
x	X-axis column
y	Y-axis column
hue	Category/color
jitter	Spread overlapping points
marker	Point shape
alpha	Transparency
edgecolor	Border color
linewidth	Border thickness
32. Swarm Plot
A swarm plot displays individual observations while trying to prevent points from overlapping.
Example:
sns.swarmplot(
    data=df,
    x="Type1",
    y="Weight"
)

plt.savefig("swarm.png")
Difference
stripplot → uses jitter
swarmplot → intelligently positions points
33. Histogram
A histogram shows the distribution of numerical data.
sns.histplot(
    data=df,
    x="Weight"
)

plt.savefig("histogram.png")
34. Histogram with bins
sns.histplot(
    data=df,
    x="Weight",
    bins=10
)
bins controls how the numerical values are grouped.
35. Histogram with hue
sns.histplot(
    data=df,
    x="Weight",
    hue="Type1"
)

plt.savefig("hist_hue.png")
36. KDE Plot
KDE means:
Kernel Density Estimate
It provides a smooth estimate of the distribution of numerical data.
Example:
sns.kdeplot(
    data=df,
    x="Weight"
)

plt.savefig("kde.png")
Mental model
Histogram:
▂ ▅ █ ▇ ▃
KDE:
      /\
    /    \
  /        \
_/          \_
37. KDE with hue
sns.kdeplot(
    data=df,
    x="Weight",
    hue="Type1"
)

plt.savefig("kde_hue.png")
38. Heatmap
A heatmap represents values using different shades/colors.
It is commonly used for:
Correlation matrices
Missing data
Numerical tables
Example:
sns.heatmap(df)

plt.savefig("heatmap.png")
For a correlation matrix:
correlation = df.corr(numeric_only=True)

sns.heatmap(
    correlation
)

plt.savefig("correlation.png")
39. Heatmap with annot
annot=True displays the actual values inside the cells.
sns.heatmap(
    correlation,
    annot=True
)

plt.savefig("correlation_annotated.png")
Example:
┌─────────┬─────────┐
│ 1.00    │ 0.72    │
├─────────┼─────────┤
│ 0.72    │ 1.00    │
└─────────┴─────────┘
40. Heatmap — Important Parameters
sns.heatmap(
    correlation,
    annot=True,
    linewidths=0.5,
    vmin=-1,
    vmax=1
)
Important:
Parameter	Meaning
annot	Show values
linewidths	Cell border thickness
vmin	Minimum color scale
vmax	Maximum color scale
cmap	Color map
41. Pair Plot
A pair plot creates multiple plots showing relationships between numerical columns.
Syntax
sns.pairplot(df)
Example:
sns.pairplot(df)

plt.savefig("pairplot.png")
It can help identify:
Relationships
Correlations
Distributions
42. Pair Plot with hue
sns.pairplot(
    df,
    hue="Type1"
)

plt.savefig("pairplot_hue.png")
This colors observations according to Type1.
43. Pair Plot with Selected Columns
Use vars.
sns.pairplot(
    df,
    vars=["Height", "Weight"],
    hue="Type1"
)

plt.savefig("pairplot_selected.png")
Important
The correct parameter is:
vars
Not:
var_names
Not:
var_namess
44. hue_order in Pair Plot
sns.pairplot(
    df,
    vars=["Height", "Weight"],
    hue="Type1",
    hue_order=["Fire", "Water", "Grass"]
)

plt.savefig("pairplot_order.png")
hue_order controls the order of categorical hue levels.
45. Catplot
catplot() is a figure-level categorical plotting function.
It can create several categorical plots.
Basic example
sns.catplot(
    data=df,
    x="Type1",
    y="Weight"
)

plt.savefig("catplot.png")
46. kind in Catplot
kind decides which type of categorical plot to create.
Examples:
sns.catplot(
    data=df,
    x="Type1",
    y="Weight",
    kind="strip"
)
Other examples:
kind="box"
kind="bar"
kind="violin"
kind="swarm"
kind="point"
Mental model
catplot()
   |
   ├── strip
   ├── box
   ├── bar
   ├── violin
   ├── swarm
   └── point
47. Catplot with hue
sns.catplot(
    data=df,
    x="Type1",
    y="Weight",
    hue="Type2",
    kind="box"
)

plt.savefig("catplot_hue.png")
48. FacetGrid
FacetGrid is used to create multiple plots based on categories.
Example:
g = sns.FacetGrid(
    df,
    col="Type1"
)
This creates separate panels for each Type1.
49. FacetGrid with map
Example:
g = sns.FacetGrid(df)

g.map(
    plt.scatter,
    "Height",
    "Weight"
)

plt.savefig("facetgrid.png")
This applies the plotting function to each facet.
50. FacetGrid with map_dataframe
A useful modern approach is:
g = sns.FacetGrid(
    df,
    col="Type1"
)

g.map_dataframe(
    sns.scatterplot,
    x="Height",
    y="Weight"
)

plt.savefig("facetgrid.png")
Difference
map()
→ generally works with positional data

map_dataframe()
→ passes DataFrame subsets to plotting functions
51. FacetGrid — col
col creates separate columns for categories.
g = sns.FacetGrid(
    df,
    col="Type1"
)
Conceptually:
┌──────────┬──────────┬──────────┐
│  Grass   │   Fire   │  Water   │
│  graph   │  graph   │  graph   │
└──────────┴──────────┴──────────┘
52. FacetGrid — row
row creates separate rows.
g = sns.FacetGrid(
    df,
    row="Type1"
)
53. FacetGrid — col_wrap
If there are many categories:
g = sns.FacetGrid(
    df,
    col="Type1",
    col_wrap=3
)
This wraps columns into multiple rows.
54. Figure-Level vs Axes-Level Functions
This is an important Seaborn concept.
Axes-level functions
Examples:
sns.scatterplot()
sns.lineplot()
sns.barplot()
sns.boxplot()
sns.stripplot()
sns.histplot()
They generally draw on one Matplotlib Axes.
Figure-level functions
Examples:
sns.relplot()
sns.catplot()
sns.displot()
sns.pairplot()
sns.jointplot()
They manage an entire figure and can create multiple facets.
55. order
order controls the order of categorical values on an axis.
Example:
sns.boxplot(
    data=df,
    x="Type1",
    y="Weight",
    order=["Fire", "Water", "Grass"]
)

plt.savefig("ordered_box.png")
Difference
order      → category order on axis
hue_order  → category order inside hue
56. palette
palette controls the colors used for categorical groups.
Example:
sns.boxplot(
    data=df,
    x="Type1",
    y="Weight",
    hue="Type1",
    palette="Set2"
)

plt.savefig("palette.png")
Common palettes include:
"Set1"
"Set2"
"Set3"
"deep"
"muted"
"bright"
"pastel"
"dark"
"colorblind"
57. height and aspect
These are commonly used with figure-level functions.
Example:
sns.catplot(
    data=df,
    x="Type1",
    y="Weight",
    height=5,
    aspect=1.5
)

plt.savefig("catplot_size.png")
Meaning
height → figure height
aspect → width / height ratio
58. col and row in Figure-Level Functions
Example:
sns.catplot(
    data=df,
    x="Type1",
    y="Weight",
    col="Type2",
    kind="box"
)
This creates separate plots for each Type2.
You can also use:
row="Type2"
or both:
row="Type2",
col="Legendary"
59. Relational Plots
Seaborn provides relational plotting functions.
Scatter
sns.scatterplot()
Line
sns.lineplot()
Figure-level relational plot
sns.relplot()
Example:
sns.relplot(
    data=df,
    x="Height",
    y="Weight",
    hue="Type1"
)

plt.savefig("relplot.png")
60. relplot
relplot() can create:
Scatter plots
Line plots
Example:
sns.relplot(
    data=df,
    x="Height",
    y="Weight",
    hue="Type1",
    kind="scatter"
)
Line:
sns.relplot(
    data=df,
    x="Height",
    y="Weight",
    hue="Type1",
    kind="line"
)
61. Distribution Plots
Seaborn provides several ways to visualize distributions.
Important functions:
sns.histplot()
sns.kdeplot()
sns.displot()
histplot
sns.histplot(
    data=df,
    x="Weight"
)
kdeplot
sns.kdeplot(
    data=df,
    x="Weight"
)
displot
sns.displot(
    data=df,
    x="Weight"
)
62. displot
displot() is a figure-level distribution plot.
Example:
sns.displot(
    data=df,
    x="Weight",
    kind="hist"
)

plt.savefig("displot.png")
KDE:
sns.displot(
    data=df,
    x="Weight",
    kind="kde"
)
63. Important Seaborn Parameters
These parameters are extremely important:
data
x
y
hue
hue_order
order
palette
style
size
alpha
marker
jitter
linewidth
edgecolor
kind
col
row
col_wrap
height
aspect
64. Meaning of Important Parameters
Parameter	Meaning
data	DataFrame
x	X-axis variable
y	Y-axis variable
hue	Color/category
hue_order	Order of hue categories
order	Order of x/y categories
palette	Color palette
style	Marker/line style
size	Size based on variable
alpha	Transparency
marker	Marker shape
jitter	Spread overlapping points
linewidth	Line/border thickness
edgecolor	Border color
kind	Plot type
col	Facet columns
row	Facet rows
col_wrap	Number of facet columns before wrapping
height	Figure height
aspect	Width/height ratio
65. Seaborn + Pandas
This is one of the most common combinations in Data Science.
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

df = pd.read_csv("sample.csv")

sns.boxplot(
    data=df,
    x="Type1",
    y="Weight"
)

plt.title("Weight by Type")

plt.tight_layout()

plt.savefig("weight.png")
66. Seaborn + Matplotlib
Seaborn and Matplotlib can be combined.
Example:
sns.scatterplot(
    data=df,
    x="Height",
    y="Weight",
    hue="Type1"
)

plt.title("Height vs Weight")

plt.xlabel("Height")
plt.ylabel("Weight")

plt.grid()

plt.tight_layout()

plt.savefig("graph.png")
Seaborn creates the graph and Matplotlib can further customize it.
67. Common Seaborn Errors
Error 1 — Wrong column name
If your DataFrame contains:
Height
Weight
but you write:
x="height"
you may get an error because column names are case-sensitive.
Correct:
x="Height"
68. Error 2 — Wrong pairplot parameter
❌
sns.pairplot(
    df,
    var_names=["Height", "Weight"]
)
Use:
sns.pairplot(
    df,
    vars=["Height", "Weight"]
)
The parameter is:
vars
69. Error 3 — Incorrect hue
If your DataFrame does not contain:
Type1
then:
hue="Type1"
will produce an error.
Always check:
print(df.columns)
70. Error 4 — Incorrect hue_order
hue_order should contain valid categories from the hue variable.
For:
hue="Type1"
the values in hue_order should exist in Type1.
Example:
hue_order=["Fire", "Water", "Grass"]
71. Error 5 — Excessive Jitter
This:
jitter=3
may spread points too far depending on the scale of your categorical axis.
Usually start with:
jitter=True
or:
jitter=0.2
72. Error 6 — Wrong Alpha Type
Prefer:
alpha=0.5
instead of:
alpha="0.5"
73. Error 7 — Dataset Loading
If you use:
sns.load_dataset("sample.csv")
that is not how you normally load your own CSV file.
Use Pandas:
df = pd.read_csv("sample.csv")
Then:
sns.scatterplot(
    data=df,
    x="Height",
    y="Weight"
)
74. Important Seaborn Plot Selection
Relationship
     |
     ├── scatterplot()
     └── lineplot()

Categorical
     |
     ├── barplot()
     ├── countplot()
     ├── boxplot()
     ├── violinplot()
     ├── stripplot()
     └── swarmplot()

Distribution
     |
     ├── histplot()
     ├── kdeplot()
     └── displot()

Matrix
     |
     └── heatmap()

Multiple Variables
     |
     └── pairplot()

Multiple Panels
     |
     └── FacetGrid
75. When to Use Which Plot?
Plot	Main Purpose
scatterplot()	Relationship between two numerical variables
lineplot()	Trend
barplot()	Compare categories
countplot()	Count categories
boxplot()	Distribution + outliers
violinplot()	Distribution shape
stripplot()	Individual observations
swarmplot()	Individual observations without overlap
histplot()	Numerical distribution
kdeplot()	Smooth distribution
heatmap()	Matrix/correlation
pairplot()	Relationships among multiple variables
catplot()	Multiple categorical plot types
FacetGrid()	Multiple panels
76. Most Important Seaborn Concepts
You should understand these particularly well:
1. data
data=df
Tells Seaborn which DataFrame to use.
2. x
x="Height"
Selects the X-axis column.
3. y
y="Weight"
Selects the Y-axis column.
4. hue
hue="Type1"
Adds categories using color.
5. hue_order
hue_order=["Fire", "Water", "Grass"]
Controls hue category order.
6. order
order=["Fire", "Water", "Grass"]
Controls categorical axis order.
77. Complete Scatter Plot Example
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

df = pd.read_csv("sample.csv")

sns.set_style("ticks")

sns.scatterplot(
    data=df,
    x="Height",
    y="Weight",
    hue="Type1",
    style="Type2",
    alpha=0.7
)

plt.title("Height vs Weight")
plt.xlabel("Height")
plt.ylabel("Weight")

plt.tight_layout()

plt.savefig(
    "height_weight.png",
    bbox_inches="tight"
)
78. Complete Box Plot Example
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

df = pd.read_csv("sample.csv")

sns.set_style("whitegrid")

sns.boxplot(
    data=df,
    x="Type1",
    y="Weight",
    hue="Type1"
)

plt.title("Weight Distribution by Type")
plt.xlabel("Type")
plt.ylabel("Weight")

plt.tight_layout()

plt.savefig(
    "boxplot.png",
    bbox_inches="tight"
)
79. Complete Pair Plot Example
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

df = pd.read_csv("sample.csv")

sns.pairplot(
    df,
    vars=["Height", "Weight"],
    hue="Type1",
    hue_order=["Fire", "Water", "Grass"]
)

plt.savefig(
    "pairplot.png",
    bbox_inches="tight"
)
80. Complete FacetGrid Example
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

df = pd.read_csv("sample.csv")

g = sns.FacetGrid(
    df,
    col="Type1"
)

g.map_dataframe(
    sns.scatterplot,
    x="Height",
    y="Weight"
)

plt.savefig(
    "facetgrid.png",
    bbox_inches="tight"
)
81. Seaborn Cheat Sheet
Import
import seaborn as sns
Theme
sns.set_theme()
Style
sns.set_style("ticks")
Remove spines
sns.despine()
Scatter Plot
sns.scatterplot(
    data=df,
    x="Height",
    y="Weight"
)
Line Plot
sns.lineplot(
    data=df,
    x="Height",
    y="Weight"
)
Bar Plot
sns.barplot(
    data=df,
    x="Type1",
    y="Weight"
)
Count Plot
sns.countplot(
    data=df,
    x="Type1"
)
Box Plot
sns.boxplot(
    data=df,
    x="Type1",
    y="Weight"
)
Violin Plot
sns.violinplot(
    data=df,
    x="Type1",
    y="Weight"
)
Strip Plot
sns.stripplot(
    data=df,
    x="Type1",
    y="Weight"
)
Swarm Plot
sns.swarmplot(
    data=df,
    x="Type1",
    y="Weight"
)
Histogram
sns.histplot(
    data=df,
    x="Weight"
)
KDE
sns.kdeplot(
    data=df,
    x="Weight"
)
Heatmap
sns.heatmap(
    data
)
Pair Plot
sns.pairplot(df)
Cat Plot
sns.catplot(
    data=df,
    x="Type1",
    y="Weight"
)
Rel Plot
sns.relplot(
    data=df,
    x="Height",
    y="Weight"
)
Distribution Plot
sns.displot(
    data=df,
    x="Weight"
)
FacetGrid
g = sns.FacetGrid(
    df,
    col="Type1"
)
82. Parameter Cheat Sheet
data
DataFrame being used.
x
X-axis column.
y
Y-axis column.
hue
Category represented using color.
hue_order
Order of hue categories.
order
Order of categorical axis values.
style
Changes marker/line style based on a variable.
size
Changes size based on a variable.
palette
Controls categorical colors.
alpha
Controls transparency.
marker
Controls marker shape.
jitter
Spreads overlapping categorical points.
kind
Selects plot type for figure-level functions.
row
Creates facets by rows.
col
Creates facets by columns.
col_wrap
Controls number of columns before wrapping.
height
Controls figure height.
aspect
Controls width/height ratio.
83. Matplotlib Functions Commonly Used with Seaborn
Seaborn handles the main visualization, while Matplotlib can customize it.
plt.title()
plt.xlabel()
plt.ylabel()

plt.xlim()
plt.ylim()

plt.xticks()
plt.yticks()

plt.grid()

plt.tight_layout()

plt.savefig()
plt.show()
Example:
sns.boxplot(
    data=df,
    x="Type1",
    y="Weight"
)

plt.title("Weight by Type")
plt.xlabel("Pokemon Type")
plt.ylabel("Weight")

plt.tight_layout()

plt.savefig("graph.png")
84. Matplotlib vs Seaborn — Quick Comparison
Feature	Matplotlib	Seaborn
Basic plotting	Excellent	Excellent
Customization	Very high	High
DataFrame support	Good	Excellent
Statistical plots	Basic	Excellent
Attractive defaults	Less automatic	More automatic
Heatmap	Possible	Easy
Pair plot	No direct equivalent	Easy
Faceting	More manual	Easy
Built on	Base plotting library	Matplotlib
85. Placement Priority
MUST KNOW ⭐⭐⭐
Learn these first:
sns.scatterplot()
sns.lineplot()

sns.barplot()
sns.countplot()

sns.boxplot()
sns.violinplot()

sns.stripplot()

sns.histplot()
sns.kdeplot()

sns.heatmap()
sns.pairplot()

sns.catplot()
sns.FacetGrid()
And understand:
data
x
y
hue
hue_order
order
palette
alpha
jitter
marker
style
size
kind



                      
 Final Quick Revision
Import
import seaborn as sns
import matplotlib.pyplot as plt
Load Data
df = pd.read_csv("sample.csv")
Scatter
sns.scatterplot(
    data=df,
    x="Height",
    y="Weight"
)
Hue
hue="Type1"
Hue Order
hue_order=["Fire", "Water", "Grass"]
Line
sns.lineplot(
    data=df,
    x="Height",
    y="Weight"
)
Bar
sns.barplot(
    data=df,
    x="Type1",
    y="Weight"
)
Count
sns.countplot(
    data=df,
    x="Type1"
)
Box
sns.boxplot(
    data=df,
    x="Type1",
    y="Weight"
)
Violin
sns.violinplot(
    data=df,
    x="Type1",
    y="Weight"
)
Strip
sns.stripplot(
    data=df,
    x="Type1",
    y="Weight",
    jitter=True
)
Histogram
sns.histplot(
    data=df,
    x="Weight"
)
KDE
sns.kdeplot(
    data=df,
    x="Weight"
)
Heatmap
sns.heatmap(
    correlation,
    annot=True
)
Pairplot
sns.pairplot(
    df,
    vars=["Height", "Weight"],
    hue="Type1"
)
Catplot
sns.catplot(
    data=df,
    x="Type1",
    y="Weight",
    kind="box"
)
FacetGrid
g = sns.FacetGrid(
    df,
    col="Type1"
)
Style
sns.set_style("ticks")
Remove Spines
sns.despine()
Save
plt.savefig("graph.png")
 Final Seaborn Checklist
Before moving to advanced visualization, make sure you can explain and use:

sns.scatterplot()

sns.lineplot()

sns.barplot()

sns.countplot()

sns.boxplot()

sns.violinplot()

sns.stripplot()

sns.swarmplot()

sns.histplot()

sns.kdeplot()

sns.heatmap()

sns.pairplot()

sns.catplot()

sns.relplot()

sns.displot()

sns.FacetGrid()

hue

hue_order

order

palette

style

size

alpha

marker

jitter

linewidth

edgecolor

kind

row

col

col_wrap

height

aspect

sns.set_style()

sns.set_theme()

sns.despine()

Seaborn + Pandas

Seaborn + Matplotlib
