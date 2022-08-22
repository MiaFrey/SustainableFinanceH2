# Sustainable Finance - Homework 2
## Introduction
The objectives are the following:

- Evaluate the (weighted average) carbon intensity of a business-as-usual (BAU) portfolio
- Build a decarbonized portfolios of stocks based on the mean-variance criterion (efficient frontier)
- Evaluate the relative performance of BAU and decarbonized portfolios

Our Group was asked to look at **European firms with available scope 1 to 3 emissions** (Trucost).

## Exercise 1
- **Report summary statistics (mean, median, min, max, standard deviation) on the cross-sectional distribution of the carbon intensity. Draw the histogram of the cross-sectional distribution of the variable of interest and comment on the summary statistics and the histogram.**

Our report focuses on European firms with available carbon intensity data for Scopes 1, 2 and 3. A cross-sectional analysis aims to have an industry-wide lens of European firms to identify companies with a particular strength or weakness. It allows us to understand the \"what\" rather than the \"why\". This means that instead of focusing on the relationships between the different companies to be compared, the investor uses cross-sectional analysis to identify their characteristics [@bib:csa].

As aforementioned, the variable of interest in this paper is carbon intensity. The latter measures the volume of carbon emissions per million dollars of revenue and is expressed in tonnes of CO2 equivalents per million dollars of revenue (tCO2e/mln \$) [@bib:Jondeau]. The carbon intensity of a portfolio per period (CI) is calculated as follows:

$$CI_t^{(p)} = \frac{\sum_{i=1}^{N_t} \cdot o_{i,t}^{(p)} \cdot E_{i,t}}{\sum_{i=1}^{N_t} \cdot o_{i,t}^{(p)} \cdot Rev_{i,t}}
   \hspace{0.2cm}$$

According to the GHG Protocol corporate standard, a firm's emissions are divided into three Scopes. Scope 1 emissions are the GHG emissions generated from burning fossil fuels, as well as production processes that are owned or controlled by the firm. They are the so-called direct emissions. Scope 2 emissions stem from the consumption of purchased electricity, heat, or steam by the firm. They are the first-tier indirect emissions. Finally, Scope 3 emissions are other indirect emissions from the value chain of the reporting firm. They include upstream emissions, such as energy, utilities, materials, chemicals, industrials, and consumer goods. Scope 3 also encompasses downstream Scope 3 emissions of financed emissions and sold products, such as oil and gas, automobiles, technology, apparel, and chemicals [@bib:Jondeau].

It is mandatory for firms to report Scope 1 and 2, which should be included in every portfolio construction [@bib:Jondeau]. In France, for example, companies are obliged to include Scopes 1 and 2 in their annual management report [@bib:scope_france]. Scope 3 on the other hand is optional, hard to measure and monitor, and only of importance for some industries. For instance, banks have a small Scope 1 and 2 but as they provide financing to highly polluting companies, their Scope 3 is significantly high. Thus, it can have a substantial impact on the carbon intensity of the portfolio. However, as this data sheds a negative light on the firm in question, it is often not disclosed and thus only estimated by data providers [@bib:Jondeau], such as Trucost which is used for this report. It aims to provide the data, tools, and insights needed by firms, investors, and decision-makers to enable the transition to a low carbon and resource-efficient economy [@bib:Jondeau].

