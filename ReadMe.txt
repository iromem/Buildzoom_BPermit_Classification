Scripts written to automate the classification of Buildzoom’s building permit data.
This file describes 7 ipython notebook files (.ipynb) that house the different steps of the pipeline developed for the classification.
Briefly, each ipython notebook has code for the following:

1) BuildZoom_BPermit_K-Means_Pipeline.ipynb

Code for the K-Means portion of the pipeline. In essence, it does K-means across a sample of permit data and outputs cluster of permits and the top keyword associated to each cluster. These clusters served to identified keywords that supported the identification of a taxonomy of permit subtypes and the most common keywords associated to each subtype (taxonomy_cluster_keywords).

2) Buildzoom_BPermit_NBClassifiers.ipynb

Code for the construction of Naive Bayes classifiers for each of the permit subtypes. It builds a classifier for each of the permit subtypes using a sample of data that is labeled a priori using keyword-searching from the taxonomy clustering step.

3) Buildzoom_BPermit_Evaluation.ipynb

Code to evaluate the Naive Bayes classifiers trained in previously against a manually curated test set.

4) Buildzoom_BPermit_Classify.ipynb

Code to transverse Buildzoom’s Building permit database and classify every building permit. All classification are identified by building permit id and stored in the building_permits_classification table.

5) Buildzoom_BPermit_StructuredLearning.ipynb

*** Was not fully tested and/or completed ***
Code to explore using a structured model for building permit classification. Chow-Liu’s tree graph algorithm was implemented to find the strongest mutual information associations between permit subtypes. From there,only one model, Multilabel SVM with a NSlackSVVM learning was tested. 

6) Buildzoom_SRequests_Classify 

Code to look at Buildzoom’s Service Request and classify them using the Naive Bayes classifiers used to train building permits. The query to call the service request is found in ’s_request_query.txt’ (it assumes service requests with status=1 are actual requests). All classifications are identified by service request id and stored in the service_requests_classification table.

7) Buildzoom_SRequests_Analysis

Code performed to explore the service request data. A simple wordcloud is built on the most recurring words across service requests and a latent-dirichlet allocator (LDA) model is used to perform topic analysis on the service requests. 

Additional files:

a) s_request_query.txt

Sql query to fetch service requests.

b) taxonomy_cluster_keywords

File with the list of building permit subtypes (by row) with their associated synonym keywords. The first word for each row becomes the identifier for that subtype.

c) NB_Classifiers folder

Folder that holds all the trained Naive Bayes classifier objects (in python .pkl and .npy file format). Additionally, this folder also houses some plots regarding the evaluation metrics. 