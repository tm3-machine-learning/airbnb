# Airbnb Busyness Recommendation Engine

This repository contains the code and resources for a “Airbnb Busyness Recommendation Engine” project. The goal of this project is to demonstrate how Airbnb (or a similar platform) could leverage listing‐level data to measure neighbourhood “busyness” and then recommend underutilised (less busy) but similar neighbourhoods when a user’s desired area is at capacity. By redirecting guest demand to quieter areas, the system aims to help mitigate overtourism and make better use of available inventory.

## Authors
- Marie Levesque
- Mark Chandler  
- Matthew Bowyer  
- Thiago Contardi  

## Overview

When a popular neighbourhood becomes crowded, many guests struggle to find alternative—but still appealing—options nearby. This repository implements a proof‐of‐concept K-Nearest Neighbors (KNN) recommendation engine that:

1. **Quantifies “Busyness”**  
   - Aggregates listing features (price, availability, review metrics, room‐type mix, host profile, etc.) at the neighbourhood level.  
   - Constructs a composite “busyness score” by combining inverse availability, average reviews per month, and listing density (all MinMax‐scaled).

2. **Builds Neighbourhood Profiles**  
   - Assembles an 18-dimensional feature vector for each neighbourhood (covering pricing distribution, room‐type proportions, host composition, review activity, and more).  
   - Cleans and normalises all numeric inputs to ensure fair distance calculations (KNN is sensitive to feature scale).

3. **Recommends Less Busy Neighbourhoods**  
   - For any given (busy) neighbourhood, the system returns:  
     - The three most similar neighbourhoods overall (in feature space).  
     - The nearest neighbour among those with a strictly lower composite busyness score.  
   - This ensures every suggestion is demonstrably less busy while remaining similar in character.

4. **Provides Transparency and Interpretability**  
   - Unlike latent‐factor or decision‐boundary models, KNN simply yields the closest feature‐space neighbours, making it easy to trace why a certain area was recommended.

5. **Serves as a Proof-of-Concept**  
   - Although not yet optimised for production, the code demonstrates how listing‐level and aggregated neighbourhood data can be combined to address overtourism in a data‐driven way.  

## Dataset 
The dataset used in this project is a subset of Airbnb listings in New York City, the dataset is available at [Airbnb NYC Open Data](https://www.kaggle.com/datasets/dgomonov/new-york-city-airbnb-open-data).

