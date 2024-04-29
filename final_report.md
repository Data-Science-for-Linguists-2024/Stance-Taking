# Stancetaking in Spontaneous Speech
by Maya Asher, 4/28/24
## 1. Introduction
Using the spontaneous speech from the [Santa Barbara Corpus of Spoken American English](https://www.linguistics.ucsb.edu/research/santa-barbara-corpus) (SBCSAE), this project investigates the use and frequency of lexical items and discourse markers for indicating investment. This project was conducted as my term project for Data Science for Linguists taught by Dr. Na-Rae Han at the University of Pittsburgh. 
## 2. Theoretical Background
### What is stance?
Stance and stancetaking, often used interchangeably, refer to the ways in which people position themselves in conversations (Kiesling, 2022). An interlocutor's stance may be dictated by their level of politeness, certainty, and/or emotion toward their interactants and the objects of conversation (Kiesling, 2022). It is an important feature of discourse analysis because it helps explain the patterning of language and the motivations for the use of lexical items, constructions, and discourse markers. There are many different theories on how stance is constructed, but this project is based on Dr. Scott Kiesling's theory.
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
The files themselves are tab-separated and have columns for time stamps, speaker names (which were pseudonyms), and the text. The text includes a large number of conventional symbols that are used to indicate many things like overlaps, pauses, pitch, quality, tone, and transcriber's notes, among others. Luckily, an annotation key was provided to disambiguate the symbols.

![SBC001-excerpt](/figures/SBC001-excerpt.png) 

(Du Bois, et al., 2000-2005)

To [process these files](https://github.com/Data-Science-for-Linguists-2024/Stance-Taking-in-Spontaneous-Speech/blob/main/notebooks/reprocessing_sbcsae.ipynb#Read-in-files), I read them in and stored them in individual pandas dataframes, leaving me with a single dictionary containing 43 dfs. I ran into some column issues, but the issues were resolved simply by being consistent with column names. 

From there, I [extracted my target words](https://nbviewer.org/github/Data-Science-for-Linguists-2024/Stance-Taking-in-Spontaneous-Speech/blob/main/notebooks/analyzing_sbcsae.ipynb#Extract-targets), which were 'like', 'love', 'fine', 'good', 'great', 'I mean', 'might', 'always', 'maybe', and 'very'. I then [outputted](https://nbviewer.org/github/Data-Science-for-Linguists-2024/Stance-Taking-in-Spontaneous-Speech/blob/main/notebooks/analyzing_sbcsae.ipynb#Pipeline-for-outputs) every occurrence of each target word in 20 lines of context. These [output files](https://github.com/Data-Science-for-Linguists-2024/Stance-Taking-in-Spontaneous-Speech/tree/main/targets_w_context) (example below) facilitated the annotation part of this project. 

![love-output](/figures/love-output.png) 

### Value Add
To add value to this very impressive data set, I decided to create annotations indicating the investment of certain lexical items and discourse markers. To do this, I read through each occurrence in context and used the [file summaries](https://github.com/Data-Science-for-Linguists-2024/Stance-Taking-in-Spontaneous-Speech/blob/main/file_summary.md) to better understand the scenario. I then made a judgment as to whether the target word indicated a *higher investment* in the evaluation being made (labeled `H`), or a *lower investment* (labeled `L`). This process proved to be rather difficult and tedious, so I only got through 4 of the 10 target word files; however, in the future I hope to get through the rest of them to further deepen the analysis. 

After annotating the data, I then exported them to separate [text files](https://github.com/Data-Science-for-Linguists-2024/Stance-Taking-in-Spontaneous-Speech/tree/main/annotations) and [reprocessed them](https://nbviewer.org/github/Data-Science-for-Linguists-2024/Stance-Taking-in-Spontaneous-Speech/blob/main/notebooks/analyzing_sbcsae.ipynb#Analyze-the-annotated-data) for analysis purposes. I created a dataframe where the rows were the file name (SBC001-SBC060) and the columns were the target words ('maybe', 'love', 'great', 'fine'). The values were a list of tuples: (index, H or L). From this data, I was able to extract the counts of H and L for both the rows and columns, which will facilitate my analysis. 
## 4. Analysis
With the data processed and annotated, I am finally able to address my research questions:
1. Which lexical item/discourse marker is used most frequently in this corpus? 
2. What generalizations can be made for the investment level of each item/marker?
3. Are there contexts where some `H` or `L` items/markers are used more than others?
### Research Question 1
Since I was unable to get through all 10 of my target words, I can only partly answer this question. 

![hl_counts](/figures/hl_counts.png) 

Of the 4 words, 'maybe' has the highest token count across the 43 transcripts. There are two potential reasons for this substantial influx in tokens: repetition and multiple meanings. Of all 4 target words, 'maybe' had the most repetition, most likely because it is a sort of questioning item that presents multiple options (see below).

![maybes](/figures/maybes.png) 

Aside from its use as a discourse marker, 'maybe' can also be used as a form of estimation: for example, "There were maybe forty people there". In this example, 'maybe' is not being used as a hedge, but rather as an approximation. 
### Research Question 2
To answer this question, it is helpful to look at the normalized graph below.

![normalized](/figures/norm_counts.png) 

It is clear that 'maybe' is used by an animator to lower their investment in their evaluation, and 'love' is used to higher their investment, but there is some ambiguity for 'great' and 'fine'. In most cases, 'great' is used to higher investment, which makes sense because it is generally a positive adjective and discourse marker; however, in some scenarios 'great' was used dismissively and unenthusiastically, which lowers the animator's investment. On the other hand, we have 'fine', which, when used as a discourse marker, is a pretty neutral descriptor. But, there were cases where the preceding context was negatively evaluating the object of conversation, and the animator uses 'fine' to evaluate the object more positively, highering their investment.

In general, 'maybe' and 'fine' index lower investment and 'love' and 'great' index higher investment, but there do exist exceptions to this norm.
### Research Question 3
Taking a look at top counts of `H` and `L`, it becomes clear that some transcripts include a great deal of items/markers that higher/lower investment. 

![top_counts](/figures/top_counts.png) 

From the [file summary](https://github.com/Data-Science-for-Linguists-2024/Stance-Taking-in-Spontaneous-Speech/blob/main/file_summary.md), we can make connections between the influx of Hs and Ls and the content of the conversations.

The transcripts with the highest amount of `H` markings were mostly between friends and family on special occasions of sorts. SBC003, SBC015, and SBC051 are all conversations between couples and their friends, and the friends are from out of town in SBC003 and SBC051. Being adult friends, and some of them being out of town, it makes sense that they would want to indicate their investment and excitement to be talking to one another. Similarly, SBC048 is from Christmas morning's gift exchange, SBC016 is a sales encounter, and SBC056 is a speaker raving about her new pony – all 3 conversations are showing off new things, so the use of 'love' and 'great' is bound to occur.

The transcripts with the highest amount of `L` markings can be broken into two categories: people who know each other really well and strangers/acquaintances. SBC005 is a conversation between a couple lying in bed and SBC043 is a conversation between a mother and daughter. Given the familiarity of the interlocutors, a lack of investment is more permissible and can be a sign of their understanding of each other. On the other hand, SBC023 is a book club conversation and SBC029 is a business conversation where an estimate is being given. The interlocutors in these conversations give the feeling that they don't want to step on the other interlocutors' toes, so they may hedge more and utilize 'maybe' and 'fine'. 
## 5. Reflection
### History
I began this project with grand ideas and a strong theoretical basis, but in the end I bit off more than I could chew and only produced a fraction of what I had hoped. I was completely lost when it came to processing the data. I tried a lot of different things (as you can see in [my initial processing notebook](https://nbviewer.org/github/Data-Science-for-Linguists-2024/Stance-Taking-in-Spontaneous-Speech/blob/main/notebooks/processing_sbcsae.ipynb)) but after a while I was finally able to produce [something useable](https://nbviewer.org/github/Data-Science-for-Linguists-2024/Stance-Taking-in-Spontaneous-Speech/blob/main/notebooks/reprocessing_sbcsae.ipynb#Read-in-files). With that data, I was able to mess around with pandas dataframes, file I/O, subgrouping, and more. I then annotated the extracted outputs and analyzed it to answer my research questions. Though I wish I could've achieved more, I am proud of what I accomplished. 

### Motivation
My original motivation for choosing this topic stemmed from experience taking Discourse Analysis two years ago with Dr. Scott Kiesling and from working with speech data in Dr. Dan Villarreal's Computational Sociolinguistic lab. I really enjoyed conducting small-scale discourse analyses in class and I have found that I much prefer speech data over text data, so for this project my goal was to conduct a large-scale discourse analysis on speech data. However, everything I touch seems to turn into research, so I think I spent a little too much time on the theoretical basis and not enough time on the actual data science aspect of the project. With the skill I have now, I probably could've gotten the data processed within a week and had the rest of the semester to annotate and analyze...but alas, hindsight is 20/20.

## 6. References
Du Bois, J. W. (2007). The stance triangle. Stancetaking in Discourse: Subjectivity, Evaluation, Interaction, ed. by Robert Englebretson, 139–182

Du Bois, J. W., Chafe, W. L., Meyer, C., Thompson, S. A., Englebretson, R., & Martey, N. (2000-2005). Santa Barbara corpus of spoken American English, Parts 1-4. Philadelphia: Linguistic Data Consortium

Howell, P., & Kadi-Hanifi, K. (1991). Comparison of prosodic properties between read and spontaneous speech material. Speech Communication, 10(2), 163–169. https://doi.org/10.1016/0167-6393(91)90039-V

Kiesling, S. F. (2022). Stance and Stancetaking. Annual Review of Linguistics, 8, 409-426. https://doi.org/10.1146/annurev-linguistics-031120-121256