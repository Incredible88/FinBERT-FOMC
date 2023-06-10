# FinBERT-fine-tuned
This is a fine-tuned FinBERT model by sentiment focus, the data used FOMC minutes 2006.1 to 2023.2.

## Why Fine-tune FinBERT
The drawbacks of FinBERT is obvious. FinBERT has great performance in simple financial sentences, when it turns to complex sentences which contains disjunctive words( Although, While, But), FinBERT would easily misclassify the sentiment. The orientation for fine-tining is to make FinBERT more fit complex financial sentences.

## Sentiment Focus

**Step1.**  
To remove comma when two paragraph should be together. For Example: 
 
However, the apparent pickup in longer-term expectations, while worrisome, was relatively small  
⇓  
However, the apparent pickup in longer-term expectations, while worrisome was relatively small 

---
**Step2.**  
If there is a transition such as **although**, **though** and **while**, the focus will be on those paragraph except this one, and if there is a **but**, the focus will be on the paragraph containing the but. For example:

**Although** some scattered signs of cooling of the housing sector had emerged, the pace of construction activity and sales remained brisk.  
⇓  
the pace of construction activity and sales remained brisk.

Starts of new single-family homes dropped back somewhat in October from September's very strong pace, **but** permit issuance remained elevated.   
⇓  
permit issuance remained elevated.

**Example:**  
![image](https://github.com/Incredible88/FinBERT-fine-tuned/assets/60803217/0e0253eb-2927-4ed3-9fc9-18dfb1ddab5e)
If we do sentiment focus processing, we can get correct sentiment classification.

## Results
For testing datasets, which is manual labeled data, the overall accuracy of fine-tined model is 88.3% and the original FinBERT is 84.0%.
![image](https://github.com/Incredible88/FinBERT-fine-tuned/assets/60803217/d19af3a6-7336-4497-8895-841649b4a1d9)

  
As the reason that most of the testing data is simple sentences, it is hardly possible to see the superiority of the fine-tuned model. When we only selected the complex sentences, the results is comparison of FinBERT, Fine-tuned model and FinBERT after Sentiment Focus. Now we can see there are more than 13% accurate( 87% over 74%) in fine-tune model to original FinBERT:
![image](https://github.com/Incredible88/FinBERT-fine-tuned/assets/60803217/367809b5-95d7-4b08-b735-5783b8b17bdd)



