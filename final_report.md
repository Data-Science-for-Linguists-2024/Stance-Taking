Think of this as a usual “final report” that is in a markdown format instead of MS Word. Details:

Shoot for around 1,500 words, excluding references if any. That’s the length of a short paper of about 4-5 pages. (Remember to use the wc command!)

Use headers and clearly mark your sections.

Use visualization! Display figures you had saved as external image files. Example here.

Link to relevant parts of your Jupyter Notebook. As explained above, you should reference sections of your code on jupyter.org’s nbviewer. See this example.

What should you include in this report? Revisit the overall description of the term project at the top of this page.
Have a paragraph devoted to the overall history and process of your project, warts and all. Document setbacks, false starts, and other difficulties you experienced.


A. Data
Start with found data. Many linguistics research projects begin with a targeted data collection effort – field work, surveys, elicitation, human subjects, and more. But the underlying assumption of data science is that data exists in the wild, and it is up to a data scientist to harness it. True to this assumption, we will have you start with data that is found in the wild, be it published data sets, corpora, or social media streams.

Add value. You should not, however, be content with data as it is packaged and presented to you. In many cases, your data will need a lot of work – sourcing, cleaning up, and reorganizing. In other cases, you may be dealing with published data that’s more or less ready for analysis. You are, then, expected to add value: augmenting, annotating and leveraging multiple data sets are all potential avenues.

Follow best data practices. Throughout this semester, we will be learning about best data practices, both emerging and firmly established in data science circles. Make sure your own data efforts and the output are in compliance.

B. Analysis
Linguistic analysis. You will have designed your data with a research question in mind. Your data should make a suitable empirical basis for your linguistic inquiry; your research question should be properly motivated and addressed in a theoretically and methodologically sound manner. You interpretations of the findings should likewise be rigorously supported by your data. Even with meticulous preparation, however, your data in the end may not prove fruitful grounds for your original research question. Pivoting is therefore allowed up to a certain point; whether or not this move is ultimately successful, reasons for pivoting and/or failure of the original research agenda must be thoroughly probed and documented, since this sort of outcome is all part and parcel in research efforts deeply grounded in real-life data and, further, provides valuable insight.

Computational methods. In your linguistic analysis, you are expected to employ various computational methods including natural language processing, statistics, machine learning, topic modeling and more. Proper techniques should be used in accordance with your research question and the specifics of your data. At the same time, you should demonstrate mastery of these techniques by justifying your choice of computational methods and thoroughly evaluating the outcome, rather than blindly applying them and accepting the returned output. As with linguistic analysis, failed experimentation should not be brushed aside, but rather receive proper investigation and documentation, as this is all part of the discovery process.

C. Presentation
This component encompasses all audience-facing aspects of your project, which include but are not limited to:

Proper use of GitHub as a project-hosting and publication platform.
Overall documentation.
Structure, readability and organization of your Python code in the form of Jupyter notebooks.
Visualization through graphs and plots.
Your oral presentation, scheduled in the last two weeks of class.
Your final report: language, content, clarity, precision, organization, citation, etc.
Weight distribution. Ideally, a project will have the three components in perfect balance: a total of say 180 points will be equally split between data/analysis/presentation as 60-60-60. In reality, everyone’s project will be different: some will have ambitious and challenging data curation plans, while others might wish to focus their efforts on extensive use of advanced computational methods. To accommodate this, a limited amount of trade-off is provisioned between the “data” and the “analysis” components: more data-focused projects therefore may have up to 70-50-60 distribution with more data-side contribution, while projects heavily focused on analysis are allowed to go easier on data-related efforts, with up to 50-70-60 split.

#==============================================

