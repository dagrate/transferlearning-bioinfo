# transferlearning-bioinfo

Transfer learning for gene editing.

Data preprocessing in transferlearning_crispr_datapipeline.ipynb.


------

## Experiments

### Data Set Description

| Data Set                       | **Nbr of samples in minority class (N_min)** | **Nbr of samples in majority class (N_maj)** | **Class imbalance ratio (N_min/N_maj)** |
| :---:                          |     :---:                |    :---:                  |             :---:              |
| **listgarten_elevation_cd33**      |      2273            |       2800                |       0.468                    |
| **listgarten_elevation_hmg**       |      52              |       10077               |       0.005                    |
| **Kleinstiver_5gRNA_wholeDataset** |      54              |       95775               |       0.001                    |
| **Listgarten_22gRNA_wholeDataset** |      56              |       383463              |       <0.001                   |
| **elevation_guideseq**             |     354              |       294180              |       0.001                    |
| **CIRCLE_seq_10gRNA**              |     7371             |       577578              |       0.013                    |
| **SITE_seq_offtarget**             |     7371             |       213966              |       0.017                    |



### Preliminary Results

Metrics displayed are the ROC AUC and the F1 Score Class 1.

*How to read the table:* for (listgarten_elevation_cd33 x listgarten_elevation_cd33), the model is trained and tested on listgarten_elevation_cd33. For (listgarten_elevation_cd33 x listgarten_elevation_hmg), the model is trained on listgarten_elevation_cd33, and tested on listgarten_elevation_hmg. Thus, we apply transfer learning on listgarten_elevation_hmg. 


**Metrics for Random Forest Classifier (without class rebalancing)**

@settings{
  font-size: 100;

| Data Set                       | **listgarten_elevation_cd33** | **listgarten_elevation_hmg** | **Kleinstiver_5gRNA_wholeDataset** |
| :---:                          |     :---:                     |    :---:                     |             :---:                  |
| **listgarten_elevation_cd33**      |      0.879; 0.768         |       0.626; 0.015           |       0.634; 0.002                 |
| **listgarten_elevation_hmg**       |      0.476; 0.000         |       0.589; 0.000           |       0.508; 0.036                 |
| **Kleinstiver_5gRNA_wholeDataset** |      0.490; 0.000         |       0.551; 0.000           |       0.595; 0.100                 |

}

Remark: class imbalance on some of the data sets is high. Thus, it impacts strongly the classifier performance.

**Metrics for Random Forest Classifier (with class rebalancing, ratio N_min/N_maj:TBD.)**
**WORK IN PROGRESS**
| Data Set                       | **listgarten_elevation_cd33** | **listgarten_elevation_hmg** | **Kleinstiver_5gRNA_wholeDataset** |
| :---:                          |     :---:                     |    :---:                     |             :---:                  |
| **listgarten_elevation_cd33**      |      0.000; 0.000         |       0.000; 0.000           |       0.000; 0.000                 |
| **listgarten_elevation_hmg**       |      0.000; 0.000         |       0.000; 0.000           |       0.000; 0.000                 |
| **Kleinstiver_5gRNA_wholeDataset** |      0.000; 0.000         |       0.000; 0.000           |       0.000; 0.000                 |


More to be uploaded soon.
