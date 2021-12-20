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
|**listgarten_elevation_cd33**|**5.848;0.5529**|6.439;0.3569|6.451;0.3517|6.374;0.3652|6.472;0.3675|6.446;0.3602|6.520;0.3467|
|**CIRCLE_seq_10gRNA**|**6.438;0.3560**|6.511;0.9221|6.812;0.3528|6.817;0.4202|6.587;0.8529|6.778;0.3970|6.836;0.4813|
|**Listgarten_22gRNA**|**6.449;0.3562**|6.808;0.3554|6.662;0.6235|6.840;0.3725|6.820;0.3592|6.764;0.3912|6.888;0.3618|
|**listgarten_elevation_hmg**|6.374;0.3685|6.818;0.4213|6.843;0.3744|**6.363;0.9191**|6.730;0.4134|6.779;0.3764|6.815;0.4570|
|**listgarten_elevation_guideseq**|**6.474;0.3662**|6.590;0.8522|6.823;0.3603|6.729;0.4149|6.512;0.8470|6.785;0.3950|6.847;0.4878|
|**Kleinstiver_5gRNA**|6.444;0.3604|6.775;0.3943|6.762;0.3903|6.780;0.3770|6.784;0.3923|**6.365;1.0186**|6.832;0.3898|
|**Seq_offTarget**|6.519;0.3474|6.841;0.4679|6.887;0.3622|6.818;0.4543|6.848;0.4867|6.831;0.3887|**6.514;0.8444**|


**With manahattan distance**

| Data Set                       | **listgarten_elevation_cd33** | **CIRCLE_seq_10gRNA** | **Listgarten_22gRNA** | **listgarten_elevation_hmg** | **listgarten_elevation_guideseq** | **Kleinstiver_5gRNA** | **Seq_offTarget** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|**listgarten_elevation_cd33**|**34.582;5.3525**|41.598;4.5479|41.700;4.5194|40.772;4.6529|41.998;4.7083|41.663;4.6069|42.644;4.4710|
|**CIRCLE_seq_10gRNA**|**41.589;4.5520**|43.239;10.7001|46.548;4.8315|46.685;5.6476|44.194;10.0680|46.089;5.3089|47.025;6.0941|
|**Listgarten_22gRNA**|**41.704;4.4995**|46.518;4.7891|44.651;7.5075|46.997;5.0941|46.662;4.8798|45.899;5.2236|47.571;4.9556|
|**listgarten_elevation_hmg**|**40.765;4.6302**|46.680;5.6499|46.980;5.0946|41.179;10.3247|45.424;5.5334|46.006;5.0574|46.627;6.0261|
|**listgarten_elevation_guideseq**|**42.004;4.7033**|44.155;10.0518|46.650;4.8736|45.471;5.4987|43.159;9.8803|46.211;5.3083|47.117;6.3199|
|**Kleinstiver_5gRNA**|41.654;4.5776|46.057;5.3038|45.875;5.2282|46.078;5.0070|46.159;5.3128|**41.439;11.8242**|46.755;5.2664|
|**Seq_offTarget**|**42.615;4.4870**|47.078;6.0692|47.593;4.9324|46.644;6.0233|47.132;6.3009|46.808;5.2698|43.158;9.6432|



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

