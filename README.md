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


### Bootstrapped data such that class imbalance ratio is maintained identical to the original data sets.

| Data Set                       | **Nbr of samples in minority class (N_min)** | **Nbr of samples in majority class (N_maj)** | **Class imbalance ratio (N_min/N_maj)** |
|:---:|:---:|:---:|:---:|
|**listgarten_elevation_cd33**  |117|133|0.468|
|**CIRCLE_seq_10gRNA**          |3|247|0.013|
| **SITE_seq_offtarget**        |4|246|0.017|
| **elevation_guideseq**        |0|250|<0.001|
| **Listgarten_22gRNA**         |0|250|<0.001|
| **Kleinstiver_5gRNA**         |0|250|<0.001|
| **listgarten_elevation_hmg**  |1|249|0.005|


### Data Similarity Analysis


#### Data Similarity Analysis between bootstrapped data and original data sets
from left to right:  **listgarten_elevation_cd33**,  **CIRCLE_seq_10gRNA**, **Listgarten_22gRNA**, **listgarten_elevation_hmg**, **listgarten_elevation_guideseq**, **Kleinstiver_5gRNA**, **Seq_offTarget**

##### Experiment 1: Hypothesis : random search (nmc=2k), minimal distances

--- EUCLIDEAN DISTANCES (the lower, the more similar) ---- <br/>
listgarten_elevation_cd33_boot: [1.3977, 5.2809, 5.4279, 5.341, 5.2283, 5.4269, 5.2436]  <br/>
CIRCLE_seq_10gRNA_boot: [5.1996, 3.2476, 5.3034, 3.5988, 5.5554, 5.6006, 5.4666]  <br/>
Listgarten_22gRNA_boot: [5.3715, 5.1515, 3.0817, 5.1959, 5.6527, 5.6003, 5.5161]  <br/>
listgarten_elevation_hmg_boot: [5.2901, 3.314, 5.2003, 3.1697, 5.5135, 5.592, 5.3902]  <br/>
listgarten_elevation_guideseq_boot: [5.2459, 5.6058, 5.6767, 5.6207, 3.0845, 5.5407, 5.623]  <br/>
Kleinstiver_5gRNA_boot: [5.1016, 5.454, 5.5316, 5.4568, 5.4171, 2.9346, 5.4315]  <br/>
Seq_offTarget_boot: [5.0977, 5.4297, 5.442, 5.4455, 5.5744, 5.6849, 2.269]  <br/>

--- MANHATTAN DISTANCES (the lower, the more similar) ---- <br/>
listgarten_elevation_cd33_boot: [3.536, 28.088, 29.552, 28.504, 27.48, 29.68, 27.448] <br/>
CIRCLE_seq_10gRNA_boot: [27.012, 10.992, 28.588, 13.564, 31.012, 31.492, 29.868] <br/>
Listgarten_22gRNA_boot: [28.84, 27.46, 10.368, 27.976, 32.128, 31.528, 30.512] <br/>
listgarten_elevation_hmg_boot: [27.864, 11.324, 27.72, 10.232, 30.44, 31.312, 28.664] <br/>
listgarten_elevation_guideseq_boot: [27.576, 31.4, 32.264, 31.672, 10.664, 30.824, 31.552] <br/>
Kleinstiver_5gRNA_boot: [26.0319, 29.8526, 30.7291, 29.8645, 29.3865, 9.3147, 29.9044]  <br/>
Seq_offTarget_boot: [26.032, 29.772, 29.784, 29.424, 31.288, 32.344, 6.28] <br/>

--- COSINE DISTANCES (1 = perfect match, 0 = worst possible value)---- <br/>
listgarten_elevation_cd33_boot: [0.9319, 0.531, 0.5185, 0.5306, 0.5472, 0.5092, 0.5231]  <br/>
CIRCLE_seq_10gRNA_boot: [0.5551, 0.843, 0.5909, 0.806, 0.5544, 0.5481, 0.5561]  <br/>
Listgarten_22gRNA_boot: [0.5353, 0.6065, 0.8542, 0.6102, 0.5443, 0.5531, 0.554]  <br/>
listgarten_elevation_hmg_boot: [0.5505, 0.8384, 0.6093, 0.8582, 0.5665, 0.5567, 0.5796]  <br/>
listgarten_elevation_guideseq_boot: [0.548, 0.5479, 0.5441, 0.5485, 0.8495, 0.5546, 0.5293]  <br/>
Kleinstiver_5gRNA_boot: [0.572, 0.5688, 0.5639, 0.5738, 0.5765, 0.8668, 0.5559]  <br/>
Seq_offTarget_boot: [0.5638, 0.5632, 0.5711, 0.5727, 0.5406, 0.5253, 0.9092] <br/>

