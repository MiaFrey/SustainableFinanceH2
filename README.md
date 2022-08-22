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

## Exercise 2
- **In Question 5 of Homework 1, you calculated efficient portfolios with various target returns. Take these portfolios, calculate and report the weighted-average carbon intensity of these portfolios (you can take the average carbon intensity for each firm over time). Comment on the carbon intensity of the portfolios. Which firms (e.g. top 10; report firm names along with ISIN) are driving the carbon intensity up? Plot on the volatility-carbon intensity space the various portfolios (i.e., make a plot similar to the efficient frontier except that carbon intensity replaces the return on the y-axis).**

One thing to note for this exercise and the entire Homework 2 is that the list of 50 companies selected was changed between the first and third assignments,as the list of random firms was not saved in the first homework.

This is why the code of Homework 1 was rerun for the new 50 firms, to create a benchmark for comparison, before proceeding with the new part of the question. A return of 16% can still not be reached, thus, the same technique as in Homework 1 is used to counter the problem: a return of 2% is targeted and the increment step was then modified to produce eight portfolios with reachable returns.

The efficient frontier representing the efficient portfolios and the attainable returns that can be targeted with these 50 randomly selected firms is the following.

[Efficient frontier of the 50 selected firms]{.image}

The weighted-average carbon intensity (WACI) is a measure of the portfolio's exposure to polluting firms. The higher a portfolio's investment in carbon-intensive firms, the higher its weighted-average carbon intensity is. The measurement's unit is in tons of $CO_2$ equivalents per million dollars of revenue $[tCO_2eq/\$mln]$. The following formula is used to calculate the WACI of a portfolio in year $t$ [@bib:Jondeau]:

$$WACI = \Sigma_{i=1}^{N_t} w_{i,t} \cdot \frac{E_{i,t}}{Rev_{i,t}} = \Sigma_{i=1}^{N_t} w_{i,t} \cdot CI_{i,t}$$

Where $N_t$ is the number of firms in the portfolio in period $t$, $w_{i,t}$ is the weight of the firm $i$ in the portfolio in period t, $E_{i,t}$ is the emissions of the firm $i$ in period t, $Rev_{i,t}$ its revenue in period t and $CI_{i,t}$ its carbon intensity in period t.

More precisely in the case of this exercise, the calculation of the weighted average carbon intensity is done with the mean carbon intensity of each firm over time multiplied by the corresponding weights of the firms in the portfolio. The summary statistics of the results are reported below. One can observe the usual positive correlation between return and volatility, this being that the higher the return, the higher the volatility. The maximal Sharpe ratio observable in the table is
equal to 0.093 and corresponds to a portfolio WACI that is almost half the one of a portfolio maximising return.

[Summary statistics of the different portfolios created]{.image}

