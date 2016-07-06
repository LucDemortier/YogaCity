# YogaCity
This project analyzes Yelp reviews of yoga businesses in NYC and LA (mainly yoga studios, but also gyms offering yoga classes, stores selling yoga apparel, etc.). What concerns do practitioners/customers have, and how do these concerns differ between NYC and LA? 

This was my "Project Kojak" in the Spring 2015 Metis Data Science Boot Camp. 

See blog post at [lucdemortier.github.io](http://lucdemortier.github.io/projects/5_Kojak.html) for a description of the results.

iPython notebooks used to generate the results and plots for the YogaCity project:

1. **YelpScrape**: Scrapes Yelp website for reviews of yoga businesses in the NYC and LA areas.
  - Outputs pickle files NYC_yoga_businesses.pkl, LA_yoga_businesses.pkl, NYC_yoga_businesses_unique_urls.pkl, and LA_yoga_businesses_unique_urls.pkl. These files contain identifying information for the yoga businesses.
  - Writes the scraped reviews to a MongoDB 
  - Makes plots of the number of reviews per studio for NYC, LA, and both superimposed.
  
1. **Geocodes**: Creates json files with yoga studio names, addresses, and geocoordinates.
  - Outputs NYC_yoga_studios_v1.json and LA_yoga_studios_v1.json
  
1. **Yogana_byStudio_NYCLA_LSI**: Concatenates reviews by studio and performs both Latent Semantic Indexing (LSI) and Boolean Keyword Matching (BKM) on the resulting NYC and LA corpora.
  - Outputs the following plots:
    * Singular values, in decreasing order;
    * 2D plots of documents in LSI space, to illustrate latent topics;
    * Plots of LSI cosine similarity versus BKM count for the queries "Bikram", "prenatal pregnant pregnancy", and "Yoga nidra";
    * Plots of LSI retrieval probabilities for various queries, in the LA corpus versus the NYC corpus;
    * Plots of BKM retrieval probabilities for various queries, in the LA corpus versus the NYC corpus;
    * Plot of the retrieval probability difference Prob(LSI)-Prob(BKM), for various queries in the LA corpus versus the NYC corpus.
  - Outputs the json files NYC_yoga_studios_v3.json and LA_yoga_studios_v3.json.  These files add to the corresponding v1 files vectors of LSI and BKM query results, for use in the web maps on the blog.
  
1. **Yogana_byStudio_NYCLA_LDA**: Looks at topics produced by Latent Dirichlet Allocation (LDA) from the NYC and LA corpora.

1. **Yogana_byStudio_HDP**: Looks at topics produced by a Hierarchical Dirichlet Process (HDP) from the NYC and LA corpora.

The LSI, LDA, and HDP transformations were all done with Radim Řehůřek's gensim library.
