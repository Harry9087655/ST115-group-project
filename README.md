# ST115-group-project
ST115 group project focusing on Guardian's coverage on Global South

## Does the Global South Receive Less Guardian Coverage as Crises Get More Serious?

### I. Research Questions

1. Is there a measurable disparity in Guardian coverage volume between Global South and Western countries, controlling for conflict severity?

2. Do structural features of articles — length and section placement — differ systematically by region?

3. When The Guardian covers Global South crises, whose expertise does it centre, local professionals or Western commentators?

4. Does The Guardian respond to casualty spikes differently depending on region, and has any disparity narrowed or widened over time (2015–2024)?


### II. Motivation and Originality

Media coverage of global crises shapes public awareness and, in turn, political and humanitarian response. If a newspaper's coverage is disproportionately concentrated on Western conflicts, regardless of their relative severity, this has real implications for how its readership understands and prioritises global suffering. The Guardian is a particularly meaningful case study: it has an explicit editorial commitment to international reporting and positions itself as a progressive outlet with global reach. This project tests that claim empirically and quantitatively.


The concept of proximity bias in journalism is well-established in media studies literature: outlets tend to devote more coverage to geographically or culturally proximate events. However, existing work is largely qualitative or limited to specific conflicts. No publicly available analysis applies a severity-controlled, data-driven framework to Guardian coverage across a decade-long window. The originality of this project lies in using ACLED fatality data as a quantitative severity benchmark, allowing us to ask not just "who gets covered?" but "who gets covered relative to how serious their crisis is?" — a meaningfully sharper question.


III. Data Collection and Preliminary Steps


### Main Data Source - Guardian API

We will collect article metadata via the Guardian Open Platform API across 2015 to 2024. For each article we will request: publication date, section name, word count, country and region tags, and pillar. Data will be collected by querying the world

section filtered by country tag, paginating through results programmatically in Python using the requests library. This will produce a structured dataset of several thousand articles with consistent metadata fields.


### Supplementary Data Source - ACLED

We will download the Number of Reported Fatalities by Country-Year CSV directly from acleddata.com. This requires no API, it is a free, publicly available dataset updated regularly. It will serve as our severity proxy, providing total reported conflict fatalities per country per year. We will merge this with our Guardian dataset on country name and year to produce a unified analytical dataset.


### Preliminary Steps

1. *IDA:* Assess missing values in word count and section fields; verify country tag consistency across the Guardian dataset; cross-check ACLED coverage for all countries present in the Guardian data.

2. *Wrangling:* Parse and standardise dates; assign region labels (Global South vs. Western/high-income) to each country; normalise article counts by conflict duration; merge Guardian and ACLED data on country and year.

3. *Core analysis:*

- Choropleth world map of total articles per country; bar chart of the 5 most covered countries to identify outliers

- ANOVA testing on structural features

- Source-voice analysis: Using AI to get which expert give their commentary and use a stacked bar chart for visualisation

- Scatter plot of fatalities (x-axis, log scale) vs. article count (y-axis, log scale), grouped by region — the central analytical plot

- Matched bar chart comparisons of countries with similar fatality totals but different regions

- Boxplots of median article word count by region; section placement breakdown (world vs. politics vs. opinion)

- Time series of monthly article volume per region with ACLED casualty figures overlaid, to measure coverage responsiveness and lag

- Sensitivity check excluding UK-focused articles to verify findings are not driven by domestic reporting volume
