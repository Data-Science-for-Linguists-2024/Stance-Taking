# Stancetaking in Spontaneous Speech
by Maya Asher, 4/28/24
## 1. Introduction
Using the spontaneous speech from the [Santa Barbara Corpus of Spoken American English](https://www.linguistics.ucsb.edu/research/santa-barbara-corpus) (SBCSAE), this project investigates the use and frequency of lexical items and discourse markers for indicating investment. This project was conducted as my term project for Data Science for Linguists taught by Dr. Na-Rae Han at the University of Pittsburgh. 
## 2. Theoretical Background
### What is stance?
Stance and stancetaking, often used interchangably, refer to the ways in which people position themselves in conversations (Kiesling, 2022). An interlocutor's stance may be dictated by their level of politeness, certainty, and/or emotion toward their interactants and the objects of conversation (Kiesling, 2022). It is an important feature of discourse analysis because it helps explain the patterning of language and the motivations for the use of lexical items, constructions, and discourse markers. There are many different theories on how stance is constructed, but this project is based on Dr. Scott Kiesling's theory.
### The Stance Triangle
As Dr. Kiesling discusses in his paper "Stance and Stancetaking" (2022), stance is how people position themselves in conversations and it can be analyzed using a three-dimensional model that encompasses **evaluation**, **alignment**, and **investment**. In a simple conversation, animator A evaluates an object, prompting animator B to also evaluate that object, resulting in an alignment or disalignment between the two interlocutors. Investment is the extent to which each person commits to their evaluation.

![stance-triangle](/figures/Du-Bois-2007.png) 

(Du Bois, 2007, as cited in Kiesling, 2022, p. 418)

So, for example, if I were to say *"I really love data science,"* I am indexing a large amount of investment to my evaluation of data science. Then, if my interlocutor were to respond, *"I kind of like data science,"* we are somewhat aligning by speaking of data science in a positive light, but they are indexing less investment in their evaluation than I am. Investment can also be indicated through epistemicity and evidentiality, but for the purposes of this project, we will be focusing on lexical items and discourse markers. 

In the three-dimensional model of analysis mentioned above, there are also three different participant roles: the **author** who composes the essential text, the **animator** who produces the speech, and the **principal** who takes responsibility for the utterance (Kiesling, 2022). This project will mainly focus on the animators, but the other terms are crucial, especially for quoted speech.
### Why spontaneous speech? 
Before discussing my choice of data, it is important to understand the difference between read speech and spontaneous speech. The two types of speeches position their tone boundaries, stress, and pauses in different places, making them audibly distinct (Howell & Kadi-Hanifi, 163). Read speech tends to be more fluid and constructed, while spontaneous speech incurs many more pauses and interruptions. In the field of discourse analysis, a heavy emphasis is placed on natural interactions between interlocutors, so I took extra care to find a corpus of natural, spontaneous speech. 
## 3. Data 
### Sourcing
As previously mentioned, the corpus I chose for this study was the Santa Barbara Corpus of Spoken American English (SBCSAE), which includes 60 recordings/transcripts, totaling in ~249,000 words (Du Bois, et al., 2000-2005). Since I was only interested face-to-face spontaneous speech, I excluded 17 files which were everything from lectures and meetings to storytelling and phone calls. So, in the end I worked with 43 transcripts.

The SBCSAE includes conversations from all over the United States, encompassing a wide variety of people with different regional origins, ages, occupations, genders, and ethnic and social backgrounds.
### Clean-up and Processing
The files themselves are tab-separated and have columns for time stamps, speaker names (which were pseudonyms), and the text. The text includes a large amount of conventional symbols that are used to indicate many things like overlaps, pauses, pitch, quality, tone, and transcriber's notes, among others. Luckily, an annotation key was provided to disambiguate the symbols.

![SBC001-excerpt](/figures/SBC001-excerpt.png) 

(Du Bois, et al., 2000-2005)

To [process these files](https://github.com/Data-Science-for-Linguists-2024/Stance-Taking-in-Spontaneous-Speech/blob/main/notebooks/reprocessing_sbcsae.ipynb#Read-in-files), I read them in and stored them in individual pandas dataframes, leaving me with a single dictionary containing 43 dfs. I ran into some column issues, but the issues were resolved simply by being consistent with column names. 

From there, I [extracted my target words](https://nbviewer.org/github/Data-Science-for-Linguists-2024/Stance-Taking-in-Spontaneous-Speech/blob/main/notebooks/analyzing_sbcsae.ipynb#Extract-targets), which were 'like', 'love', 'fine', 'good', 'great', 'I mean', 'might', 'alway', 'maybe', and 'very'. I then [outputted](https://nbviewer.org/github/Data-Science-for-Linguists-2024/Stance-Taking-in-Spontaneous-Speech/blob/main/notebooks/analyzing_sbcsae.ipynb#Pipeline-for-outputs) every occurrence of each target word in 20 lines of context. These [output files](https://github.com/Data-Science-for-Linguists-2024/Stance-Taking-in-Spontaneous-Speech/tree/main/targets_w_context) (example below) facilitated the annotation part of this project. 

![love-output](/figures/love-output.png) 

### Value Add
To add value to this very impressive data set, I decided to create annotations indicating the investment of certain lexical items and discourse markers. To do this, I read through each occurrence in context and used the [file summaries](https://github.com/Data-Science-for-Linguists-2024/Stance-Taking-in-Spontaneous-Speech/blob/main/file_summary.md) to better understand the scenario. I then made a judgement as to whether the target word indicated a *higher investment* in the evaluation being made (labeled `H`), or a *lower investment* (labeled `L`). This process proved to be rather difficult and tedious, so I only got through 4 of the 10 target word files; however, in the future I hope to get through the rest of them to further deepen the analysis. 

After annotating the data, I then exported them to separate [text files](https://github.com/Data-Science-for-Linguists-2024/Stance-Taking-in-Spontaneous-Speech/tree/main/annotations) and [reprocessed them](https://nbviewer.org/github/Data-Science-for-Linguists-2024/Stance-Taking-in-Spontaneous-Speech/blob/main/notebooks/analyzing_sbcsae.ipynb#Analyze-the-annotated-data) for analysis purposes. I created a dataframe where the rows were the file name (SBC001-SBC060) and the columns were the target words ('maybe', 'love', 'great', 'fine'). The values were a list of tuples: (index, H or L). From this data, I was able to extract the counts of H and L for both the rows and columns, which will facilitate my analysis. 
## 4. Analysis
With the data processed and annotated, I am finally able to address my research questions:
1. Which lexical item/discourse marker is used most frequently in this corpus? 
2. Which is most informative of the animator’s investment?
3. What generalizations can be made for the investment level of each item/marker?
### Research Question 1
Since I was unable to get through all 10 of my target words, I can only partly answer this question. 

![hl_counts](/figures/hl_counts.png) 

Of the 4 words, 'maybe' has the highest token count across the 43 transcripts. There are two potential reasons for this substaintial influx in tokens: repetition and multiple meanings. Of all 4 target words, 'maybe' had the most repetition, most likely because it is a sort of questioning item that presents multiple options (see below).

![maybes](/figures/maybes.png) 

Aside from its use as a discourse marker, 'maybe' can also be used as a form of estimation: for example, "There were maybe fourty people there". In this example, 'maybe' is not being used as a hedge, but rather as an approximation. 
### Research Question 2
### Research Question 3

## 5. Reflection
### History
### Future Steps
## 6. References
Du Bois, J. W. (2007). The stance triangle. Stancetaking in Discourse: Subjectivity, Evaluation, Interaction, ed. by Robert Englebretson, 139–182

Du Bois, J. W., Chafe, W. L., Meyer, C., Thompson, S. A., Englebretson, R., & Martey, N. (2000-2005). Santa Barbara corpus of spoken American English, Parts 1-4. Philadelphia: Linguistic Data Consortium

Howell, P., & Kadi-Hanifi, K. (1991). Comparison of prosodic properties between read and spontaneous speech material. Speech Communication, 10(2), 163–169. https://doi.org/10.1016/0167-6393(91)90039-V

Kiesling, S. F. (2022). Stance and Stancetaking. Annual Review of Linguistics, 8, 409-426. https://doi.org/10.1146/annurev-linguistics-031120-121256

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



can see which interviews have the highest counts and relate it back to the topics! (0023 is a discussion abt a book i think so it makes sense that there is a lot of hedging)