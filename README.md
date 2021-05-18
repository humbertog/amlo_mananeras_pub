# Latent Dirichlet Allocation (LDA) analysis and visualizations of AMLO's morning conferences

LDA is used in order to discover the topics that the president AMLO talks in his daily morning conferences (mañaneras). MALLET's 
algorithm (http://mallet.cs.umass.edu/ ) is used after some basic pre-processing of the text data, including:
- special character removal
- bigram creation
- stop words removal

The number of topics is set to 65 and α=40.

The transcriptions of the conferences are available online in the Government's website, and they are periodically 
scraped and put in csv format by https://github.com/NOSTRODATA/conferencias_matutinas_amlo

For the StreamGraph (https://en.wikipedia.org/wiki/Streamgraph) the topic distribution is smoothed using a Gaussian window.
Each document is limited to the 3 topics in order to better differentiate the topics in the documents (ToDo: this may be achieved using smaller α values).
