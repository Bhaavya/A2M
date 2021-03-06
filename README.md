Repository for code and data associated with the A2M framework paper on analogy generation via prompting GPT-3 (Davinci).

# Data

## PLM-based Analogy Generation

* `/data/discp_adapt`: Candidate Discipline-specific Adaptive Analogies for arts, social science (ss) and business (bus) disciplines
* `/data/pref_adapt`: Candidate Preference-specific Adaptive Analogies for cooking (cook), gardening (gar), music (mus), and sports preferences
* `/data/non_adapt`: Candidate Non-Adaptive Analogies for Cybersecurity (cyber), Machine Learning (ai), and High-school science (sci) domains
* `/data/non_analogies`: Non-Analogies used as negative sample for training Analoginess Scorer
* `/data/sci_src`: Additional Analogies (generated with source concept as part of the prompt) for High-school science domain used as positive samples for training Analoginess Scorer

For all files names, p<em>n</em> means analogies generated with prompt id <em>n</em> in the paper, ht means high temperature, lt means low temperature.

Each file contains the following fields separated by tab: (1) Generated Analogy, (2) Target Concept, (3) Prompt.

### Prompt Refinement: 

* `/data/prompt_refiner/discp_adapt.txt`: Candidate Discipline-specific Adaptive Analogies after prompt refinement
* `/data/prompt_refiner/pref_adapt.txt`: Candidate Preference-specific Adaptive Analogies after prompt refinement
* `/data/prompt_refiner/non_adapt.txt`: Candidate Non-Adaptive Analogies classified after prompt refinement

Each file contains the following fields separated by tab: (1) Generated analogy after prompt refinement, (2) Target Concept, (3) Original Prompt, (4) Temperature (low -- lt or high --ht) (5) Domain (for non-adaptive analogies)/Preference/Discipline, (6) Generated analogy before prompt refinement (classified as non-analogy).

## Analoginess Scorer

* `/data/analoginess_scorer/discp_adapt.txt`: Candidate Discipline-specific Adaptive Analogies classified as non-analogy and analogy
* `/data/analoginess_scorer/pref_adapt.txt`: Candidate Preference-specific Adaptive Analogies classified as non-analogy and analogy
* `/data/analoginess_scorer/non_adapt.txt`: Candidate Non-Adaptive Analogies classified as non-analogy and analogy

Each file contains the following fields separated by tab: (1) Generated Analogy, (2) Target Concept, (3) Prompt, (4) Temperature (low -- lt or high --ht) (5) Domain (for non-adaptive analogies)/Preference/Discipline, (6) Predicted Class (0 -- non-analogy, 1 -- analogy).

### After Prompt Refinement: 

* `/data/analoginess_scorer/prompt_refiner/discp_adapt.txt`: Candidate Discipline-specific Adaptive Analogies classified as non-analogy and analogy after prompt refinement
* `/data/analoginess_scorer/prompt_refiner/pref_adapt.txt`: Candidate Preference-specific Adaptive Analogies classified as non-analogy and analogy after prompt refinement
* `/data/analoginess_scorer/prompt_refiner/non_adapt.txt`: Candidate Non-Adaptive Analogies classified as non-analogy and analogy after prompt refinement

Each file contains the following fields separated by tab: (1) Generated analogy after prompt refinement, (2) Target Concept, (3) Prompt, (4) Temperature (low -- lt or high --ht) (5) Domain (for non-adaptive analogies)/Preference/Discipline, (6) Predicted Class (0 -- non-analogy, 1 -- analogy), (7) Generated analogy before prompt refinement (classified as non-analogy).

## PLM-based Source Extraction

* `/data/extracted_src/discp_adapt.txt`: Source extracted from Discipline-specific Adaptive Analogies 
* `/data/extracted_src/pref_adapt.txt`: Source extracted from Preference-specific Adaptive Analogies
* `/data/extracted_src/non_adapt.txt`: Source extracted from Non-Adaptive Analogies

Each file contains the following fields separated by tab: (1) Generated Analogy, (2) Target Concept, (3) Prompt, (4) Temperature (low -- lt or high --ht) (5) Domain (for non-adaptive analogies)/Preference/Discipline, (6) Extracted Source(s).

In case the PLM generated multiple mappings between source and target concepts, they are separated by ###. We only used the first mapping in our experiments.

## Retrieval-based Analogy Mining

`/data/ret_am/`: Each file contains analogies retrieved from the Web for one target and source concept pair. It has a json dictionary with the following keys and values: (1) "src_spec_res" with lists of Bing search results returned for <em>source-specific</em> queries, (2) "gen_res" with lists of Bing search results returned for <em>general</em> queries, (3) "all_bing_queries" with the list of all the source-specific and general queries.

## Ranked Analogies

* `/data/ranked_analogies/discp_adapt.txt`: Contains Adaptive Analogy Ranking Score, Reliability Score, and Adaptiveness Score of Discipline-Specific Adaptive Analogies.  
* `/data/ranked_analogies/pref_adapt.txt`: Contains Adaptive Analogy Ranking Score, Reliability Score, and Adaptiveness Score of Preference-specific Adaptive Analogies.  
* `/data/ranked_analogies/non_adapt.txt`: Contains Creative and Existing Analogy Ranking Score, Reliability Score, and Creativity Score of Non-Adaptive Analogies. 

# Analoginess Scorer Model

Trained model available at: https://drive.google.com/file/d/1egpgQyjDd9I0b-_wmIRPsgnK0OGs9FqX/view?usp=sharing. 

Download the model and place in under `/model` under this repo folder to run Analoginess Scorer Prediction Code (`src/analoginess_scorer_pred.py`)
