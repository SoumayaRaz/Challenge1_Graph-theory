# 🍽️ Find Influencers to Promote a Restaurant in the Bay Area

![Python](https://img.shields.io/badge/Python-3.9-blue)
![Project Status](https://img.shields.io/badge/Project-Completed-brightgreen)

> 🔎 Identifying the most influential individuals on LinkedIn to promote a local restaurant using network analysis and machine learning.

---

## 📌 Overview

As part of a data science team at LinkedIn, our marketing department has requested an online influencer campaign for a restaurant located in the San Francisco Bay Area. Our mission is to identify the **top 5 most influential LinkedIn users** who can effectively promote the restaurant.

This involves:
- Understanding and modeling social influence within a network
- Completing missing profile data (location, employer, college)
- Applying **centrality measures** to rank users in terms of influence

---

## 🧠 Business Understanding

Marketing campaigns aim to deliver a message to a target audience. On social media, **influencers** are central figures within communities who can amplify a message's spread. To identify these key individuals, we use various **graph-based centrality metrics** such as:
- **Degree centrality**
- **Pagerank**
- **Betweenness centrality**

The goal is to **select 5 users from San Francisco** who maximize information diffusion within the LinkedIn graph.

---

## 📊 Data Understanding

The dataset includes:
- A **graph G** representing user connections
- Three dataframes:  
  - `df_l`: locations  
  - `df_e`: employers  
  - `df_c`: colleges  

Key observations:
- Graph: 811 nodes, 1597 edges, undirected, unweighted
- No duplicate locations per person
- Some users had multiple universities or job changes

Figures:
- 📌 Top values of `college`, `employer`, and `location`

---

## 🧹 Data Preparation

We enriched the graph `G` with the following node attributes:
- **Location**
- **Employer**
- **College**

This allowed us to integrate social and profile information directly into the network structure.

---

## 🧪 Modeling

The modeling process is divided into **two main steps**:

### 1. Filling Missing Attributes

We used two strategies:

#### 🔁 a) Homophily-based Inference
- Detected **Louvain communities** in the graph
- Assumed similar individuals belong to the same community
- Imputed missing values using most frequent attributes within communities

✅ Output: complete user profiles

#### 🌲 b) Random Forest Classification
- Built adjacency matrix of the graph
- Treated each node as a feature vector
- Used Random Forest to predict missing attributes like `location`

✅ Output: predicted attributes using supervised learning

---

### 2. Influencer Identification

We applied four **centrality measures** on nodes located in **San Francisco**:

- **Degree Centrality**  
  > Most directly connected users  
  📈 Top 5 with highest number of LinkedIn connections

- **Closeness Centrality**  
  > Fastest spreaders of information  
  📈 Top 5 with shortest distance to all others

- **Eigenvector Centrality**  
  > Most connected to other well-connected people  
  📈 Top 5 influencers in terms of network quality

- **Betweenness Centrality**  
  > Key bridges across communities  
  📈 Top 5 brokers connecting otherwise isolated groups

🧠 Final influencers were selected based on **recurrence across all rankings**.

---

## 📈 Evaluation

We evaluated the model in two parts:

### 1. Data Completion Accuracy
- Compared predicted values to ground truth
- Used `evaluation_accuracy` function for homophily approach
- Measured **Random Forest precision** on hold-out sets

### 2. Influencer Relevance
- Checked consistency across centrality metrics
- Verified influencer locality (must be from San Francisco)

---

## 🧾 Conclusion

This project successfully identified **5 influential LinkedIn users** likely to maximize restaurant visibility in the San Francisco Bay Area.

✅ Key achievements:
- Graph-based community detection
- Hybrid approach combining **network science** and **machine learning**
- Comprehensive influencer analysis via **multiple centrality metrics**

📌 Future improvements:
- Refine community detection using more advanced algorithms
- Explore deep learning for graph representation

---

## 📁 Repository Structure

```text
📂 Influencer_Restaurant_Project/
├── 📄 README.md                # Project overview and documentation
├── 📁 data/                    # Raw data and generated data
├── 📁 notebooks/               # Jupyter notebooks for data processing, modeling, and analysis
└── 📄 Report                   # Technical writeup and final summary
 
