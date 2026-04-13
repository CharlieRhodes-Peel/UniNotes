# Summary
- Recommender systems are used to recommend the best item / movie / whatever to a user
- Recommender systems (RS) can be seen as a function
	- Where the user {**model + items**} are input and {**relevance score**} is the output
- This module focuses mainly on **collaborative** filtering with U2U and I2I models (user-to-user and item-to-item respectively)

### Collaborative filtering - Most prominent approach
 //TODO: come back to this later and fill it out!

# Modern Systems
Nowadays modern system have grown away from collaborative filtering, which was used heavily in the 2000s to now Deep NNs and [[Matrix Factorization]]

# [[Matrix Factorization]]

# Neural Network Approaches
Neural Collaborative Filtering - **NCF**
- Integrates [[Matrix Factorization]] with a feedforward neural network
- Captures both linear and non-linear interactions between users and items

Autoencoders for Non-Linear Matrix Decomposition 
- An early deep learning approach for recommender systems
- Learns compressed representations of user-item interactions
- Effectively handles sparse rating matrices

Joint Representation Learning for Multimodal Data
- Users NNs to extract auxiliary informations from text, audio and video
- Deep leaning models: CNNs for image-based recommendations, RNNs for sequential data, GANs for data augmentation and GNNs for modelling user-item relationships