The data of the carbon intensity per firm and Scope was already provided. The original data sets span from 1999 to 2020, however, we extract the data from the years 2005 to 2019 for our analysis as the other years have a notable amount of missing data and are thus less interesting to include. We estimate that 14 years of data is sufficiently representative for this report. Furthermore, we create monthly carbon intensity data by reporting the same carbon intensity for a given year twelve times, such that the annual value appears in each month of that year. Additionally, the carbon intensity, found in the scope intensity data sets, for each company and each year were summed up. (Note here that we use \"Scopes\" for scope intensities, which are the carbon intensities mentioned above) Meaning that we create a new data set, in which a company has a new value each year/month (depending on the data needed), which represents the sum of its three Scopes. (To improve the reading flow, the report will from here on refer to the sum of the Scopes as **Scopes**.) Yet, one must note that the Scopes are interlinked and often prone to double counting as the same emission could be counted up to three times in a portfolio reaching up to 40% of total emissions. Unfortunately, it is impossible to eliminate this problem completely [@bib:Jondeau]. Hence, it is important to keep this information in the back of one's mind when analysing the summary statistics and histograms of the carbon intensity.

[Scopes mean intensity]{.image}

[Scopes median intensity]{.image}

To begin with, Figure [1](#fig:Scatter_mean){reference-type="ref" reference="fig:Scatter_mean"} depicts the mean (over time) of the Scope intensities for every European firm. One can observe that most companies lie between 0 and 2000 tCO2e/mln \$ and the mean is 337.82 tCO2e/mln \$. Yet, the range including the outliers is huge, namely from 21 to 14,462 tCO2e/mln \$. Figure [2](#fig:Scatter_median){reference-type="ref" reference="fig:Scatter_median"} shows the median of the Scope intensities. Its mean is slightly lower, at 325 tCO2e/mln \$, and its range is 22 to 15,981 tCO2e/mln \$. The two graphs are similar and show the same two companies with the highest emissions.

Finally, after looking at these two graphs, one could simply say that there are extreme values that influence our average. Indeed, the mean is influenced by outliers while the median is a robust measure in the presence of outliers. For instance, when taking the median of the mean (Figure [1](#fig:Scatter_mean){reference-type="ref" reference="fig:Scatter_mean"}) this gives 137.79 tCO2e/mln \$ which is much lower than our mean of the mean (338 tCO2e/mln \$)). However, we cannot remove the extreme values here because they represent high emitting companies and are not necessarily errors in the data. For the rest of the exercise, the average is used to summarise the statistics as this is commonly done.

We find that the number one polluter is a firm named \"Biffa\", which is a waste management company. In Figure [3](#fig:Plot_highest_emission_firm){reference-type="ref" reference="fig:Plot_highest_emission_firm"} one can observe their development over three years. In 2008 Severn Trent, which had acquired the company in 1991, transferred it to a consortium formed by 3 entities [@bib:Wiki_Biffa]. This is probably why there the data stops in 2007. Their occupation explains the abnormally high emissions. Furthermore, Scope 1 was the main contributor (with values in the thousands). This is logical because Scope 1 encompasses the emissions from burning fossil fuels and production processes owned or controlled by a firm.

[Biffas' carbon intensity]{.image}

[International Powers' carbon intensity]{.image}

The second worst polluter is \"International Power\". Figure [4](#fig:Plot_2nd_highest_emission_firmpng){reference-type="ref" reference="fig:Plot_2nd_highest_emission_firmpng"} shows an astonishing evolution in their Scope intensities. Its emissions dropped each year this was due to the Scope 1 (main driver) decreasing drastically. Hence, as in the case of Biffa, its main driver was Scope 1, which is reasonable as the company is working in the energy sector (mostly non-renewable). Then the data ends in 2011 as the company merged with another in the year that followed [@bib:international_power].

Next, we can see that the minimum values (plotted in Figure [5](#fig:Scatter_min){reference-type="ref" reference="fig:Scatter_min"}) range from 5 to 7096 tCO2e/mln \$ and are on average around 256 tCO2e/mln \$. While the maximum scope intensities range from 24 to 25,729 tCO2e/mln \$ and are on average 462 tCO2e/mln \$. Both these values are also sensitive to extremes but they give a great picture of the emission range across firms. For instance, it can be observed that the graph with the minima has more variation, hence the minimum Scope values differ more from one firm to another.

[Scopes minimum intensity]{.image}

[Scopes maximum intensity]{.image}

The last summary statistic we explore is the standard deviation (Figure [7](#fig:Scatter_std){reference-type="ref" reference="fig:Scatter_std"}). It measures how dispersed the data is concerning the mean. Its value ranges between 0.2 and 12,089 tCO2e/mln \$ and is on average 82 tCO2e/mln \$.

[Scopes' standard deviation]{.image}

Given the data, Figure [8](#fig:Boxplot_as_course){reference-type="ref" reference="fig:Boxplot_as_course"} depicts the boxplot obtained in 2019 with a range (y-axis) of 0 to 1,400 tCO2e/mln \$. Upon comparing this with Figure [9](#fig:Boxplot_course){reference-type="ref" reference="fig:Boxplot_course"} [@bib:Jondeau], we observe that both plots are very similar. This is great as it demonstrates that the data collection and cleaning of this report were done to a good standard and
are representative of the European situation. It is interesting to note that the emerging countries have a huge interquartile range, meaning that some really small but also extremely big companies exist. China is a big influencer in the Asian market. Europe however has a relatively smaller interquartile range and is comparable to North America and the Pacific. Yet, the median values of all regions, depicted by the horizontal line within each box, are similar.

[Boxplot of the sum of Scopes of European firms]{.image}

[Boxplot from the course]{.image}

Next, we move onto the histogram analysis. First, the mean Scope values are put in a histogram (Figure [10](#fig:histo_mean_log){reference-type="ref" reference="fig:histo_mean_log"}). However, as observable in the graph on the top, it does not reveal much information for the specific data interval we are interested in. The problem is that the highest values are over thousands bigger than the smallest Thus, we transformed the distribution by looking at the logarithm. This is an easy way of displaying data over a wide range of values in a compact way. Meaning that the axis compresses the range into a non-linear form. Hence, the new y-axis represents the density. The logarithmic histogram is skewed to the right implying that the mean is bigger than the median value. This can also be observed in the data mentioned before, as 338 tCO2e/mln \$ (mean) is bigger than 325 tCO2e/mln \$ (median). This shows that a few firms emit a lot.

[Histogram of the mean Scopes linear and logarithmic]{.image}

To take a closer look at the values that range below 2000 tCO2e/mln \$, two more histograms are constructed. In Figure [11](#fig:histo_mean_2000){reference-type="ref" reference="fig:histo_mean_2000"} the values below 2000 tCO2e/mln \$ are depicted. Once again the histogram resembles the first one as most of
the data takes very small values. Thus, the histogram in Figure [12](#fig:histo_mean_50){reference-type="ref" reference="fig:histo_mean_50"} shows a small part of the total x-axis, namely the one between 0 and 50 tCO2e/mln \$. It depicts that no firm had a minimum mean emission lower than 20 tCO2e/mln \$. Once again, this data was already found and reported previously.

[Histogram of the mean Scopes linear with range 2000 tCO2e/mln \$]{.image}

[Histogram of the mean Scopes linear with range 50 tCO2e/mln \$]{.image}

To observe the evolution of Scopes through the years, we plot the mean Scope emissions per year (Figure [13](#fig:mean_plot){reference-type="ref" reference="fig:mean_plot"}). This is a key plot and shows that the emissions dropped drastically, especially, in 2008 because of the financial crisis. It then increased a little again, leading to another big drop in the following years until 2014. This is due to a variety of reasons from the growth of renewables, the use of less carbon-intensive fuels, energy efficiency improvements to structural changes in the economy and a recession [@bib:eea2014]. This graph is \"great news\", as the emissions already drastically decreased, however it is sadly not sufficient enough a drop to limit global warming to 2 degrees.

In 1997 the Kyoto Protocol was established. It is a legally binding treaty with the aim of decreasing greenhouse gas (GHG) emissions and it included the EU, which went even further and committed to an 8% cut in their emissions. During the period 2008-2012, the members met this, compared to the base year (1990) [@bib:Kyoto1]. Then the second commitment period of Kyoto was established. It was a 20% reduction compared to 1990 [@bib:Kyoto2]. Following this is the European Climate Law. It aims to reach net-zero by 2050 and reduce net GHG emissions by at least 55% by 2030 compared to 1990 [@bib:EUClimateLaw]. Given the overall decrease observed in Figure [13](#fig:mean_plot){reference-type="ref" reference="fig:mean_plot"}, we estimate that the most likely driver of this was the Kyoto Protocol and that it is possible to achieve further decline, however, a sharp decrease is needed.

Based on this we decided to compare the starting year 2005 and the most recent year with the most data in 2019.

[Mean Scopes emission per year]{.image}

The results obtained are quite similar to before (Figure [\[fig:histo\]](#fig:histo){reference-type="ref" reference="fig:histo"}). Again little information can be extracted from the linear scales and once transformed, we observe that the logarithmic scales are skewed to the right, indicating that a few companies emit quite a lot.

[Linear and logarithmic histogram of the year 2005 Scopes]{.image}

[Linear and logarithmic histogram of the year 2019 Scopes (linear and logarithmic]{.image}


