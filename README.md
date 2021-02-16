# Measuring semantic similarity for normal and reversed word pairs.
### Anastasiia Todoshchuk and Alexey Khrustalev, Freie Universität Berlin 2021.  

#### Gold Standard Data Loading
The Gold Standard Data is loaded, the first 100 pairs of words are taken and the dataset with the inversed pairs is created. 

#### Human Data Loading and Processing. 
The human data was loaded, the unnecessary columns were dropped and the necessary preprocessing steps were done. Some pairs of word were deleted, as these word are not in the model's dictionary. 

The distribution of humans' answers were plotted to identify if the answers are distributed normally. 

The pandas DataFrame with the word pairs, gold standard values, average humans' scores for the inversed and normal pairs, and the difference between gold standard score and average humans' scores for the normal pairs was created. 

The smoothed plots were plotted for human data (red) and gold standard data (green) to see if they are similar to each other. 

The correlation and t-test were computed between gold standard data and human data.

#### Vector space model
  The corpus-based vector space models are based on distributional semantics. The predict models subtype (Baroni et al., 2014; cf. Mandera et al., 2017) was used.
 Predict models are neural nets trained on predicting words from their context or vice versa. 
 
 The model (implicitly) assume that word similarity ratings are based on semantic similarity or association only. However, how plausible is it that readers exclusively use this kind of semantic information – be it experiential, distributed or some mixture of the two– when rating word similarity? After all, the literature presents ample evidence for the fact that orthographic, phonological and other semantic features (e.g., affective semantics; e.g., Jacobs et al., 2015, 2016; Warriner et al., 2013) play a role in (single) word recognition (e.g., Andrews et al., 2009; Jacobs & Grainger, 1994). Thus, to the extent that the similarity rating task involves the automatic recognition of two words –preceding the rating– it seems plausible that these factors also influence the ratings. Our working model thus assumes that a similarity rating is based on a set of variables representing both surface (i.e., orthographic-phonological) and semantic features of the word pair. Each similarity variable, in turn, is a compound of N features. Semantic similarity can be based on a multitude of features including affective semantics (e.g., valence, arousal, emotion potential, Bestgen & Vincze, 2012; Jacobs, 2015; Jacobs et al., 2015; Westbury et al., 2015), embodied semantics (e.g., Juhasz et al., 2011; Siakaluk et al., 2008), feature norms (e.g., McRae et al., 2005), or aesthetic semantics (e.g., sonority score, aesthetic potential; Jacobs, 2017; Jacobs & Kinder, 2018).

#### Path Similarity 
Return a score denoting how similar two word senses are, based on the shortest path that connects the senses in the is-a (hypernym/hypnoym) taxonomy. The score is in the range 0 to 1. By default, there is now a fake root node added to verbs so for cases where previously a path could not be found---and None was returned---it should return a value. The old behavior can be achieved by setting simulate_root to be False. A score of 1 represents identity i.e. comparing a sense with itself will return 1.

#### Leacock-Chodorow Similarity
Return a score denoting how similar two word senses are, based on the shortest path that connects the senses (as above) and the maximum depth of the taxonomy in which the senses occur. The relationship is given as -log(p/2d) where p is the shortest path length and d the taxonomy depth.

#### Wu-Palmer Similarity 
Return a score denoting how similar two word senses are, based on the depth of the two senses in the taxonomy and that of their Least Common Subsumer (most specific ancestor node). Note that at this time the scores given do _not_ always agree with those given by Pedersen's Perl implementation of Wordnet Similarity.


