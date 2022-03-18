# transferlearning-bioinfo

Transfer learning for gene editing.

Data preprocessing in transferlearning_crispr_datapipeline.ipynb.


------

## Experiments

### Data Set Description

| Data Set                       | **Nbr of samples in minority class (N_min)** | **Nbr of samples in majority class (N_maj)** | **Class imbalance ratio (N_min/N_maj)** |
|:---:|:---:|:---:|:---:|
|**listgarten_elevation_cd33**  |2273|2800|0.468|
| **CIRCLE_seq_10gRNA**         |7371|577578|0.013|
| **SITE_seq_offtarget**        |7371|213966|0.017|
| **elevation_guideseq**        |354|294180|0.001|
| **Listgarten_22gRNA**         |56|383463|<0.001|
| **Kleinstiver_5gRNA**         |54|95775|0.001|
|**listgarten_elevation_hmg**   |52|10077|0.005|


### Bootstrapped data such that class imbalance ratio is maintained identical to the original data sets.

| Data Set                       | **Nbr of samples in minority class (N_min)** | **Nbr of samples in majority class (N_maj)** | **Class imbalance ratio (N_min/N_maj)** |
|:---:|:---:|:---:|:---:|
|**listgarten_elevation_cd33**  |117|133|0.468|
|**CIRCLE_seq_10gRNA**          |3|247|0.01|
| **SITE_seq_offtarget**        |4|246|0.02|
| **elevation_guideseq**        |2|248|<0.001|
| **Listgarten_22gRNA**         |2|248|<0.001|
| **Kleinstiver_5gRNA**         |2|248|<0.001|
| **listgarten_elevation_hmg**  |3|247|0.01|
| **guide_seq**                 |16|234|0.07|


### Data Similarity Analysis


#### Data Similarity Analysis between bootstrapped data and original data sets
from top to bottom <br/>
table_names = [ <br/>
**listgarten_elevation_cd33_boot**, <br/>
**CIRCLE_seq_10gRNA_boot**, <br/>
**Listgarten_22gRNA_boot**, <br/>
**listgarten_elevation_hmg_boot**, <br/>
**listgarten_elevation_guideseq_boot**, <br/>
**Kleinstiver_5gRNA_boot**, <br/>
**Seq_offTarget_boot**, <br/>
**Guide_seq** <br/>
] <br/>

from left to right:  **listgarten_elevation_cd33**,  **CIRCLE_seq_10gRNA**, **Listgarten_22gRNA**, **listgarten_elevation_hmg**, **listgarten_elevation_guideseq**, **Kleinstiver_5gRNA**, **Seq_offTarget**, **guide_seq**

##### Experiment 1: Hypothesis : random search (nmc=3k), minimal distances

--- COSINE DISTANCES (1 = perfect match, 0 = worst possible value)---- <br/>
[0.9354, 0.5383, 0.5229, 0.5357, 0.5511, 0.5174, 0.5279, 0.5007] <br/>
[0.5617, 0.8514, 0.5973, 0.8079, 0.5629, 0.5545, 0.5697, 0.7954] <br/>
[0.5396, 0.6031, 0.8692, 0.5991, 0.5518, 0.5572, 0.5668, 0.5556] <br/>
[0.5583, 0.8436, 0.62, 0.8623, 0.5738, 0.5579, 0.5866, 0.8199] <br/>
[0.556, 0.5536, 0.5488, 0.5531, 0.8443, 0.5548, 0.536, 0.507] <br/>
[0.5709, 0.5773, 0.5767, 0.584, 0.5821, 0.8787, 0.5593, 0.5454] <br/>
[0.5703, 0.5641, 0.5736, 0.5756, 0.546, 0.5394, 0.9282, 0.5313] <br/>
[0.5696, 0.8721, 0.6232, 0.8715, 0.5765, 0.5588, 0.6106, 1.0] <br/>


##### Experiment 2: Hypothesis : random search (nmc=2k), minimal distances

