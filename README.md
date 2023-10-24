# TriS
TriS: A Comprehensive Model for Writing Style Change Detection by Integrating Semantic, Syntactic, and Stylistic Features

The exploration of writing style shifts within multi-authored texts is a promising field in computational linguistics. It aims to localize instances of style transition, exhibiting immense potential for real-world applications such as plagiarism detection, forensic analysis, literary study, and author attribution. In this project, we propose the model TriS for multi-author writing style change detection. TriS comprises three modules, namely **S**emantic, **S**yntactic, and **S**tylistic encoders, leveraging fine-tuned BERT models and a Logistic Regression classifier to analyze stylometric patterns associated with style shifts. This study focuses on the task presented in [PAN Multi-Author Writing Style Analysis 2023](https://pan.webis.de/clef23/pan23-web/style-change-detection.html), which is characterized by constrained topic information.

## Full Model
The main body of our model consists of three modules. The first part is a text content analysis module that utilizes BERT as a pre-trained model (**Semantic Encoder**). This module examines the textual content and extracts semantic information for style analysis. The second part is a POS-tag encoder module that also utilizes BERT as a pre-trained model (**Syntactic Encoder**). It encodes the part-of-speech tags of the text, which can provide additional syntactic insights into the writing style. Lastly, the third part is a logistic regression model (**Stylistic Encoder**) that analyzes the stylistic features of the text. This module captures specific linguistic patterns and features that contribute to writing style. The outputs of these three sub-models are then fused together in our fusion module (**Fusion Recognizer**), which combines and integrates the individual outputs to provide the final analysis result.
<img width="965" alt="full model" src="https://github.com/NKUludandan/TriS/assets/66631654/0177cae9-1e99-4056-838f-9dc185aa40d9">

## Semantic Encoder
In the Semantic Encoder module, our goal is to extract semantic features from the text for detecting writing style. To achieve this, we have opted to fine-tune a pre-trained BERT model.
<img width="905" alt="semantic encoder" src="https://github.com/NKUludandan/TriS/assets/66631654/a8a7f3c9-a141-4608-919e-0b30755b4c2d">

## Syntactic Encoder
In the Syntactic Encoder module, our goal is to extract syntactic features from paragraphs for writing style detection. We believe that the POS tag sequences of paragraphs contain a wealth of information about word classes, phrase structures, hierarchical structures, and other syntactic features. To achieve this, we utilize a pre-trained BERT model and fine-tune it specifically for our task.
<img width="832" alt="Syntactic Encoder" src="https://github.com/NKUludandan/TriS/assets/66631654/9cc0dd92-5858-4e18-bbd5-9a2903fc6312">

## Stylistic Encoder
In the Stylistic Encoder module, our goal is to extract the stylistic features of paragraphs for writing style detection. We utilize 11 different stylistic features and construct their corresponding feature vectors. For each text pair, we subtract the feature vectors element-wise and take the absolute value, resulting in a stylistic difference feature vector for the text pair. Finally, we employ a logistic regression model to fit the feature vector and determine whether a writing style change has occurred.
<img width="887" alt="Stylistic Encoder" src="https://github.com/NKUludandan/TriS/assets/66631654/11975493-6e13-46b4-b0b0-fe8f29871869">
