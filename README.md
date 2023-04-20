# 6502 Text Analysis Using Python: Final Project
## **Introduction**
The phenomenon of climate change has been increasingly recognized as a pressing and paramount concern, one that demands immediate actions from the international community. Acknowledging the gravity of the situation and working towards mitigation and adaptation strategies to address the impending crisis. The Intergovernmental Panel on Climate Change (IPCC)’s [Sixth Assessment Report (AR6)](https://www.ipcc.ch/report/ar6/wg3/), published by Working Group III (WGIII) in 2022, provides a comprehensive analysis of climate change. It measures the environmental and socio-economic impacts of climate change and analyzes options and mitigation strategies for GHG emission reductions. For each statement, the report indicates a degree of confidence following ‘Guidance Note for Lead Authors of the IPCC Fifth Assessment Report on Consistent Treatment of Uncertainties’, which uses ‘confidence in the validity of a finding’ and ‘quantified measures of uncertainty’ as two metrics to categorize the degree of certainty in key findings. <br>
<br>
*This research is focusing on the IPCC's sixth assessment report released in 2022 given the full report for the latest AR6 synthesis report on climate change 2023 has not been publicly available yet.*<br> 
<br>
WGIII is one of the three working groups under the IPCC, a scientific body under the United Nations to provide information on climate change. This study is interested to examine the linguistic tone of the certainty level in each section of AR6 with a focus on mitigation strategies and technologies. This provides an understanding of IPCC's underlying views on the  <br>
<br>

## **Thesis**
How does the linguistic tone of the certainty levels of each statement (‘very high’, ‘high’, ‘medium’, ‘low’, and ‘very low’) in IPCC’s Sixth Assessment Report (AR6) published by Working Group III (WGIII) vary across different sections of the report with a focus on mentioned mitigation strategies and technology?<br>

<br>

## **Hypothesis**
The linguistic tone of certainty levels in IPCC's AR6 WGIII report regarding mitigation strategies and technology will vary across different sections of the report, largely due to the uncertainties associated with estimating policy implementations, adoption of climate goals by different countries, and other external factors. This study hypothesizes that the report will take a neutral tone and describe various emission mitigation pathways as the potential solutions to address the issue of climate change. Specifically, the study hypothesized that sections discussing about sector-specific topics, such as industry, urbanization, building, and agriculture, will have higher degree of cenrtainty in the statements compared to sections discussing potential solutions and scenario-based discussions, such as mitigation strategies and international cooperations. This is because sector-specific themes might have more concrete data on established policies and less unpredictabilities, leading to a higher degree of confidence, whereas hypotheical scenarios about mitigation pathways rely on nations' climate policy adoptions and political priorities.<br>

<br>

## **Methodologies**
### ***Menu***
- [Web Scrapping & Text Extraction by Chapters](https://github.com/JianiW/6502_Final_Project/blob/main/Final_project_Download_Extract_byChapter.ipynb)
- [Data Cleaning & Analysis](https://github.com/JianiW/6502_Final_Project/blob/main/Final_Version_Data_Cleaning_and%20Analysis.ipynb): this study uses separate jupyter notebook to an easier-navigating purpose. During actual coding processes, additional data cleaning processes were required due to some error messages. More details are explained below.
- <*additional code, not part of this project*>[Web Scrapping & Text Extraction (full report)](https://github.com/JianiW/6502_Final_Project/blob/main/Final_Project_Download_Extract_Whole_pdf.ipynb): *This code was not used for this research since anlayzing the report as a whole does not provide any meaningful insights due to the difficulties of cleaning all the comfounding text, such as references, chart, and plots.

### ***Data Collection***
The main source of data will be the full AR6 report, ‘Climate Change 2022: Mitigation of Climate Change’, released by WGIII. The report is publicly available and is 2258 pages including appendices. The full report includes 17 chapters discussing 8 climate scenarios, sector-analysis and projections, policy summaries and recommandations, and potential international cooperations, and financial analysis.<br>
<br>
The primary method to scrape text from IPCC's website is using the `request` method and the `BeautifulSoup` library. The code is from [the webpage "Downloading PDFs with Python using Requests and BeautifulSoup"](https://www.google.com/url?q=https://www.geeksforgeeks.org/downloading-pdfs-with-python-using-requests-and-beautifulsoup/&sa=D&source=docs&ust=1681670025773146&usg=AOvVaw2kiguF-w_aUhMPILIKYUh1) <br>
<br>
The primary method to extract PDF to text is `PyPDF2`. Given the full report is 2256 pages long mixed with appendix, references, plots, charts, and supplementary materials. The approach to extract text is breaking down the chapters by sections and themes and mannualy labeling the page ranges. A PDF reader object is created to extract the text from the pages corresponding to the summary. For the page range, it only includes from the executive summary of the targeted section to the last page before supplementary materials and reference. The code will remove any text that start with the footnote number then be saved as the resulting text into a text file. The code is revised based on [the webpage "Extract text from PDF File using Python"](https://www.geeksforgeeks.org/extract-text-from-pdf-file-using-python/#") and [Stack Overflow "How to extract text from a PDF file?"](https://stackoverflow.com/questions/34837707/how-to-extract-text-from-a-pdf-file). <br>
<br>
There are 15 txt files extracted from the full report with the following corresponding order:<br>
> | Report Chapter Name | Corresponding Section (txt file)|
> | --- | --- |
> | Summary for Policymakers | 'chapter_policymaker.txt' |
> | Introduction (Chapter 1) | 'chapter_intro.txt' |
> | Mitigation Pathway (Chapter 2 - 5) | 'chapter_mitigation.txt' |
> | Energy System (Chapter 6) | 'chapter_Energy_System.txt' | 
> | Agriculture, Forestry, and Other Land Use (AFLOU) (Chapter 7) | 'chapter_AFLOU.txt' |
> | Urban System and Other Settlements (Chapter 8) | 'chapter_Urban_System.txt' |
> | Buildings (Chapter 9) | 'chapter_Building.txt' |
> | Transport (Chapter 10) | 'chapter_Transport.txt' |
> | Industry (Chapter 11) | 'chapter_Industry.txt' | 
> | Cross-Sectoral Perspectives (Chapter 12) | 'chapter_Cross_sectoral.txt' |
> | National and Sub-national Policies and Institutions (Chapter 13) | 'chapter_national_policies.txt' |
> | International Cooperations (Chapter 14) | 'chapter_intl_coop.txt' |
> | Investment and Finance (Chapter 15) | 'chapter_Investment.txt' |
> | Innovation, Technological Development and Transfer (Chapter 16) | 'chapter_innovation.txt' |
> | Accelerating the Transition in the Context of Sustainable Development | 'chapter_Sus_Dev.txt' |
<br>
<br>

#### ***Data Cleaning***
Stop words removal, lemmatization, and tokenization are performed to reduce noise caused by stop words, inflectional forms of words, punctuation marks. It's important to note that the processed data are not completely 'clean' due to the nature of the IPCC's report. It's mixed of technical, scientific and policy-oriented lanaguaes. Despite the data cleaning steps taken, the text data may still contain some noise or variation due to the nature of the source material. For example, some technical terms may be inflected differently in different sections of the report, and some policy-oriented language may be harder to identify as stop words. Therefore, the cleaned data represents a simplified version of the original text data, with some potentially relevant information removed or altered. However, the cleaned data still provides a valuable foundation for analysis, allowing us to focus on the most salient information and explore the main themes and patterns in the report.<br>
<br>
The raw txt files are all imported and saved into dataframes using the `pandas` library and the `glob` using the revised code originated from [the Stack Overflow webpage "Iterate through folders and find a file to put into a dataframe"](https://stackoverflow.com/questions/63814128/iterate-through-folders-and-find-a-file-to-put-into-a-dataframe") and [the webpage "pandas.DataFrame.to_csv"](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.to_csv.html).<br>
<br>
A function was created to perform tokenization, stop word removal, and lemmatization and applied to the entire dataframe saved previously. In this study, tokenization is performed firstly to break up the text into individual tokens and converted to lowercase to standardize the text and make it easier to process. The codes for tokenization, stop words removals, and lemmatization are from the Internet and weekly course content: [Stack Overflow "Getting rid of stop words and document tokenization using NLTK"](https://github.com/rskrisel/web_scraping_workshop) for tokenization and [the week 7 content](https://github.com/rskrisel/web_scraping_workshop) for stop words removal and lemmitization.<br>
<br>

### ***Data Analysis***
#### ****Coutning frequency****
The first step in the data cleaning process involves creating a function to count the frequency of each confidence level in every section of the IPCC report. In the report, each statement is assigned a degree of confidence according to [the "Guidance Note for Lead Authors of the IPCC Fifth Assessment Report on Consistent Treatment of Uncertainties"](https://www.ipcc.ch/site/assets/uploads/2018/05/uncertainty-guidance-note.pdf). For each statement, the report indicates a degree of confidence following the two metrics: 'confidence in the validity of a finding' and 'quantified measures of uncertainty', which are used to categorize the degree of certainty in key findings. For the purposes of this research, the confidence levels of 'high confidence' and 'very high confidence' were grouped together as one category, as were 'low confidence' and 'very low confidence'. The resulting frequency count of each category can provide valuable insights into the overall level of certainty and tone of the IPCC report. By analyzing which sections contain more or less mentions of each confidence level, we can gain a better understanding of the level of certainty around different topics and recommendations. The code are revised based on [the webpage "Counting the frequencies in a list using dictionary in Python"](https://www.geeksforgeeks.org/counting-the-frequencies-in-a-list-using-dictionary-in-python/#) and [Stack Overlow "Word frequency using dictionary"](https://stackoverflow.com/questions/23481032/word-frequency-using-dictionary). <br>
<br>

#### ****Further data extraction by confidence level****
To facilitate sentiment analysis and TF-IDF tests, we extracted the sentences containing the phrases corresponding to different levels of confidence, as well as the preceding and following sentences. These sentences were then saved in new columns labeled 'high confidence text', 'medium confidence text', and 'low confidence text'. This approach allows for more contextual analysis of the statements, and helps to identify any patterns or trends in the use of different levels of confidence throughout the IPCC report. `nltk.sent_tokenize` method helps to split a text into a list of sentences by detecting punctuation marks that typically end a sentence. The method for exact text extraction is `extract` function using the `NLTK` library. The code to loop through all phrases is revised from [Stack Overlow 'find index of word in sentence with information from phrase'](https://stackoverflow.com/questions/69837764/find-index-of-word-in-sentence-with-information-from-phrase). Then, we define the process as a function named `extract` and apply it to all phrase by defining the parameters, `phrases = ['high confidence', 'medium confidence', 'low confidence`. <br>
<br>
In the later analysis process, there are issues with unable conducting TF-IDF texts on list. Therefore, additional steps are added to flatten the list into string using the code from [Stack Overflow "How do I make a flat list out of a list of lists?"](https://stackoverflow.com/questions/952914/how-do-i-make-a-flat-list-out-of-a-list-of-lists)<br>
<br>

#### ****Sentiment Analysis****
Sentiment analysis will provide an overview of the tone of each statement in the report as ‘positive’, ‘negative’, or ‘neutral’ along with identifying sections that express positive or negative sentiment towards certainty technologies and quantifying the level of sentiment. This helps understand which technologies or strategies are more favorable by the IPCC. The sentiments will be correlated with the associated levels of confidence, which provide an understanding of how the IPCC views the reliability of different technologies and strategies for emission reductions and whether there are discrepancies between the sentiment expressed and the associated confidence levels.<br>
<br>
There are four columns of sentiment analysis based on 1.overall processed text, high confidence text, medium confidence text, and low confidence text. The purpose is to identity the differences in patterns and trend of the sentiment among confidence levels and compared to the overwhole text. The code for the sentiment analysis is from [Week 10 "Sentiment Workshop](https://github.com/rskrisel/sentiment_analysis_workshop).<br>
<br>

#### ****TF-IDF Test****
TF-IDF will help identify the most important terms used in each section of the report which will benefit to analyze the linguistic tone and associated levels of certainty expressed in IPCC’s Sixth Assessment Report. This provides us with an understanding of words and phrases that are most closely associated with the different confidence levels and technologies or mitigation strategies mentioned in the IPCC report. For instance, if certain words or technologies are more commonly associated with low-confidence statements, it indicates potential concerns the report has towards the effectiveness or reliability of such technologies or strategies.<br>
<br>
The coding processes shares a similar approach as above - creating codes that can properly conduct TF-IDF test on one targeted row then turning into a funtion to apply the same test to the whole table. Given the study's interestes in the differences among statements with low, medium, and high confidence level, the TF-IDF test is targeting the aggregated extracted text by confidence level in each section.(corresponding to the `low confidence_text`, `medium confidence_text`, and `high confidence_text` columns in the `ipcc_processed_csv`, the dataframe). Therefore, the tf-idf score could be different if we are comparing the high confidence text in the context of the whole report. This is because the tf-idf score is calculated based on the term frequency of a word in a document and the inverse document frequency of the word. Another approach to consider TF-IDF test will be targeting by the whole preprocessed test of each section, but it was not the best fit to this specific research interest.<br>
<br>
The code for TF-IDF test is developed from [Week 12's TF-IDF class curriculum](https://github.com/rskrisel/tf-idf/blob/main/README.md), [Stack Overflow's "Meaning of TfidfVectorizer toarray() and HashingVectorizer"](https://stackoverflow.com/questions/54562820/meaning-of-tfidfvectorizer-toarray-and-hashingvectorizer), and [the webpage "Python TfidfVectorizer.fit_transform Examples"](https://python.hotexamples.com/examples/sklearn.feature_extraction.text/TfidfVectorizer/fit_transform/python-tfidfvectorizer-fit_transform-method-examples.html). <br>
<br>

## **Result and Discussion**
The IPCC's AR6 demonstrates a consistent and orbust high-confidence tone throughout the document based on our analysis. The table below summarizes the total number of mentions by confidence levels for each section. <br>

> #### *Total Number of Mention by Confidence Levels*<br>
> | Section Name | # of High Confidence | # of Medium Confidence | # of Low Confidence |
> | --- | --- | --- | --- |
> | Energy System | 140 | 26 | 4 |
> | AFLOU | 65 | 62 | 7 |
> | Industry | 14 | 4 | 0 |
> | Innovation| 20 | 7 | 0 |
> | Transport | 15 | 11 | 4 |
> | Mitigation | 178 | 54 | 5 |
> | Cross-sector | 13 | 2 | 2 |
> | National Policies | 1 | 1 | 0 |
> | International Cooperations | 18 | 12 | 3 |
> | Building | 1 | 0 | 2 |
> | Introduction | 2 | 0 | 0 |
> | Summary for Policymaker | 190 | 84 | 1 |
> | Urban System | 24 | 9 | 2 |
> | Sustainable Development | 0 | 0 | 0 |
> | Investment | 115 | 22 | 1 |
<br>
Overall, the distribution of labeled confidence levels reflects the different nature of the sections and the level of certainty associated with their content. The high count of high confidence labels in the Summary for Policymakers section suggests that the IPCC's key messages and recommendations are well-supported by scientific evidence and consensus. The high count of high confidence labels in the Mitigation and Energy sections indicates that the IPCC has a solid understanding of the potential pathways for reducing emissions and the available technologies to support the transition to a low-carbon economy.<br>
<br>
On the other hand, the high count of low confidence labels in the AFLOU section suggests that the uncertainties and complexities associated with the interactions between the climate and the land-use systems make it challenging to make precise predictions and recommendations. This observation highlights the need for further research and collaboration among scientists, policymakers, and stakeholders to address the knowledge gaps and develop effective strategies for sustainable land-use management.<br>
<br>
In summary, the distribution of labeled confidence levels provides insights into the strengths and limitations of the IPCC's report and the challenges associated with addressing the complex and interrelated issues of climate change.
<br>

### **Sentiment Analysis**
The chart shows the Compounded Sentiment Analysis Score for different sections related to climate change, with scores for high, medium, and low confidence levels. The overall score for all sections is 1.0, indicating a positive sentiment overall.<br>

> #### *Compounded Sentiment Analysis Score by Confidence Levels*<br>
> | Section Name | Overall Score | For High Confidence | For Medium Confidence | For Low Confidence |
> | --- | --- | --- | --- | ---|
> | Energy System | 1.0 | 1.0 | 0.9997| 0.9905 |
> | AFLOU | 1.0 | 0.9999 | 0.9999 | 0.9620 |
> | Industry | 1.0| 0.9986 | 0.9682 | N/A |
> | Innovation| 1.0| 0.9999| 0.9987| N/A |
> | Transport | 1.0	| 0.9996 | 0.9987 | 0.9826 |
> | Mitigation | 1.0| 1.0000 | 1.0000 | 0.9859 |
> | Cross-sector | 1.0 | 0.9997 | 0.9940 |0.9325|
> | National Policies | 1.0 | 0.9687 | 0.9687 | N/A |
> | International Cooperations | 1.0 | 0.9999 | 0.9997 | 0.7906|
> | Building | 1.0 | -0.7650 | N/A | 0.9657|
> | Introduction | 1.0 | 0.9684 | N/A | N/A |
> | Summary for Policymaker | 1.0| 1.0000| 1.0000| 0.8591|
> | Urban System | 1.0| 0.9997 | 0.9981 | 0.9062|
> | Sustainable Development | 1.0 | N/A | N/A | N/A |
> | Investment | 1.0 | 1.0000 | 0.9991 | 0.7430|
<br>
All sections receive an overall score of 1 indicating that the IPCC's report is written in an extremely positive tone. Comparing the scores across the confidence level, the scores for high confidence are generally higher and are all nearly equal to 1 (the most positive tone) with the exception of the building section. One possible reason for the low sentiment score in the building section is the vocabulary used to express low evidence in the statements and the content itself, which concerns the damage of inaction. For instance, the chapter states, 'Repurposing existing non-residential buildings, no longer in use due to the expected spread of teleworking triggered by the health crisis and enabled by digitalisation, could be the way to overcome the new needs for office and school buildings triggered by the health crisis (low evidence, high confidence).' Words like 'trigger,' 'crisis,' and 'low' can result in a negative score for the text.<br>
<br>
Cross-row comparison shows that the Mitigation and Summary for Policymaker sections have the highest scores across all confidence levels, indicating a consistently positive sentiment in those sections. The result is the same as the rank of the number of high confidence count. <br>
<br>

### **TF-DIF Test**
The chart below provides the top five words mentioned with high, medium, and low confidence levels in different sections, excluding interfering words. Interfering words are defined here as any words that do not provide specific information for the given chapter. This is a manual revision process used to select the top 5 words with the most mentions by confidence level. Digits, units, overarching terms (e.g., words like climate, change, confidence, and 'year' that do not provide detailed information for the audience to understand the content of the reports) are excluded. Therefore, the following chart might be biased depending on the audience group. In this study, we are primarily interested in understanding the linguistic tones for the mitigation pathways and technology.<br>

> #### *Top 5 words mentioned by confidence level (Excluding interfering words)*
> | Section Name | High Confidence  | Medium Confidence | Low Confidence |
> | --- | --- | --- | --- |
> | Energy System | energy(0.468) <br>cost(0.163) <br>electricity(0.1415)<br> carbon(0.131) <br>fossil fuel(0.109)| energy(0.261)<br> warming (0.228) <br>electricity(0.206)<br> cost(0.163)<br> use(0.141) | wind(0.277) <br>climate & effect (0.185)<br>carbon (0.138)<br> enablers(0.138) <br> impact (0.138) |
> | AFLOU | emission(0.306)<br>mitigation(0.263)<br>AFOLU(0.195)<br>Potential(0.136)<br>land(0.137) | emission(0.254)<br>potential(0.238)<br>mitigation(0.184)<br>land(0.123)<br> global(0.119) | carbon(0.251)<br>potential(0.215)<br>change(0.179)<br>mitigation(0.179)<br>coastal(0.108) |
> | Industry | material(0.260)<br>energy(0.137)<br>efficiency(0.122)<br> industry & use (0.121) | emission(0.474)<br>cost(0.189)<br>cement(0.142)<br>production & source(0.142)<br> | N/A |
> | Innovation| innovaton(0.477)<br>technology(0.218)<br>development (0.166)<br>system(0.145)<br>country(0.103) | technology(0.298)<br>country(0.178)<br>mitigation(0.178)<br>climate & development (0.149) | N/A |
> | Transport | fuel(0.195)<br>hydrogen(0.156)<br>carbon(0.130)<br>demand(0.117)<br>sector(0.117) | carbon(0.168)<br>electric(0.151)<br>hydrogen(0.151)<br>system(0.135)<br>decarbonization(0.118) | aviation(0.221)<br>fuel(0.221)<br>land(0.221)<br>shipping(0.221)<br>contrail(0.133) |
> | Mitigation | emission(0.359)<br>mitigation(0.225)<br>pathway(0.175)<br>warming(0.149)<br>carbon(0.120) | emission(0.293)<br>mitigation(0.213)<br>warming(0.192)<br>change(0.187)<br>energy(0.155) | emission(0.392)<br>aggregate(0.142)<br>2019(0.178)<br>carbon(142) <br> economic(0.142)|
> | Cross-sector | land(0.253)<br>use(0.179)<br>production(163)<br>united(0.147)<br>food(0.130) | trade(0.267)<br>biomass(0.200)<br>governance(0.200)<br>technology(0.200)<br>coordinated & climate (0.133) | effect(0.235)<br>enablers(0.240)<br>acceptance(0.157)<br>air(0.157)<br>assessment(0.157)<br>barrier(0.157) |
> | National Policies | emission(0.256)<br>subsidy(0.256)<br>agreeement(0.171)<br>evidence(0.171)<br>fossil & fuel (0.171) | emission(0.256)<br>mitigation(0.256)<br>subsidy(0.256)<br>agreement(0.171)<br>evidence (0.171) | N/A |
> | International Cooperations | agreement(0.234)<br>cooperation(0.235)<br>support(0.122)<br>development(0.112)<br>emission(0.112) | aggrement(0.281)<br>level(0.252)<br>Paris(0.192)<br>ambition(0.163)<br>cooperation(0.148) | impact(0.186)<br>reduction(0.187)<br>scenario(0.187)<br>surface(0.187)<br>change(0.125) |
> | Building | building(0.543)<br>new(0.232)<br>crisis(0.155)<br>health(0.155)<br>need(0.155)<br>residential(0.155) | N/A | effect(0.247)<br>enablers(0.247)<br>acceptance(0.165)0<br>air(0.165)<br>barrier(0.165) |
> | Introduction | Pathway(0.273)<br>ipcc(0.205)<br>ndcs(0.205)<br>overshoot(0.205)<br>emission(0.136) | N/A | N/A |
> | Summary for Policymaker | emission (0.365)<br>mitigation(0.196)<br>energy(0.138)<br>pathway(0.118)<br>warming(0.104)| mitigation(0.218)<br>global(0.166)<br> pathway(0.152)<br>policy(0.131)<br> national(0.112) | CO2(0.320)<br> 2019(0.204)<br> high(0.240)<br> occurred(0.240)<br> growth(0.160)  |
> | Urban System | urban(0.482)<br> city(0.250)<br> infrastructure(0.232)<br> climate(0.142)<br> mitigation(0.135)| urban(0.513)<br> emission(0.218)<br> increased(0.202)<br> person(0.140)<br> region(0.140) | urban(0.372)<br> effect(0.186)<br> enablers(0.186)<br> land(0.186)<br> strategy(0.186) |
> | Sustainable Development | N/A | N/A | N/A |
> | Investment | climate(0.397)<br> financial(0.229)<br> risk(0.212)<br> investment(0.176)<br> finance(0.171) | investment(0.215)<br> climate(0.190)<br> market(0.152)<br> scenario(0.152)<br> energy(0.139) | bound(0.280)<br> energy(0.280)<br> estimate(0.280)<br> number(0.280)<br> reported(0.280) |
<br>
From the chart, the energy systems, AFLOU, and mitigation sections all have the word "emission" as one of the most frequently mentioned. "Carbon" is another commonly mentioned word across several sections such as Energy Systems, AFLOU, Mitigation, and Transport sections. "Mitigation" itself is a frequently mentioned word in both the Mitigation and AFLOU sections. <br>
<br>
Some important takeaways from the TF-IDF test are:<br>
<br>
1. Statements with high confidence labels for the industry section cover "materials", "efficiency", and "use". The section emphasizes the importance of the energy emission-intensive and basic material industries as key strategies for reaching net-zero emissions. It highlights the importance of materials and energy efficiency in emission reduction, in line with the IPCC's view.<br>
<br>
2. "Aviation" is the most frequently mentioned word among statements with low confidence labels for the transport sector. It reflects the diversified discussions on the decarbonization strategies for the aviation sector. In contrast, "hydrogen", "fuel", and "electric" are frequently mentioned in the high-confidence statements. This suggests that the IPCC's position is to decarbonize the transport sector through fuel transitions from carbon-intensive sources to renewables.<br>
<br>
3. "Economic" is one of the most frequently mentioned words in the low-confidence statements from the mitigation sector, indicating the IPCC's concerns and uncertainty towards the economic impact of different mitigation strategies.<br>

## **Conclusionn**
This study aims to offer an analysis of the linguistic tone found within the IPCC's sixth assessment report on emission mitigation pathways and sector-specific discussions. The findings have implications for researchers seeking to understand the report's key themes and the optimistic attitudes of the IPCC towards climate change. It should be noted that further data cleaning is necessary to draw nuanced conclusions about the linguistic tone used across different sectors and technologies. Nevertheless, this study provides a solid foundation and introduction for interested audiences.