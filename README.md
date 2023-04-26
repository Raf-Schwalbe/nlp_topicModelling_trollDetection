# nlp_topicModelling_trollDetection

## Purposes of the project:

1. to find topics in a set of polish language tweets
2. to find the most important users who initiate discussions in specific topics
3. to find trolls accounts 

## Table of content
1. Preparation
    1. Prepare the workbench
    2. Get data
    3. Clean tweets
2. What topics can we see in the texts (what are people writing about)?
    1. Gibbs Sampling Dirichlet Mixture Model
    2. Train inital GSDMM
    3. Find the best number of clusters
    4. GSDMM vs LDA
    5. Train final GSDMM model
  6. Visualize results
3. What are the most important users who initiate discussions in specific topics?
    1. Coal influencers
    2. Energy resources influencers
    3. Nuclear energy influencers
4. How can we identify inauthentic accounts which could possibly be bots or trolls?
    1. Prepare a workbench
    2. Datasets preparation
    3. FiveThirtyEight's troll tweets dataset
    4. **Language detector**
    5. Annotated dataset
    6. Model fine-tuning
    7. Model evaluation
    8. Model saving
    9. **Predictions with trained model**
    10. Find users with higher than average number of troll-like tweets

## Interesting features

1. language - the language of the analyzed tweets was Polish. It differentiated the project from english oriented ones and requires use of relevant tools
2. in topic modelling two approaches were compared - 
    1. **Gibbs Sampling Dirichlet Mixture Model (GSDMM)** which is a modified LDA algorithm that uses the simple assumption of one topic assigned to one text. 
    This assumption turned out to be relevant for tweets
    2. LDA
3. In topic modelling hyperparameter - number of topics was tuned with **coherence measure**
4. Approach to the troll account hunt - the problem was translated to the supervised one and then transition from tweets to accounts tweets was made:
    1. find labelled (troll-like, not-troll-like) datasets and filter polish language text with language detector 
    2. fine-tune a **Transformer model** on labelled dataset - **transfer** learning was used
    3. Use model to predict whether tweets are troll-like
    4. If the account has share of troll-like tweets sinificantly higher than population it points the account maybe troll one 

## Next steps
1. build application where user can use built models to:
    1. find topic of user provided short text
    2. predict whether the text is troll features
2. contenerize the application with Docker
3. deploy application with AWS ECS
    
