## Note 
This is an MSR study as part of the MSR course 2022 at UniKo, CS department, SoftLang Team.

## Names of team/students
This is team **ZULU**.
- Ali Vahdatnia
- Danoosh Peachkah
- Soroush Mozooni

## Underlying paper
https://ieeexplore.ieee.org/document/9796252

## Reproduced baseline
### Objectives:
#### Description:
The main aim of the paper is to provide insight into current approaches in issue Tracking Systems (ITS) using machine learning. We have reproduced all the aspects of the study, from data extraction to duplicate detection and further analysis.

Lastly, we would like to mention that this paper is not the one we used for Assignment 2 as that one was not reproducible. After examining 15+ papers individually we finally found this one as it has checked all the marks - it is reproducible, not simple yet not too complex.
#### Input data: 
Input data were extracted with the needed properties from this [MongoDB dump](https://zenodo.org/record/5901956#.Ykaz2hBBzzc).
It got about 60+ GB of the MongoDB installation directory and a day for this primary step (data_extract.py & data_access.py).

Our repo that contains all the reproduced content: 
For your convenience, we reproduced the data extraction step which provides input for the models, You may download the extracted files out of the dump here [click here to download](https://cloud.uni-koblenz.de/s/DgEpEmFYctdEppW). The downloaded input files go to the "../data/crawl" directory.
#### Output data:
Links to the paper’s results:
https://github.com/RegenKordel/LYNX-BeyondDuplicates/tree/main/RQ3_link_detection

Links to our reproduced output:
https://github.com/AliVn85/MSR-Assignment3-Zulu-SoSe2022/tree/main/process/RQ3_link_detection
### Findings:
The reproduced process as well as reproduced outputs are exactly identical to the original paper's findings. That is because little to no changes happened to the scripts in the way that it changes the results, and also we used the identical MongoDB dump, which sealed our reproduction process as a high-quality success.

## MSR study enhancement
### Threat:
This paper provided several models to predict the situation of an issue ticket and how it can be linked to the others that may have included a duplication or partially interconnected contents. It then further compared their state-of-the-art technique. Consequently, this makes the evaluation part even more significant.
For a model to properly gets trained, and accurately classify the types, it should be trained in the way that types of the groups are equally included in the training set. This helps to obtain a non-biased result. (Wortman, P. M. (1983))
However, in the process of the evaluation of this paper, the researchers made a relatively subpar method in the sampling part which affected the whole process including the evaluation part severely. 
Therefore, based on the definition of internal validity threat (Feldt, Robert & Magazinius, Ana. (2010)), the outcome must have been changed. 

For your information, we have checked the mentioned Thread to Validity section of the paper but they are not possible to worked with due to the characterstics of them, or too complex to be studied on.
### Traces:
"Each training set is balanced including approximately the same amount of instances for each class. This means we did not include all possible Non-Links and Other-Links, as this would heavily imbalance the dataset and possible skew the performance." page 54
### Theory:
After a deep dive into the codes, we noticed that the way they tried to balance the classes for training the model, they combined all the class types and then randomly chose samples out of it. 
The hypothesis is that if - like this paper- we combine all groups into one set and do random selection, we may get "selection bias" mostly as this way never guarantees a concrete equal number of samples per each class. Causing an internal threat to validity.
### Methodology:
We randomly get an equal number of samples out of each class type and next we feed those for training the model, eventually, we would get a more accurate evaluation as the model will not have "selection bias". Ultimately, this should affect the paper's findings.
### Feasibility:
To curate the process, we reproduced all parts of the study and focused only on one model of SCCNN (Duplicates vs Non-Link & Other-Link types a.k.a LTvNLOL), but we proved that this is also possible for other models. Our suggestion is to ignore the data extraction and Link Type structure analysis, as we have already done that but it is not directly related to the enhancement part but rather is related to the reproduction. The other point to tackle this subject, we had to use a smaller database of MariaDB to optimize the code execution runtime.
### Process:
Since we fully reproduced the paper exactly the way it was, no other extra or additional processes were done.
That being said, we had to use only MariaDB from the MongoDB dump as it was too expensive for our computer to calculate the whole database.
### Data:
For your convenience, we provided an additional image in the output folder that compares our findings and the paper's original findings.
### Results:
Lastly, by looking at the model evaluation results, we have successfully achieved a higher considerable amount for mostly all evaluation metrics such as the F1 score, which proved the legitimacy of our thread for validity detection hypothesis, and project enhancement effort.

## Implementation
### Hardware requirements:
-   1.6 GHz or faster processor
-   1 GB of RAM
### Software requirements:
-   OS X El Capitan (10.11+)
-   Windows 8.0, 8.1, and 10, 11 (32-bit and 64-bit)
-   Linux (Debian): Ubuntu Desktop 16.04, Debian 9
-   Linux (Red Hat): Red Hat Enterprise Linux 7, CentOS 7, Fedora 34
-	VS Code
-	Jupyter Notebook
-	Python Version: Python 3.8.10
	- gensim                   4.0.1                      
	- Keras                    2.4.3              
	- keras-nightly            2.5.0.dev2021032900
	- Keras-Preprocessing      1.1.2                     
	- matplotlib               3.4.2                        
	- networkx                 2.6.2              
	- nltk                     3.6.2              
	- numpy                    1.19.5                      
	- pandas                   1.2.4                         
	- pymongo                  3.11.4                   
	- regex                    2021.4.4                
	- scikit-learn             0.24.2             
	- scipy                    1.6.3              
	- seaborn                  0.11.1                       
	- sklearn                  0.0                      
	- spacy                    3.0.6              
	- spacy-legacy             3.0.5                   
	- stanza                   1.2                
	- tensorboard              2.5.0              
	- tensorboard-data-server  0.6.1              
	- tensorboard-plugin-wit   1.8.0              
	- tensorflow               2.5.0              
	- tensorflow-addons        0.13.0             
	- tqdm                     4.60.0 
-	Active Internet Connection
### Validation:
For evaluating a model, meaning how precise it is working based on the expectation we have for it. Therefore, a higher evaluation score is better. This paper tried to create some ways to better understand the status of an issue in ITS environments. As you can see, the evaluation metrics such as the F1 Score output of the SCCNN Jupyter file depict a higher value than the original paper's, validating our work.
![results](https://github.com/AliVn85/MSR-Assignment3-Zulu-SoSe2022/blob/main/data/output/comparison.jpg?raw=true)
### Data: 
***Inputs:***
Since our enhancement is the continuation of the reproduction step, the input is the same as we mentioned above in the Reproduced baseline part.

***Output:***
The output contains cleaned links and the result of the Jupyter files, scattered in the process as well as the data folder.
But the actual output of our enhancement work resides in the output folder which compares the original and our newly revised enhancement job.
To reproduce this, please run the ``SingleChannel.ipynb`` file and run the model depicted in the picture (`LTvNLOL_preds`).

## Bonus - Reproduction Steps:
1. Download the extracted files out of the MongoDB dump.
2. Put the unzipped data folder into the root folder so that you have the directory structure of "../data/crawl".
3. Install the python packages on your machine.
4. Run Jupyter Notebook (as the paper has mentioned a GPU is recommended).
5. Run the SingleChannel.ipynb of RQ3 in the notebook as we have already done the previous steps for you in case you want to rerun the experiment.

###### References:

Wortman, P. M. (1983). "Evaluation research – A methodological perspective". Annual Review of Psychology. 34: 223–260. doi:10.1146/annurev.ps.34.020183.001255)

Feldt, Robert & Magazinius, Ana. (2010). Validity Threats in Empirical Software Engineering Research - An Initial Survey.. 374-379.
