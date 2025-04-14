Sarvam Research Fellow Assignment
-Ojas Jain
(ojasjain94@gmail.com)

The code implements a supervised cross-lingual word embedding alignment system using the Procrustes method, evaluates its performance, and conducts ablation studies. It also includes an optional unsupervised alignment method using CSLS and adversarial training.
Code Structure
1. Data Preparation
The code begins by loading pre-trained FastText embeddings for English and Hindi, limiting the vocabulary to the top 100,000 words for each language.
Key Steps:
Load embeddings using gensim.models.KeyedVectors.
Filter embeddings to include only the top 100,000 most frequent words.
2. Downloading and Loading Bilingual Dictionary
The bilingual dictionary is downloaded from the MUSE dataset and processed to extract valid word pairs for supervised alignment.
Function: download_muse_dictionary
Downloads bilingual dictionaries for English-Hindi from the MUSE dataset.
Inputs: Source language (src_lang), Target language (tgt_lang).
Outputs: Paths to downloaded dictionary files.
Function: load_dictionary
Processes dictionary files to create a list of valid word pairs.
Inputs: Dictionary path (dict_path), source vocabulary (src_vocab), target vocabulary (tgt_vocab).
Outputs: List of valid word pairs.
3. Procrustes Alignment
The Procrustes method is used to learn a linear mapping between source (English) and target (Hindi) embeddings using the bilingual dictionary.
Function: learn_procrustes_alignment
Learns an orthogonal mapping matrix using Procrustes analysis.
Inputs: Source embeddings (src_embs), Target embeddings (tgt_embs), Bilingual dictionary (bilingual_dict).
Outputs: Mapping matrix (W).
4. Evaluation
The aligned embeddings are evaluated using translation accuracy metrics: Precision@1 and Precision@5.
Function: compute_precision_at_k
Computes translation accuracy for word pairs based on cosine similarity.
Inputs: Source embeddings (src_embs), Target embeddings (tgt_embs), Test dictionary (test_dict), Mapping matrix (mapping_matrix), Precision level (k).
Outputs: Precision score (p_at_k) and predicted translations.
5. Ablation Study
An ablation study is conducted to assess the impact of bilingual lexicon size on alignment quality.
Function: ablation_study
Tests different dictionary sizes and evaluates translation accuracy.
Inputs: Source embeddings (src_embs), Target embeddings (tgt_embs), Training dictionary (train_dict), Test dictionary (test_dict), List of dictionary sizes (dict_sizes).
Outputs: Results with Precision@1 and Precision@5 scores for each dictionary size.
6. Cosine Similarity Analysis
Analyzes cosine similarities between word pairs after alignment.
Function: analyze_cosine_similarities
Computes cosine similarity between aligned word pairs.
Inputs: Source embeddings (src_embs), Target embeddings (tgt_embs), Test dictionary (test_dict), Mapping matrix (mapping_matrix).
Outputs: List of cosine similarities between word pairs.
7. Visualization
Plots results from the ablation study to visualize the impact of bilingual dictionary size on translation accuracy.
Function: plot_ablation_results
Plots Precision@1 and Precision@5 scores against dictionary sizes.
Inputs: Results from ablation study, Dictionary sizes.
Outputs: Saves plot as ablation_results.png.
8. Optional Unsupervised Alignment
Note-The optional unsupervised method could not be executed due to computational constraints but is included in the code for reference.
Implements unsupervised alignment using Cross-Domain Similarity Local Scaling (CSLS) combined with adversarial training.
Function: unsupervised_alignment
Uses CSLS and adversarial training to refine alignment iteratively.
Inputs: Source embeddings, Target embeddings, Number of iterations.
Outputs: Refined mapping matrix.
Function: csls_retrieval
Retrieves nearest neighbors using CSLS for improved alignment quality.
Inputs: Source embeddings, Target embeddings, Mapping matrix, Number of neighbors (k).
Outputs: CSLS scores.

9. Comparison of Methods
Compares supervised Procrustes alignment with unsupervised CSLS-based alignment methods.
Function: compare_methods
Evaluates both supervised and unsupervised methods using Precision@1 and Precision@5 metrics.
Inputs: Source embeddings, Target embeddings, Test dictionary.
Outputs: Comparison results with visualization.
10. Main Function
The main function orchestrates all steps:
Loads embeddings and dictionaries.
Performs Procrustes alignment.
Evaluates translation accuracy.
Conducts ablation study and cosine similarity analysis.
Visualizes results.




Function: main()
Key Outputs
Translation Accuracy Metrics:
Precision@1
Precision@5
Cosine Similarity Analysis:
Top 10 most similar word pairs
Bottom 10 least similar word pairs
Ablation Study Results:
Impact of bilingual dictionary size on translation accuracy
Visualization:
Plots saved as PNG files
Notes
The optional unsupervised method could not be executed due to computational constraints but is included in the code for reference.

How to run the file
To run this code just change the path name as mentioned below after downloading the required files
I have uploaded those things on my drive and accessing them from there






