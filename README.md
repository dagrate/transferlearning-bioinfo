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



### Preliminary Results

Metrics displayed are the ROC AUC and the F1 Score Class 1.

*How to read the table:* for (listgarten_elevation_cd33 x listgarten_elevation_cd33), the model is trained and tested on listgarten_elevation_cd33. For (listgarten_elevation_cd33 x listgarten_elevation_hmg), the model is trained on listgarten_elevation_cd33, and tested on listgarten_elevation_hmg. Thus, we apply transfer learning on listgarten_elevation_hmg. 


**Metrics for Random Forest Classifier (without class rebalancing)**


| Data Set                       | **Listgarten_22gRNA** | **listgarten_elevation_cd33** | **listgarten_elevation_hmg** | **listgarten_elevation_guideseq** | **CIRCLE_seq_10gRNA** | **Kleinstiver_5gRNA** | **Seq_offTarget** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|**Listgarten_22gRNA**|.523;.000|.517;.000|.530;.000|.499;.000|.501;.000|.496;.000|.517;.000|
|**listgarten_elevation_cd33**|.768;.0.001|.879;.768|.626;.015|.620;.004|.753;.051|.634;.002|.707;.082|
|**listgarten_elevation_hmg**|.531;.000|.476;.000|.589;.000|.735;.000|.606;.000|.508;.036|.536;.000|
|**listgarten_elevation_guideseq**|.565;.000|.521;.000|.644;.000|.734;.000|.565;.068|.522;.000|.553;.009|
|**CIRCLE_seq_10gRNA**              |
|**Kleinstiver_5gRNA**              |0.490;0.000|0.551;0.000|0.595; 0.100|
|**Seq_offTarget**                  |

Remark: class imbalance on some of the data sets is high. Thus, it impacts strongly the classifier performance.

**Metrics for Random Forest Classifier (with class rebalancing, ratio N_min/N_maj:TBD.)**
**WORK IN PROGRESS**
| Data Set                       | **listgarten_elevation_cd33** | **listgarten_elevation_hmg** | **Kleinstiver_5gRNA_wholeDataset** |
| :---:                          |     :---:                     |    :---:                     |             :---:                  |
| **listgarten_elevation_cd33**      |      0.000; 0.000         |       0.000; 0.000           |       0.000; 0.000                 |
| **listgarten_elevation_hmg**       |      0.000; 0.000         |       0.000; 0.000           |       0.000; 0.000                 |
| **Kleinstiver_5gRNA_wholeDataset** |      0.000; 0.000         |       0.000; 0.000           |       0.000; 0.000                 |


More to be uploaded soon.
