# Sustainable Finance - Homework 2
## Introduction
The objectives are the following:

- Evaluate the (weighted average) carbon intensity of a business-as-usual (BAU) portfolio
- Build a decarbonized portfolios of stocks based on the mean-variance criterion (efficient frontier)
- Evaluate the relative performance of BAU and decarbonized portfolios

Our Group was asked to look at **European firms with available scope 1 to 3 emissions** (Trucost).

## Question 1
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

## Question 2

- **In Question 5 of [Homework 1](https://github.com/MiaFrey/SustainableFinanceH1), you calculated efficient portfolios with various target returns. Take these portfolios, calculate and report the weighted-average carbon intensity of these portfolios (you can take the average carbon intensity for each firm over time). Comment on the carbon intensity of the portfolios. Which firms (e.g. top 10; report firm names along with ISIN) are driving the carbon intensity up? Plot on the volatility-carbon intensity space the various portfolios (i.e., make a plot similar to the efficient frontier except that carbon intensity replaces the return on the y-axis).**

One thing to note for this exercise and the entire Homework 2 is that the list of 50 companies selected was changed between the first and third assignments,as the list of random firms was not saved in the first homework.

This is why the code of [Homework 1](https://github.com/MiaFrey/SustainableFinanceH1) was rerun for the new 50 firms, to create a benchmark for comparison, before proceeding with the new part of the question. A return of 16% can still not be reached, thus, the same technique as in [Homework 1](https://github.com/MiaFrey/SustainableFinanceH1) is used to counter the problem: a return of 2% is targeted and the increment step was then modified to produce eight portfolios with reachable returns.

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

## Question 3

- **This question is a follow-up to Question 8 of [Homework 1](https://github.com/MiaFrey/SustainableFinanceH1). First, take the same 50 selected firms. Then, create a minimum variance portfolio with monthly rebalancing with an additional constraint: you exclude the worst firms in terms of most polluting (high carbonintensity) firms. Specifically, exclude the top tercile of the distribution in month t - 1 for the carbon intensity. Report summary statistics on the performance (return, risk, Sharpe ratio) of this portfolio as well as its carbon intensity. How do the performance measures (return, risk, Sharpe ratio) compare with the minimum variance portfolio from Question 4 of [Homework 1](https://github.com/MiaFrey/SustainableFinanceH1).**

This exercise addresses building a decarbonized portfolio, hence applying portfolio optimization including carbon risk. It is based on building a minimum variance portfolio and then adding constraints since it is assumed that an investor does not want to put money into a highly polluting company, meaning a company with a high carbon intensity. Thus, a threshold is fixed to restrict the exposure of the portfolio to the carbon intensity (idiosyncratic carbon risk) [@bib:Jondeau]. The threshold is the top tercile of the distribution in month t-1 for this exercise. Here the exclusion approach is used [@bib:Jondeau].

[Homework 1]{.image}

[Homework 3]{.image}

In theory, firms with a higher carbon intensity have a higher return since carbon-intensive firms are perceived as riskier, and hence the investor wants to be compensated for the additional risk taken [@bib:return-emission]. In this exercise, the firms in the top tercile with the highest carbon intensity values are excluded. Hence, theoretically the firms with the highest average return disappear and the new portfolio will have a lower return. The same holds for volatility. As explained in exercise 2, a firm with a high carbon intensity will have higher volatility. Yet, this is not what we find upon analysing the summary statistics. In Figure [1](#fig:Stat_old){reference-type="ref" reference="fig:Stat_old"} the annual average return is 0.047 and the volatility 0.154 but in [2](#fig:Stat_new){reference-type="ref" reference="fig:Stat_new"} the return is bigger (0.067) but the volatility (0.149) is smaller. Even though the minimum return got smaller (-0.157 \> -0.132) but the maximum one only slightly bigger (0.126 \< 0.153). Thus, the 50 randomly selected firms did not have a positive correlation between carbon intensity and return. This must be due to chance as they were selected from a large pool of possible firms. All of these points can also be observed in Figure [\[fig:MV\]](#fig:MV){reference-type="ref" reference="fig:MV"}.

Furthermore, one also observes that the Sharpe ratio increases after the exclusion of the most polluting companies (0.227 \< 0.364). This measure of risk-adjusted return shows that it is more interesting to invest in the minimum variance portfolio with the exclusion. Yet, it remains lower than 1. The potential gain generated is therefore not high enough to compensate for the risk taken by investing, even though this is rare to find. Finally, by omitting the top tercile of the polluting companies, the overall carbon intensity of the portfolio decreases drastically. In [Homework 1](https://github.com/MiaFrey/SustainableFinanceH1) the portfolio had a carbon intensity of 111.591 tCO2e/mln \$ versus \"only\" 31.9005 tCO2e/mln \$ in Homework 2. It decreased by more than one third since by excluding the top tercile of polluters one excludes more than a third of the emissions.

[Homework 1]{.image}

[Homework 3]{.image}

## Question 4

 - **For each month, sort firms based on your group's variable of interest (carbon intensity) into quintiles. Create equally-weighted and value-weighted portfolios for each period and each score or carbon intensity quintile. Report the average returns for each quintile portfolio as well as a portfolio that goes long in the highest quintile and short in the lowest quintile. Comment on your results. What can explain the relationship between the return of your portfolios and firms' carbon emissions?**

After sorting the carbon intensities in ascending order, they are separated into quintiles. Quintile 5 contains the most polluting firms this is why the portfolio goes short in that part and long in the lowest quintile to purchase even more green firms because the aim is to invest in green. Hence, the performance (return) of the short side (quintile 5) is subtracted from the performance of the long (quintile 1).

The average returns of the equally-weighted (EW) and value-weighted (VW) portfolios per quintile, from lowest (q1) to highest (q5) are depicted
on the following graphs:

[Equally weighted portfolio]{.image}

[Value weighted portfolio]{.image}

To see the effect of the size of the Scope intensities more clearly, below is the plot of only the first and last quintiles.

[Equally weighted portfolio]{.image}

[Value weighted portfolio]{.image}

For the equally weighted (EW) portfolio, the average return of Q1 is 0.0082, and for Q5 0.0085. The difference is extremely small ($\Delta$ = 0.0003) and thus insignificant. This means that the most polluting European firms had on average almost the same return as the least polluting ones. However, the value-weighted (VW) portfolio has a lower return in the Q1 with 0.0035 compared to Q5 with 0.0061. This is consistent with the correlation mentioned in Question 2 (bigger polluter
=\> larger return). For the VW portfolio, this disparity is larger ($\Delta$ = 0.0028).

In theory, the equally-weighted portfolio outperforms the value-weighted one because it gives higher weights to small firms and thus is able to have higher returns since small companies tend to have a higher return. This can also be observed in this exercise since for the first (0.0082 \> 0.0035) and the fifth (0.0085 \> 0.0061) quintile the equally-weighted portfolio yields a higher return.

To find the relationship between the return and the carbon emissions, the correlation was calculated for each quintile and is depicted in the tables below.

[Equally weighted portfolio]{.image}

[Value weighted portfolio]{.image}

In Question 2, it is explained that the relationship between returns and the emission rate of firms is positive. In Figure [\[fig:Stat_both\]](#fig:Stat_both){reference-type="ref" reference="fig:Stat_both"}, in both cases, the correlation is low but positive. Additionally, it can be observed that it increased for each quintile (except between quintiles 4 and 5 in the value-weighted portfolio). These results are consistent with the findings of Bolton and Kacperczyka. They call it the carbon premium and explain it with the fact that investing in carbon-intensive industries is perceived as riskier and thus the investors need to be compensated for it [@bib:return-emission].

Average returns for the short-long (SL) portfolio:

[Equally weighted portfolio]{.image}

[Value weighted portfolio]{.image}

In Figure [\[fig:SL\]](#fig:SL){reference-type="ref" reference="fig:SL"} the average return of the SL portfolio is -0.0003 for the EW and -0.0026 for the VW. Hence, compared to [Homework 1](https://github.com/MiaFrey/SustainableFinanceH1) Question 9 the short-long portfolio here is better (-0.0003 \> -0.02 for EW and -0.0026 \> -0.07 for VW) as the returns increased and are no longer negative but almost zero.

# Question 5 {#sec:q5}

**Take the minimum variance portfolio from Question 4 of [Homework 1](https://github.com/MiaFrey/SustainableFinanceH1) and calculate its carbon intensity. Reallocate its composition to reduce carbon intensity by 50% (see optimization problem below). Comment on the changes it took to improve the carbon intensity (e.g. how many and which firms (firm names) had to be removed in the most recent year of your sample to achieve these objectives).**

Similar to Question 3, the decarbonized portfolio is used. Minimum variance portfolios for each month are built, as in Question 4 of H[Homework 1](https://github.com/MiaFrey/SustainableFinanceH1). This time a new random sample of 50 firms (new50) is used. Hence, the code is re-run once (without modification), to have a comparable baseline. Next, the additional constraint is added. The aim is to have a weighted average carbon intensity (WACI) that is less than half that of the baseline. The reason for doing this results from the assumption that investors do not desire to invest in highly polluting companies [@bib:Jondeau]. In other words, the goal is to reduce the carbon intensity of the minimum variance portfolio by at least half each month. The constraint is the following:

$$\sum_{i}(Weight_{i,m} \cdot ScopeIntensity_{i,m}) \leq 0.5\cdot WACIbaseline_m$$

The portfolios are optimised under both constraints (sum of weights equals 1 and lower weighted average carbon intensity) to get the new weights of the decarbonized portfolios, denoted \"weights2\" in the code. The optimisation problem looks as follow:

$$\begin{aligned}
\underset{\alpha}{min}  \hspace{0.7cm}  &\alpha'\Sigma \alpha \\
s.t. \hspace{0.7cm}                     &\alpha'e = 1 \\
                                        &\alpha'CI \leq 0.5 \cdot (\alpha'CI)_{Q4-HW1}\end{aligned}$$

Where $\alpha$ are the weights, $\Sigma$ is the covariance matrix, e is a vector of ones and CI are the carbon intensities (which this report calls Scope intensities or Scopes). The formula returns a weights vector such that the resulting portfolio has the minimum possible variance, thus the minimum variance portfolio can be constructed and its summary statistics analysed.

This is all based on fundamental-based risk management in which the exposure of the portfolio to carbon intensity, an idiosyncratic carbon risk, is restricted. In this exercise, we take a portfolio threshold approach, consisting of portfolio optimisation under an additional constraint of an upper bound for the WACI of the whole portfolio. An alternative method could have been to impose an individual threshold, such that we eliminate companies from our portfolio ($\alpha$ = 0) which
have a carbon intensity above a pre-defined threshold [@bib:Jondeau].

[Without an additional constraint]{.image}

[With an additional constraint]{.image}

As it can be seen in Figure [\[fig:SumStatQ5\]](#fig:SumStatQ5){reference-type="ref" reference="fig:SumStatQ5"}, the return of the decarbonized portfolio is
higher (0.150 \> 0.137), so is the minimum (-0.89 \> -0.097) and maximum returns (0.119 \> 0.111). As volatility and return are positively correlated, we observe an slight increase in the volatility also (0.156 \> 0.154). Furthermore, the Sharpe ratio grew (0.885 \> 0.809), which means that the investor should choose the decarbonized portfolio. Finally, the carbon intensity halved (93.769 = 187.539 / 2). This is great news as this was the constraint of the decarbonized portfolio and
hereby it can be checked that the constraint was respected.

Upon carrying out this analysis, we wanted to make sure that we only considered firms that had available Scopes 1,2 & 3 over the time period studied. Otherwise, it would have be easy to wrongly re-allocate weights, such that firms with no data take up a larger portion of the portfolio, since they would not influence the WACI of the portfolio. To avoid this mistake, it is crucial to filter the data pre-optimisation. We thus chose to focus on the years that had the most available scope data, to have a large basket of firms for selecting our 50 random firms (new50). Hence, we took data over 4 years from January 2016 to December 2019, and then dropped remaining firms which had NaNs in their scopes. Among the remaining firms, we then randomly selected 50. Disclaimer: It is still possible to have weights that are NaN in our portfolio, this is because upon looking at each month individually (in our loop), we drop firms without return data, so as not to include them in the portfolio. If these happen to be a part of our set of 50 random firms, then there will be no weight associated with these particular firms.

As a result of the new optimisation, it is interesting to visualise how the weights of the different companies changes within the portfolios (Figure [3](#fig:diffWeights){reference-type="ref" reference="fig:diffWeights"}). To do so, the average difference over all months between the weight of each firm given the additional constraint and the weight of the firm without the additional constraint are plotted. In this way, firms with a positive difference, represented in the bar chart by the bars above zero, are those in which there was an increased investment, post-introduction of the new constraint. Whereas the negative bars indicate that firms lost weight in the portfolio with the additional constraint. Hence, it can be assumed, a priori, that the companies with positive bars are greener, because we increased our investment in them to satisfy the decarbonisation constraint, whereas the firms with negative bars wou

[Differences of the allocated weights per firm. $\alpha_{HW3} - \alpha_{HW1}$]{.image}

In Figure [3](#fig:diffWeights){reference-type="ref" reference="fig:diffWeights"}, the difference in weights between Homework 2 and 1 can be observed. If we look at the minimum variance portfolio of December 2019, we see that only two firms have been completely removed from the portfolio. The first one is called Umicore. It is a global material technology and recycling group [@bib:umicore]. Umicore's Scope 3 is the biggest, likely due to the use of the recycled materials and the supply chain before the material got recycled. The second company is BASF, a chemical firm [@bib:BASF]. Its Scope 1 is high but Scope 3 is even higher. Once again this can be explained by their business as chemical production itself emits a lot of emissions and so does its supply chain all the way from mining to recycling.

::: {#tab:deleted}
  **Company**           **Deleted**   **Products/Services**                      **Scope(s)**
  --------------------- ------------- ------------------------------------------ --------------
  AMIAD WATER SYSTEMS   36            Filtration Technology                      3
  BASF                  38            Chemical company                           (1), 3
  DNO                   29            Oil and gas operator                       1, (3)
  MASSIMO ZANETTI       48            Coffee production                          3
  STELLANTIS            26            Automotive manufacturing corporation       3
  SYSTEMAIR             34            Manufacturer of ventilation equipment      3
  UMICORE               32            Materials technology and recycling group   3
  ZIGNAGO VETRO         48            Glass packaging industry                   1, (2)

  : Most deleted companies
:::

Table [1](#tab:deleted){reference-type="ref" reference="tab:deleted"} [@bib:umicore], [@bib:BASF], [@bib:systemair], [@bib:stellantis], [@bib:dno], [@bib:zignago_vetro], [@bib:amiad_water_systems], [@bib:massimo] summarises the companies that were not considered in the new portfolio more than half of the time (48 months /2 = 24). \"Deleted\" means that the company was not part of the new portfolio \"Nb deleted\" times. The \"Products/Services\" explain what they do and
\"Scope(S)\" mentions the highest Scope, and if another one is high as well it is written in brackets. The two companies not considered in the most recent year (mentioned above) are also on this list, as well as the company MASSIMO ZANETTI that is talked about in the following paragraph.

To push the analysis of Figure [3](#fig:diffWeights){reference-type="ref" reference="fig:diffWeights"} further, the company with the biggest (CREALOGIX HOLDING) and smallest (MASSIMO ZANETTI) difference in weight allocation are analysed in more depth.

[MASSIMO ZANETTI]{.image}

[CREALOGIX HOLDING]{.image}

The two graphs in Figure
[5](#fig:PlotCREALOGIX_HOLDING){reference-type="ref" reference="fig:PlotCREALOGIX_HOLDING"} explain why more weight was allocated to \"CREALOGIX HOLDING\" than to \"MASSIMO ZANETTI\". Indeed, the emissions are much higher for the company \"MASSIMO ZANETTI\". It is a coffee production company and its Scope 3 has the highest
emissions[@bib:massimo]. This result is consistent with reality because coffee is one of the products that emit the most CO2 during its entire supply chain. This can be observed in Figure [6](#fig:cafe){reference-type="ref" reference="fig:cafe"}, where it can be seen that the biggest part of the emissions is related to the
cultivation of the coffee beans, which is included in Scope 3 of the company.

[Food greenhouse gas emissions across the food supply chain]{.image}

The company \"CREALOGIX HOLDING\" has a very low Scope 1 and 2. This is a result of the fact that it is a holding company. This means that it has few direct emissions. Moreover, it is a holding company that mainly supports banks, thus leading to a low Scope 3[@bib:crealogix].

---
nocite: "[@*]"
references:
- author:
  - family: Jondeau
    given: Eric
  id: "bib:Jondeau"
  issued: 2022
  title: Sustainable and entrepreunarial finance
  type: article-journal
- accessed: 2022-04-29
  author:
  - family: Chen
    given: James
  id: "bib:csa"
  issued: 2020
  title: Cross-sectional analysis
  type: webpage
  url: "https://www.investopedia.com/terms/c/cross_sectional_analysis.asp"
- author:
  - family: COUNT
    given: WE
  id: "bib:scope_france"
  title: Est-ce obligatoire de réaliser son bilan carbone (BEGES)?
  type: webpage
  url: "https://www.wecount.io/post/est-ce-obligatoire-de-réaliser-son-bilan-carbone-beges"
- author:
  - family: NewCo
  id: "bib:holding"
  title: "Qu'est-ce qu'une holding ?"
  type: webpage
  url: "https://newco.ch/fr/blog/qu-est-ce-qu-une-holding\\--52"
- accessed: 2022-05-04
  author:
  - family: Biffa
  id: "bib:Biffa"
  issued: 2022
  title: Biffa
  type: webpage
  url: "https://www.biffa.co.uk/"
- accessed: 2022-05-04
  author:
  - family: Engie
  id: "bib:international_power"
  issued: 2011
  title: International power plc and GDF SUEZ successfully create a
    global leader in independent power generation
  type: webpage
  url: "https://www.engieresources.com/international-power-plc-and-gdf-suez-successfully-create-a-global-leader-in-independent-power-generation"
- author:
  - family: Bolton
    given: Patrick
  - family: Kacperczyk
    given: Marcin
  container-title: Journal of Financial Economics
  id: "bib:return-emission"
  issue: 142
  issued: 2021
  page: 517-549
  publisher: ELSEVIER
  title: Do investors care about carbon risk?
  type: article-journal
- accessed: 2022-05-05
  id: "bib:eea2014"
  issued: 2016
  title: EU greenhouse gas emissions at lowest level since 1990
  type: webpage
  url: "https://www.eea.europa.eu/highlights/eu-greenhouse-gas-emissions-at\\#:\\~:text=European%20Union%20(EU)%20greenhouse%20gas,European%20Environment%20Agency%20(EEA)."
- accessed: 2022-05-09
  author:
  - family: Hayes
    given: Adan
  id: "bib:long"
  issued: 2021
  title: Long position
  type: webpage
  url: "https://www.investopedia.com/terms/l/long.asp"
- accessed: 2022-05-10
  author:
  - family: Commission
    given: European
  id: "bib:Kyoto2"
  title: Kyoto 2nd commitment period (2013--20)
  type: webpage
  url: "https://ec.europa.eu/clima/eu-action/climate-strategies-targets/progress-made-cutting-emissions/kyoto-2nd-commitment-period-2013-20_en"
- accessed: 2022-05-10
  author:
  - family: Commission
    given: European
  id: "bib:Kyoto1"
  title: Kyoto 1st commitment period (2008--12)
  type: webpage
  url: "https://ec.europa.eu/clima/eu-action/climate-strategies-targets/progress-made-cutting-emissions/kyoto-1st-commitment-period-2008-12_en"
- accessed: 2022-05-10
  author:
  - family: Commission
    given: European
  id: "bib:EUClimateLaw"
  title: European climate law
  type: webpage
  url: "https://ec.europa.eu/clima/eu-action/european-green-deal/european-climate-law_en"
- accessed: 2022-05-10
  id: "bib:Wiki_Biffa"
  title: Biffa
  type: webpage
  url: "https://en.wikipedia.org/wiki/Biffa"
- accessed: 2022-05-11
  id: "bib:umicore"
  title: About umicore
  type: webpage
  url: "https://www.umicore.com/en/about/"
- accessed: 2022-05-11
  id: "bib:BASF"
  title: BASF
  type: webpage
  url: "https://en.wikipedia.org/wiki/BASF"
- accessed: 2022-05-11
  author:
  - family: Wikipédia
  id: "bib:systemair"
  issued: 2022
  title: Systemair
  type: webpage
  url: "https://fr.wikipedia.org/wiki/Systemair"
- accessed: 2022-05-11
  author:
  - family: Wikipédia
  id: "bib:stellantis"
  issued: 2022
  title: Stellantis
  type: webpage
  url: "https://fr.wikipedia.org/wiki/Stellantis"
- accessed: 2022-05-11
  id: "bib:dno"
  title: DNO
  type: webpage
  url: "https://www.dno.no"
- accessed: 2022-05-11
  id: "bib:zignago_vetro"
  title: ZIGNAGO VETRO
  type: webpage
  url: "https://zignagovetro.com/fr/"
- accessed: 2022-05-11
  id: "bib:amiad_water_systems"
  title: Amiad water systems
  type: webpage
  url: "https://fr.amiad.com"
- accessed: 2022-05-11
  id: "bib:rea"
  title: R.e.a holdings plc
  type: webpage
  url: "https://www.rea.co.uk/websites/reaholdingsplc/English/1/home.html"
- accessed: 2022-05-11
  author:
  - family: Wikipédia
  id: "bib:evn"
  issued: 2019
  title: EVN (entreprise)
  type: webpage
  url: "https://fr.wikipedia.org/wiki/EVN\\_(entreprise)"
- accessed: 2022-05-11
  id: "bib:tubacex"
  title: TUBACEX GROUP
  type: webpage
  url: "https://www.tubacex.com"
- accessed: 2022-05-11
  id: "bib:tubacex2"
  title: TUBACEX GROUP, environment
  type: webpage
  url: "https://www.tubacex.com/tubacex-group/prevention-environment-quality/environment/"
- accessed: 2022-05-10
  id: "bib:crealogix"
  title: CREALOGIX
  type: webpage
  url: "https://crealogix.com/en"
- accessed: 2022-05-10
  id: "bib:massimo"
  title: Massimo zanetti
  type: webpage
  url: "https://www.mzb-group.com"
- accessed: 2020-10-17
  author:
  - family: Witlox
    given: Kasja
  - family: Keller
    given: Regula
  - family: Jungbluth
    given: Niels
  id: "bib:esu2015poster"
  issued: 2015
  title: A LCA case study of hand washing with liquid and bar soap
  type: webpage
  url: "http://esu-services.ch/fileadmin/download/witlox-2015-LCA-soap-poster.pdf"
- author:
  - family: Koehler
    given: Annette
  - family: Wildbolz
    given: Caroline
  container-title: Environmental science & technology
  id: "bib:koehler2009comparing"
  issue: 22
  issued: 2009
  page: 8643-8651
  publisher: ACS Publications
  title: "Comparing the environmental footprints of home-care and
    personal-hygiene products: The relevance of different life-cycle
    phases"
  title-short: Comparing the environmental footprints of home-care and
    personal-hygiene products
  type: article-journal
  volume: 43
- author:
  - family: Feld
    given: Brad
  - family: Mendelson
    given: Jason
  id: "bib:ventureDeals"
  issued: 2019
  publisher: John Wiley & Sons Inc
  publisher-place: New York, United States
  title: "Venture deals : Be smarter than your lawyer and venture
    capitalist"
  title-short: Venture deals
  type: book
---