--- EUCLIDEAN DISTANCES (the lower, the more similar) ---- <br/>
[1.4907, 5.3074, 5.4469, 5.3573, 5.2287, 5.3942, 5.2483, 5.1092], <br/>
[5.1959, 3.2842, 5.2757, 3.6276, 5.5431, 5.5866, 5.4444, 3.5274], <br/>
[5.3678, 5.1503, 3.1925, 5.1843, 5.641, 5.6394, 5.4839, 5.2006], <br/>
[5.2772, 3.3703, 5.2538, 3.2395, 5.5252, 5.5903, 5.3862, 3.4259], <br/>
[5.2377, 5.6367, 5.6649, 5.6585, 3.1686, 5.5446, 5.6302, 5.6631], <br/>
[5.0889, 5.4519, 5.539, 5.4421, 5.4546, 3.0146, 5.379, 5.4074], <br/>
[5.0638, 5.4321, 5.3894, 5.4189, 5.5656, 5.6421, 2.2365, 5.3892], <br/>
[4.9195, 2.9024, 5.0539, 2.9291, 5.3106, 5.4058, 5.0363, 0.0193] <br/>

--- MANHATTAN DISTANCES (the lower, the more similar) ---- <br/>
[1.4907, 5.3074, 5.4469, 5.3573, 5.2287, 5.3942, 5.2483, 5.1092], <br/>
[5.1959, 3.2842, 5.2757, 3.6276, 5.5431, 5.5866, 5.4444, 3.5274], <br/>
[5.3678, 5.1503, 3.1925, 5.1843, 5.641, 5.6394, 5.4839, 5.2006], <br/>
[5.2772, 3.3703, 5.2538, 3.2395, 5.5252, 5.5903, 5.3862, 3.4259], <br/>
[5.2377, 5.6367, 5.6649, 5.6585, 3.1686, 5.5446, 5.6302, 5.6631], <br/>
[5.0889, 5.4519, 5.539, 5.4421, 5.4546, 3.0146, 5.379, 5.4074], <br/>
[5.0638, 5.4321, 5.3894, 5.4189, 5.5656, 5.6421, 2.2365, 5.3892], <br/>
[4.9195, 2.9024, 5.0539, 2.9291, 5.3106, 5.4058, 5.0363, 0.0193] <br/>

--- COSINE DISTANCES (1 = perfect match, 0 = worst possible value)---- <br/>
to be written <br/>

CCl: conclusive for next steps


##### Experiment 3: Hypothesis : random search (nmc=1k), minimal distances

-- COSINE DISTANCES (1 = perfect match, 0 = worst possible value)---- <br/>
[0.9354, 0.5383, 0.5229, 0.5357, 0.5511, 0.5174, 0.5279, 0.5007] <br/>
[0.5617, 0.8514, 0.5973, 0.8079, 0.5629, 0.5545, 0.5697, 0.7954] <br/>
[0.5396, 0.6031, 0.8692, 0.5991, 0.5518, 0.5572, 0.5668, 0.5556] <br/>
[0.5583, 0.8436, 0.62, 0.8623, 0.5738, 0.5579, 0.5866, 0.8199] <br/>
[0.556, 0.5536, 0.5488, 0.5531, 0.8443, 0.5548, 0.536, 0.507] <br/>
[0.5709, 0.5773, 0.5767, 0.584, 0.5821, 0.8787, 0.5593, 0.5454] <br/>
[0.5703, 0.5641, 0.5736, 0.5756, 0.546, 0.5394, 0.9282, 0.5313] <br/>
[0.5696, 0.8721, 0.6232, 0.8715, 0.5765, 0.5588, 0.6106, 1.0] <br/>


##### Experiment 2: Hypothesis : random search (nmc=2k), minimal distances

--- EUCLIDEAN DISTANCES (the lower, the more similar) ---- <br/>


--- MANHATTAN DISTANCES (the lower, the more similar) ---- <br/>


