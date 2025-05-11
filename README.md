# slack-bert-topics

## Problem

<img width="573" alt="Screenshot 2025-05-11 at 4 06 19 PM" src="https://github.com/user-attachments/assets/c1e3d5d2-6146-45dd-99dc-b7894c433469" />

Slack channel descriptions are optional and if they are specificed, they quickly become stale because they’re written once at creation and seldom updated. As conversations evolve, these static blurbs fail to capture the channel’s current focus or key topics. This leaves team members without a clear, up‑to‑date summary of what each channel is really about. Instead, members must read every thread to stay current on real-time conversations, which ultimately leads to a loss of productivity. 

## Solution 

Feed a given Slack conversation into a python script that uses BERTopic encoding model for finding common topics and displaying their similarity on a umap. This is one step towards providing more insights at a glance into a given channel. 

## Future

Slack will likely have this feature in the future and not just at the channel level, but also on a thread-by-thread basis. Until then, we can combine Slack API with BERT encoding ourselves to uncover insights. 

## How it works

1. Fetch channel history from the Slack API
2. Convert the response to a csv file 
4. Run the script and view the output

### Fetch channel history from the Slack API 

 For the purpose of this project, I've provided an example csv file from the Slack repo. [source](https://github.com/apache-superset/examples-data/blob/master/datasets/examples/slack/messages.csv)

 If you want to use your own data, you will have to query the slack api. 
 <img width="696" alt="Screenshot 2025-05-11 at 3 45 17 PM" src="https://github.com/user-attachments/assets/35ce77fd-bfad-47ba-a0bc-4ebc121fa9af" />


### Convert the response to a csv file

Your .csv may have multiple columns, but the only column that will be parsed is the `text` column. 
<img width="595" alt="Screenshot 2025-05-11 at 3 48 06 PM" src="https://github.com/user-attachments/assets/69a2c1a9-488f-4482-a57a-e797c01c6dc1" />

Note: The input.csv file should be added as a sibling to the .py or .pynb file (whichever you decide to run). 

### Run the script and view the output

This is an example of the output - a dataframe with two columns: `text` and `topic`. 

Note: BERTopic can been configured to return a max of 20 topics, but you can modify this parameter. 


<img width="541" alt="Screenshot 2025-05-11 at 3 50 25 PM" src="https://github.com/user-attachments/assets/7a4792db-83b2-4c90-93a9-077e536fa131" />


The dataframe is visualized in a umap diagram

<img width="668" alt="Screenshot 2025-05-11 at 3 52 27 PM" src="https://github.com/user-attachments/assets/4a21733c-a2b7-411c-9ae8-f630015a3884" />
