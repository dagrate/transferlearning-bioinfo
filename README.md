# transferlearning-bioinfo

Transfer learning for gene editing.

Data preprocessing in transferlearning_crispr_datapipeline.ipynb.


------

## Experiments

### Data Set Description

| Data Set                       | **Nbr of samples in minority class (N_min)** | **Nbr of samples in majority class (N_maj)** | **Class imbalance ratio (N_min/N_maj)** |
|:---:|:---:|:---:|:---:|
|**listgarten_elevation_cd33**  |2273|2800|0.468|
|**listgarten_elevation_hmg**   |52|10077|0.005|
| **Kleinstiver_5gRNA**         |54|95775|0.001|
| **Listgarten_22gRNA**         |56|383463|<0.001|
| **elevation_guideseq**        |354|294180|0.001|
| **CIRCLE_seq_10gRNA**         |7371|577578|0.013|
| **SITE_seq_offtarget**        |7371|213966|0.017|


### Data Similarity Analysis

Remark: first metric is the distance, second is the std dev.


**With cosine distance**

| Data Set                       | **listgarten_elevation_cd33** | **CIRCLE_seq_10gRNA** | **Listgarten_22gRNA** | **listgarten_elevation_hmg** | **listgarten_elevation_guideseq** | **Kleinstiver_5gRNA** | **Seq_offTarget** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|**listgarten_elevation_cd33**|1.000;0.000|0.305;0.0750|0.309;0.0749|0.307;0.0758|**0.313;0.0750**|0.308;0.0760|0.305;0.0725|
|**CIRCLE_seq_10gRNA**|0.306;0.0751|1.000;0.000|0.327;0.0682|0.311;0.0813|**0.369;0.1429**|0.333;0.0752|0.329;0.0858|
|**Listgarten_22gRNA**|0.308;0.0752|0.327;0.0685|1.000;0.000|0.311;0.0723|0.337;0.0678|**0.339;0.0743**|0.325;0.0700|
|**listgarten_elevation_hmg**|0.307;0.0761|0.311;0.0816|0.311;0.0723|1.000;0.000|**0.340;0.080**|0.324;0.0712|0.326;0.0850|
|**listgarten_elevation_guideseq**|0.313;0.0752|**0.368;0.142**|0.337;0.0677|0.340;0.0810|1.000;0.000|0.343;0.0738|0.340;0.0870|
|**Kleinstiver_5gRNA**|0.308;0.0761|0.333;0.0751|0.340;0.0745|0.324;0.0751|**0.343.0.0739**|1.000;0.000|0.336;0.0743|
|**Seq_offTarget**|0.306;0.0726|0.329;0.0849|0.325;0.0698|0.325;0.0850|**0.340;0.0867**|0.336;0.0741|1.000;0.000|


**With euclidean distance**

| Data Set                       | **listgarten_elevation_cd33** | **CIRCLE_seq_10gRNA** | **Listgarten_22gRNA** | **listgarten_elevation_hmg** | **listgarten_elevation_guideseq** | **Kleinstiver_5gRNA** | **Seq_offTarget** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|**listgarten_elevation_cd33**|1.000;0.000|||||||
|**CIRCLE_seq_10gRNA**||1.000;0.000||||||
|**Listgarten_22gRNA**|||1.000;0.000|||||
|**listgarten_elevation_hmg**||||1.000;0.000||||
|**listgarten_elevation_guideseq**|||||1.000;0.000|||
|**Kleinstiver_5gRNA**|0.308;0.0761||||||1.000;0.000||
|**Seq_offTarget**|1.000;0.000||||||1.000;0.000|


**With manahattan distance**

| Data Set                       | **listgarten_elevation_cd33** | **CIRCLE_seq_10gRNA** | **Listgarten_22gRNA** | **listgarten_elevation_hmg** | **listgarten_elevation_guideseq** | **Kleinstiver_5gRNA** | **Seq_offTarget** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|**listgarten_elevation_cd33**|1.000;0.000|||||||
|**CIRCLE_seq_10gRNA**||1.000;0.000||||||
|**Listgarten_22gRNA**|||1.000;0.000|||||
|**listgarten_elevation_hmg**||||1.000;0.000||||
|**listgarten_elevation_guideseq**|||||1.000;0.000|||
|**Kleinstiver_5gRNA**|0.308;0.0761||||||1.000;0.000||
|**Seq_offTarget**|1.000;0.000||||||1.000;0.000|



### Preliminary Results for AI Classifiers

Metrics displayed are the ROC AUC and the F1 Score Class 1.

*How to read the table:* for (listgarten_elevation_cd33 x listgarten_elevation_cd33), the model is trained and tested on listgarten_elevation_cd33. For (listgarten_elevation_cd33 x listgarten_elevation_hmg), the model is trained on listgarten_elevation_cd33, and tested on listgarten_elevation_hmg. Thus, we apply transfer learning on listgarten_elevation_hmg. 


**Metrics for Random Forest Classifier (without class rebalancing)**


| Data Set                       | **Listgarten_22gRNA** | **listgarten_elevation_cd33** | **listgarten_elevation_hmg** | **listgarten_elevation_guideseq** | **CIRCLE_seq_10gRNA** | **Kleinstiver_5gRNA** | **Seq_offTarget** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|**Listgarten_22gRNA**|.523; .000|.517; .000|.530; .000|.499; .000|.501; .000|.496; .000|.517; .000|
|**listgarten_elevation_cd33**|.768; .001|.879; .768|.626; .015|.620; .004|.753; .051|.634; .002|.707; .082|
|**listgarten_elevation_hmg**|.531; .000|.476; .000|.589; .000|.735; .000|.606; .000|.508; .036|.536; .000|
|**listgarten_elevation_guideseq**|.565; .000|.521; .000|.644; .000|.734; .000|.565; .068|.522; .000|.553; .009|
|**CIRCLE_seq_10gRNA**|.706; .000|.623; .000|.575; .000|.944; .126|.883; .449|.645; .000|.761; .177|
|**Kleinstiver_5gRNA**|.564; .000|.490; .000|.551; .000|.504; .000|.506; .000|.595; .100|.554; .000|
|**Seq_offTarget**|.521; .000|.556; .000|.552; .000|.588; .046|.658; .130|.567; .000|.894; .434|

Remark: class imbalance on some of the data sets is high. Thus, it impacts strongly the classifier performance.

**Metrics for Random Forest Classifier (without class rebalancing)**

**TO BE UPLOADED**

| Data Set                       | **CIRCLEseq_cd33** | **Listgarten_22gRNA** | **listgarten_elevation_hmg** | **listgarten_elevation_guideseq** | **CIRCLE_seq_10gRNA** | **Kleinstiver_5gRNA** | **Seq_offTarget** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|

**Metrics for Random Forest Classifier (with class rebalancing, ratio N_min/N_maj:TBD.)**

**TO BE UPLOADED**

**Metrics for Random Forest Classifier (without class rebalancing)**

**TO BE UPLOADED**

| Data Set                       | **CIRCLEseq_cd33** | **Listgarten_22gRNA** | **listgarten_elevation_hmg** | **listgarten_elevation_guideseq** | **CIRCLE_seq_10gRNA** | **Kleinstiver_5gRNA** | **Seq_offTarget** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|