--- COSINE DISTANCES (1 = perfect match, 0 = worst possible value)---- <br/>
to be written <br/>


##### Experiment 4: Hypothesis : exhaustive search, minimal distances

Computation is too long (estimated computational time around 160hrs). No results to be shown.



#### Data Similarity Analysis between original data sets

Remark: first metric is the distance, second is the std dev.

**With cosine distance**

| Data Set                       | **listgarten_elevation_cd33** | **CIRCLE_seq_10gRNA** | **Listgarten_22gRNA** | **listgarten_elevation_hmg** | **listgarten_elevation_guideseq** | **Kleinstiver_5gRNA** | **Seq_offTarget** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|**listgarten_elevation_cd33**|**0.315;0.1057**|0.305;0.0753|0.309;0.0753|0.307;0.0762|0.314;0.0750|0.309;0.0765|0.306;0.0728|
|**CIRCLE_seq_10gRNA**|0.305;0.0754|**0.370;0.1538**|0.327;0.0683|0.311;0.0810|0.368;0.1422|0.333;0.0756|0.330;0.0863|
|**Listgarten_22gRNA**|0.308;0.0752|0.327;0.0681|**0.356;0.1054**|0.311;0.0730|0.336;0.0675|0.340;0.0747|0.325;0.0696|
|**listgarten_elevation_hmg**|0.307;0.0764|0.311;0.0811|0.311;0.0728|**0.380;0.1536**|0.341;0.0803|0.323;0.0715|0.325;0.0848|
|**listgarten_elevation_guideseq**|0.314;0.0749|0.369;0.1433|0.337;0.0678|0.340;0.0809|**0.394;0.1395**|0.343;0.0739|0.340;0.0866|
|**Kleinstiver_5gRNA**|0.309;0.0759|0.333;0.0760|0.339;0.0745|0.324;0.0717|0.343;0.0738|**0.404;0.1696**|0.337;0.0745|
|**Seq_offTarget**|0.306;0.0724|0.329;0.0848|0.325;0.0697|0.325;0.0852|0.340;0.0868|0.336;0.0745|**0.398;0.1360**|



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

**Metrics for Random Forest Classifier (with class rebalancing = 0.8)**

--- CORRELATION ROC AUC FOR COSINE DISTANCE --- <br/>
listgarten_elevation_cd33.pkl      : 0.903 <br/>
CIRCLE_seq_10gRNA_wholeDataset.csv : 0.160 <br/>
SITE-Seq_offTarget_wholeDataset.csv: 0.063 <br/>
listgarten_elevation_guideseq.pkl  : -0.644 <br/>
Listgarten_22gRNA_wholeDataset.csv : -0.147 <br/>
Kleinstiver_5gRNA_wholeDataset.csv : 0.083 <br/>
listgarten_elevation_hmg.pkl       : -0.167 <br/>
all correlation                    : 0.036 <br/>

--- CORRELATION F1 SCORE FOR COSINE DISTANCE --- <br/>
listgarten_elevation_cd33.pkl      : 0.991 <br/>
CIRCLE_seq_10gRNA_wholeDataset.csv : 0.562 <br/>
SITE-Seq_offTarget_wholeDataset.csv: 0.123 <br/>
listgarten_elevation_guideseq.pkl  : 0.716 <br/>
Listgarten_22gRNA_wholeDataset.csv : -0.192 <br/>
Kleinstiver_5gRNA_wholeDataset.csv : -0.231 <br/>
listgarten_elevation_hmg.pkl       : -0.177 <br/>
all correlation                    : 0.256 <br/>



**TO BE UPLOADED**

| Data Set                       | **CIRCLEseq_cd33** | **Listgarten_22gRNA** | **listgarten_elevation_hmg** | **listgarten_elevation_guideseq** | **CIRCLE_seq_10gRNA** | **Kleinstiver_5gRNA** | **Seq_offTarget** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|