CCl: conclusive for next steps

##### Experiment 2: Hypothesis : random search (nmc=20k), average distances

--- EUCLIDEAN DISTANCES (the lower, the more similar) ---- <br/>
listgarten_elevation_cd33_boot: [5.8558, 6.4472, 6.5366, 6.4772, 6.4518, 6.4516, 6.3756] <br/>
CIRCLE_seq_10gRNA_boot: [6.4414, 6.5248, 6.853, 6.5883, 6.8169, 6.785, 6.8197] <br/>
Listgarten_22gRNA_boot: [6.5139, 6.8274, 6.4967, 6.8375, 6.8765, 6.8254, 6.8006] <br/>
listgarten_elevation_hmg_boot: [6.4861, 6.5813, 6.8514, 6.5064, 6.8261, 6.7876, 6.7366] <br/>
listgarten_elevation_guideseq_boot: [6.4504, 6.8139, 6.8826, 6.8181, 6.6589, 6.7559, 6.8369] <br/>
Kleinstiver_5gRNA_boot: [6.4454, 6.7793, 6.8274, 6.7887, 6.7666, 6.3563, 6.7869] <br/>
Seq_offTarget_boot: [6.3642, 6.8079, 6.805, 6.7285, 6.8344, 6.7618, 6.3466] <br/>

--- MANHATTAN DISTANCES (the lower, the more similar) ---- <br/>
[34.4935, 41.6898, 42.7729, 42.134, 41.7425, 41.8098, 40.7785] <br/>
[41.5926, 43.4814, 47.3024, 44.3426, 46.6471, 46.2336, 46.6098] <br/>
[42.5546, 46.8653, 42.9433, 47.0107, 47.414, 46.7397, 46.6227] <br/>
[42.1289, 44.2231, 47.1408, 43.102, 46.7291, 46.2104, 45.4986] <br/>
[41.7717, 46.5481, 47.5366, 46.6405, 44.777, 45.8521, 46.8896] <br/>
[41.6596, 46.0727, 46.7593, 46.2748, 45.8743, 41.4648, 46.2219] <br/>
[40.6229, 46.5436, 46.5289, 45.3125, 46.8279, 45.8214, 41.1603] <br/>

--- COSINE DISTANCES (1 = perfect match, 0 = worst possible value)---- <br/>
[0.3156, 0.3033, 0.3032, 0.3122, 0.3083, 0.3068, 0.3065] <br/>
[0.3051, 0.369, 0.3277, 0.3683, 0.3256, 0.3313, 0.3116] <br/>
[0.3056, 0.3293, 0.3973, 0.3407, 0.3271, 0.3376, 0.3251] <br/>
[0.3118, 0.3702, 0.3387, 0.3942, 0.3359, 0.3432, 0.3409] <br/>
[0.3085, 0.3278, 0.3266, 0.3383, 0.3558, 0.3421, 0.3116] <br/>
[0.3091, 0.3341, 0.3381, 0.343, 0.3399, 0.4035, 0.3216] <br/>
[0.3075, 0.3111, 0.3261, 0.3397, 0.3114, 0.3255, 0.3808] <br/>

CCl: not conclusive for next steps


##### Experiment 3: Hypothesis : exhaustive search, minimal distances

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

**Metrics for Random Forest Classifier (without class rebalancing)**

**TO BE UPLOADED**

| Data Set                       | **CIRCLEseq_cd33** | **Listgarten_22gRNA** | **listgarten_elevation_hmg** | **listgarten_elevation_guideseq** | **CIRCLE_seq_10gRNA** | **Kleinstiver_5gRNA** | **Seq_offTarget** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|

