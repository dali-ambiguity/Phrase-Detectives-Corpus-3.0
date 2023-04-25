# Phrase Detectives Corpus 3.0

Jon Chamberlain, Silviu Paun, Juntao Yu, Udo Kruschwitz and Massimo Poesio
Release date: April 2023

This is a corpus of anaphorically annotated documents, consisting of
all the  documents completely annotated as of 19th January 2022 using
the  Phrase Detectives game-with-a-purpose: 

	   https://www.phrasedetectives.org

# Download

The corpus is avaliable at this [link]().

# The Documents

A total of 805 documents are included, for a total of 1.37M tokens and
383K markables. The documents are divided in:

* a 'new_gold' subset of 20 documents (43K tokens, 13K markables) annotated
  both by Phrase Detectives players and by two experts. This subset is newly annotated by experts according to a simplified version of the ARRUR annotation guideline (Uryupina et al., 2020). It is currently held by us and will be used as a test set for a new shared task we are proposing in the near future. In addition to the gold annotation, a 'silver' annotation is
  included, extracted using the [Mention Pair Annotation (MPA)](https://github.com/SilviuPaun/Mention-Pair-Annotations-model) probabilistic
  aggregation method for coreference discussed in the paper:

  Silviu Paun, Jon Chamberlain, Udo Kruschwitz, Juntao Yu and Massimo
  Poesio, 2018. [A Probabilistic Annotation Model for Crowdsourcing
  Coreference](https://aclanthology.coli.uni-saarland.de/papers/D18-1218/d18-1218). In Proc. of EMNLP.

* a 'gold' subset of 45 documents (23K tokens, 6K markables) annotated
  both by Phrase Detectives players and by two experts. This subset is
  a cleaned-up version of the Phrase Detectives 1.0 corpus released in
  2016. Similar to the 'new_gold' subset the 'silver' annotation is also included.
  

* a 'silver' subset of 740 documents (1.3M tokens, 363K markables) for
  which only the silver MPA annotation is provided.

The silver subset consists of documents  from two separate genres:

* Wikipedia pages (544 documents, 931K tokens, 258K markables)
* fiction from the Project Gutenberg collection (194 documents, 372K
                   tokens, 102K markables)

The gold subset consists of documents from three genres:

* Wikipedia pages (35 docs, 15287 tokens, 4423 markables)
* fiction from the Project Gutenberg collection (5 documents, 7536
                   tokens, 2133 markables)
* art history texts from the GNOME corpus (5 documents, 989 tokens,
                   331 markables)	
                   
The new_gold subset consists of document from two genres:             
* Wikipedia pages (13 docs, 22998 tokens, 7704 markables)
* fiction from the Project Gutenberg collection (7 documents, 20646
                   tokens, 5925 markables)

Overall, 580 of the total 805 documents are 'complete' annotated by the player. A document is considered 'complete' if all its markables have at least
8 annotations and each interpretation has been validated by at least
4 players. On average, 20.6 annotations per markable are present. For those documents that are not 'completely' annotated, a coreference system ([Yu et al., 2020](https://aclanthology.org/2020.lrec-1.2)) is used as an additional artificial player.

# Markup formats

The documents are provided in three different formats: MAS-XML, CONLL,
and CONLLUA.

MAS-XML

This is the format used for the original release of the corpus. It is
an inline XML format, in which each markable is identified with an
\<ne\> element, and anaphoric annotation is stored using \<PDante\>
elements containing in turn \<anchor\> elements specifiying annotations
and validations (all annotations and validations are provided) and
\<comment\> elements with additional information provided by the
players. Details for \<PDante\> and \<anchor\> are as follows: 

\<PDante\>  
id = id of the markable  
visibility = whether the administrator marked this to be "hidden"  
start_chr = the markable span was edited and the new start character is this  
end_chr = the markable span was edited and the new end character is this  

\<anchor\>  
timestamp = time the annotation was created  
interface = interface the annotation was created on (0 = standalone PD, 1 = Facebook PD)  
mode = mode of annotation (a = annotation, v = validation, e = expert)  
agree = was this annotation in agreement with the interpretation  
annotation_time = time to create the annotation response from page load  
user_rating = rating of the user  
user_id = encrypted user_id  
type = interpretation type (DN = Discourse New, DO = Discourse Old, NR = Non-referring, PR = Property, SE = same entitiy)  
ante = antecedent markable id  
favoured = the expert indicates whether this is the best interpretation (y) or another might be better  

\<comment\>  
type/type_id = the type of error detected:  

1. not_selectable
2. out_of_context_window
3. parse_error
4. discourse_diexis
5. ambiguous
6. non_referring
7. nearest_mention_embedding
8. bridge
9. quantifier

CONLL

This is the format used in the CONLL 2011 and 2012 Shared Tasks on
Coreference. Unlike the MAS-XML format, where all interpretations
produced by players are included, only one interpretation is provided
for each markable in a doc in this format. For the docs in the silver
subset, this is the silver interpretation. For the docs in the gold
subset, both the gold and the silver interpretations are included, in
separate versions of each document.

CONLLUA

This is the format used in the CODI-CRAC 2021/2022 Shared Task on Anaphora, Bridging and Discouse Deixis in Dialogue. As in the case of the CONLL format,
only one interpretation is provided for each markable. 

# Annotation scheme

Markables are annotated according to a scheme including the following
labels:

* NR: non-referring. Used for expletives, as in '[It] rains'.
* PR: used for predicatives NPs, as in 'John is [a policeman]'
* DN: Used for discourse-new mentions.
* DO: Used for discourse-old mentions.

Split-antecedent plurals are marked.

# Folder structure

The new_gold, gold and silver subsets are contained in subfolders called 'new_gold', 'gold'
and 'silver', respectively. 


# Papers

Full documentation and preliminary analysis of the data has been
published in the following EACL paper: 

Yu, J., Paun, S., Camilleri, M., Garcia, P., Chamberlain, J., Kruschwitz, U., Poesio, M. (2023)
Aggregating Crowdsourced and Automatic Judgments to Scale Up a Corpus of Anaphoric Reference for Fiction and Wikipedia Texts. In Proceedings of the 17th Conference of the European Chapter of the Association for Computational Linguistics (EACL2023).

Earlier papers on the corpus include:

Poesio, M., Chamberlain, J., Paun, S., Yu, J., Uma, A., and Kruschwitz, U. (2019).
A Crowdsourced Corpus of Multiple Judgments and Disagreement on Anaphoric Interpretation. In Proceedings of the 2019 Annual Conference of the North American Chapter of the Association for Computational Linguistics (NAACL 2019).

Chamberlain, J., and Poesio, M., and Kruschwitz, U. (2016). Phrase
Detectives Corpus 1.0: Crowdsourced Anaphoric Coreference.  In
Proceedings of the 2016 Language Resources and Evaluation Conference
(LREC'16). 

Poesio, M., Chamberlain, J., Kruschwitz, U., Robaldo, L., and
Ducceschi, L. (2013). Phrase Detectives: Utilizing collective
intelligence for internet-scale language resource creation.  ACM
Transactions on Interactive Intelligent Systems. 

# Contact

Please report any errors or issues to jchamb@essex.ac.uk

# Change Log

April 2023: Version 3.0 cerated.