One can see also in Figure [2](#fig:Q2_sumStats){reference-type="ref" reference="fig:Q2_sumStats"} and [3](#fig:CI(Vol)){reference-type="ref" reference="fig:CI(Vol)"} that aiming for a higher return increases the volatility as well as the carbon intensity of the portfolio. Bolton and Kacperczyk (2021) found that carbon emissions significantly affect stock returns and this is in line with what is found in the data of this report [@bib:return-emission]. The more one increases the targeted return the higher the carbon intensity, thus the higher the negative impact of the portfolio on the environment.

[WACI of a portfolio in function of its variability]{.image}

When looking at the top 10 emitting firms within the 50 randomly selected (Figure [4](#fig:top10){reference-type="ref" reference="fig:top10"}), one can see that the first one is more or less equal to the sum of the second to fifth ones and that together they represent around two-thirds of the emissions of the 10 worst firms. Indeed, the most polluting company has a carbon intensity of around 5000 tCO2e/mln \$, and the following companies have results of around 1000 tCO2e/mln \$.

[Top 10 carbon intensive firms within the 50 randomly selected sample]{.image}

In this report, the focus lies with European companies. Hence, to be able to compare European companies with those of the rest of the world the following summary table is presented. It summarises the emissions of the 25 most highly emitting companies in the world (considering the sum of Scopes 1, 2, and 3):

::: {.adjustbox} width=,totalheight=,keepaspectratio

::: {#tab:Elo'sTable}
   N°    Emissions                   Name                     Region         Continent
  ---- ------------- ------------------------------------ --------------- ---------------
   1    18374,02563         CHINA RESOURCES POWER            Hong Kong         Asia
   2    15282,23622              DGI.PWG.'H'                   China           Asia
   3    14270,08351                  NTPC                      India           Asia
   4    13736,28866            CHIN.PWR.INTDVT.              Hong Kong         Asia
   5    13388,66862    HUADIAN POWER INTERNATIONAL 'H'         China           Asia
   6    12624,54763               PXP ENERGY                Philipines         Asia
   7    12499,05943    HUANENG POWER INTERNATIONAL 'H'         China           Asia
   8    12259,69946       GUANGDONG ELEC.PWR.DEV.'B'           China           Asia
   9    12157,25576               NLC INDIA                    India           Asia
   10   12054,80082      TONGFANG KONTAFARMA HOLDINGS        Hong Kong         Asia
   11   10351,66473         ELECTRICITY GENERATING           Thailand          Asia
   12   10169,95282               TRANSALTA                   Canada       North America
   13   9457,156157            REFEX INDUSTRIES                India           Asia
   14   8739,007641           NATIONAL ALUMINIUM               India           Asia
   15   8277,845097     DYNEGY DEAD - DELIST.09/04/18      United States   North America
   16   8238,296685             RELIANCE POWER                 India           Asia
   17   8192,131009            SIAM CITY CEMENT              Thailand          Asia
   18   7764,15405                 YUNIPRO                    Russia          Europe
   19   7518,480417              ADANI POWER                   India           Asia
   20   7394,042326       JSW ISPAT SPECIAL PRODUCTS           India           Asia
   21   7177,030666            SHANXI XISHAN C             ELY.PWR. 'A'        6344
   22   7175,503165       SHERRITT INTL.RESTRCTD VTG          Canada       North America
   23   6776,780786                 EVERGY                 United States   North America
   24   6776,671493   SUEZ CEMENT DEAD - DELIST.11/02/21       Egypt          Africa
   25   6640,611099          ICT.TUNGGAL PRAKARSA            Indonesia         Asia

  : Rest of the world top 25 emitting firms
:::
:::

First of all, it can be observed that the most polluting companies in the world emit much more than the ones in Europe. Indeed, the emission of the 25 highest firms is around 15'000 tCO2e/mln \$ which is three times higher than the European firm emitting the most and around 15 times higher than the other highest emitters of Europe. Moreover, these companies are often in Asia. To better understand the results the following table summarises the data by continent:

::: {#tab:EmPerComp}
     Continent      Emissions     Share
  --------------- ------------- ---------
       Asia        210355,0865   81,76 %
   North America   32400,08187   12,59 %
      Europe       7764,15405    3,02 %
      Africa       6776,671493   2,63 %

  : Emission per continent
:::

Even if the sample of the top emitters is not representative of the average, it can still be noted that Asia produces about 81% of the emissions produced by the 25 most polluting companies. In second place is the USA with about 13%. These results are in agreement with the following table depicting that the largest emitters in 2017 were Asia followed by the USA and Europe [@bib:Jondeau]:

[Emissions by continent in 2017]{.image}

Currently, it is the firms located in Asia, a continent in full expansion and growth, that emit the most. In conclusion, Europe is currently not the largest emitter in the world. However, historically speaking Europe is the biggest polluter with about 33% of the global cumulative emissions. These results are consistent with the demographics of each continent. Indeed, Europe has already experienced its growth phase and is now stagnating or even declining, while Asia is still growing in terms of population and economically and is therefore evolving rapidly [@bib:Jondeau].

Next comes the analysis of the three highest emitters in Europe, according to (Figure [5](#fig:continent){reference-type="ref" reference="fig:continent"}, which drive the carbon intensity of the portfolios up.

## Firm 1 : R.E.A Holding

The biggest polluter is a holding company. This is a firm that takes financial stakes in other companies and therefore participates in their direction and management [@bib:holding]. According to the theory, it is therefore expected that Scope 3 of this company will be high, as it is linked to the emissions released by the companies that the holding company finances. There are certain anomalies in the scope data that we were unfortunately not able to find explanations for during our research.

REA invests mainly in the cultivation of palm oil, a very polluting sector[@bib:rea]. That is why it is not surprising that this company is at the top of the list.

[Scope 1]{.image}

[Scope 2]{.image}

[Scope 3]{.image}

## Firm 2: EVN

EVN is an Austrian company that produces and distributes energy. In the following three graphs, one can see the different carbon intensities for each year[@bib:evn].

The first thing to note is that the values for the years 2007 through 2012 are missing. This can have an impact on the average. Indeed, when we have fewer observations, the presence of extreme cases has a bigger influence on the average. For example, in 2005 the value for Scope 3 is much higher than the others.

Secondly, one can observe that Scope 1 has the highest emissions, which is consistent with the theory. Indeed, EVN is an energy production company whose main emission is linked to the energy they produce.

[Scope 1]{.image}

[Scope 2]{.image}

[Scope 3]{.image}

## Firm 3: Tubacex

Tubacex is a company producing pipes and their market is mainly constituted by Oil & Gas, Powergen, and Petrochemical industry[@bib:tubacex].

First of all, the results are only based on four years, which could slightly distort the average.

Scope 3 is responsible for its high overall score. This is reasonable as Scope 3 takes into account all down- and upstream emissions. Thus, the sale of their pipes mainly for purposes related to oil and gas explains their high Scope 3 intensity. We observe that something happens in 2018 which greatly increases scopes 1 and 2, however,we remain unsure of the reasons that cause this phenomena.

Their website leads us to believe that they are trying to become more sustainable, notably by \"advanced materials leading to significantly improved energy efficiency; and reduction in CO2 emissions, as a result\"[@bib:tubacex2]. We note here that by implementing these various measures, they can decrease Scope 1 and 2 but not 3 which is responsible for their high result. Nevertheless, this is better than nothing but it means that it would not have a significant impact on their total carbon intensity.

[Scope 1]{.image}

[Scope 2]{.image}

[Scope 3]{.image}