# Stancetaking in Spontaneous Speech
by Maya Asher, 4/28/24
## 0. Introduction
Using the spontaneous speech from the [Santa Barbara Corpus of Spoken American English](https://www.linguistics.ucsb.edu/research/santa-barbara-corpus) (SBCSAE), this project investigates the use and frequency of lexical items and discourse markers for indicating investment. This project was conducted as my term project for Data Science for Linguists taught by Dr. Na-Rae Han at the University of Pittsburgh. 
## 1. Theoretical Background
### What is stance?
Stance and stancetaking, often used interchangably, refer to the ways in which people position themselves in conversations (Kiesling 2022). An interlocutor's stance may be dictated by their level of politeness, certainty, and/or emotion toward their interactants and the objects of conversation (Kiesling 2022). It is an important feature of discourse analysis because it helps explain the patterning of language and the motivations for the use of lexical items, constructions, and discourse markers. There are many different theories on how stance is constructed, but this project is based on Dr. Scott Kiesling's theory.

### The Stance Triangle
As Dr. Kiesling discusses in his paper "Stance and Stancetaking" (2022), stance is how people position themselves in conversations and it can be analyzed using a three-dimensional model that encompasses **evaluation**, **alignment**, and **investment**.

![stance-triangle](/figures/Du-Bois-2007.png) (Du Bois, 2007, as cited in Kiesling, 2022, p. 418)

In a simple conversation, animator A evaluates an object, prompting animator B to also evaluate that object, resulting in an alignment or disalignment between the two interlocutors. Investment is the extent to which each person commits to their evaluation.

So, for example, if I were to say *"I really love data science,"* I am indexing a large amount of investment to my evaluation of data science. Then, if my interlocutor were to respond, *"I kind of like data science,"* we are somewhat aligning by speaking of data science in a positive light, but they are indexing less investment in their evaluation than I am. Investment can also be indicated through epistemicity and evidentiality, but for the purposes of this project, we will be focusing on lexical items and discourse markers. 

In the three-dimensional model of analysis mentioned above, there are also three different participant roles: the **author** who composes the essential text, the **animator** who produces the speech, and the **principal** who takes responsibility for the utterance. This idea will be explored later on in the analysis.
## 2. Data 
### Sourcing
### Clean-up and Processing
### Value Add
## 3. Analysis
### Research Questions
## 4. Reflection
### History
### Future Steps
## 5. References
Du Bois, J. W. (2007). The stance triangle. Stancetaking in Discourse: Subjectivity, Evaluation, Interaction, ed. by Robert Englebretson, 139–182

Du Bois, J. W., Chafe, W. L., Meyer, C., Thompson, S. A., Englebretson, R., & Martey, N. (2000-2005). Santa Barbara corpus of spoken American English, Parts 1-4. Philadelphia: Linguistic Data Consortium

Howell, P., & Kadi-Hanifi, K. (1991). Comparison of prosodic properties between read and spontaneous speech material. Speech Communication, 10(2), 163–169. https://doi.org/10.1016/0167-6393(91)90039-V

Kiesling, S. F. (2022). Stance and Stancetaking. Annual Review of Linguistics, 8, 409-426. https://doi.org/10.1146/annurev-linguistics-031120-121256

Wang, J., & Jiang, F. (Kevin). (2018). Chapter 9. Epistemic stance and authorial presence in scientific research writing: Hedges, boosters and self-mentions across disciplines and writer groups. In P. Mur-Dueñas & J. Šinkūnienė (Eds.), AILA Applied Linguistics Series (Vol. 18, pp. 195–216). John Benjamins Publishing Company. https://doi.org/10.1075/aals.18.09wan

#==============================================


ISSUES: capitalization in regex for the words (just ran out of time)



SBC031.trn
    time_start  time_end    speaker     text
560     530.602   532.612  ROSEMARY:   ... There's not enough lemon there to bother me.
561     532.612   533.055              Thank [you].
562     532.889   533.430     JAMIE:   [O]kay.
563     533.430   535.342    SHERRY:   (H) But it tastes so good with lemon in it.
564     535.342   537.730              ... @I @don't even like ice tea. 
565     537.730   539.521      BETH:   .. (H) ... Do you like hot tea?
566     539.521   540.419    SHERRY:   ... Yeah,
567     540.419   541.201              I love hot tea.
568     541.201   541.677      BETH:   .. (SNIFF)
569     541.677   542.316  ROSEMARY:   (H)=  
570     542.316   545.957    SHERRY:   ... But the winter hasn't bl[asted cold enough... 
571     544.775   546.179  ROSEMARY:   [Do you put lemon in your hot] [2tea2]?
572     545.957   546.845      BETH:   [2I'm2] going to today,
573     546.845   547.795              cause I have a sore throat. 



NOTES on MAYBE
- lots of repetition with `maybe`
- `maybe` can also mean like an estimation, which I didn't include as a discourse marker
- seems to be used often out of politeness so that the animator isn't just stating a fact but rather proposing a potential idea

can see which interviews have the highest counts and relate it back to the topics! (0023 is a discussion abt a book i think so it makes sense that there is a lot of hedging)