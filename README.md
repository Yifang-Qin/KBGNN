## KBGNN

This is the pytorch implementation for our ICDM 2022 [paper](https://arxiv.org/abs/2210.03969):
> Wei Ju, Yifang Qin, Ziyue Qiao, Xiao Luo, Yifan Wang, Yanjie Fu, and Ming Zhang(2022). Kernel-based Substructure Exploration
for Next POI Recommendation

In this paper, we propose a Kernel-Based Graph Neural Network (KBGNN) for
next POI recommendation, which combines the characteristics
of both geographical and sequential influences in a collaborative
way.

Please cite our paper if you use the code.

### Environment Requirement

The code has been tested running under Python 3.8.13. The required packages are as follows:

- pytorch == 1.11.0 
- torch_geometric == 2.0.4 
- pandas == 1.4.1
- sklearn == 0.23.2
``
### Running Example

For example, to generate `Foursquare-Tokyo` data for KBGNN models, firstly the [raw data](https://sites.google.com/site/yangdingqi/home/foursquare-dataset
) should be downloaded and unzipped at `~/raw_data/`.

After the download, run:
```shell
mkdir processed && cd processed
mkdir tky
cd ../utils
python process_data.py
```
which will generate processed data files under the directory `~/processed/tky/`.

To conduct experiment on `Foursquare-Tokyo`, run:
```shell
cd ./model
python main.py --data tky --batch 1024 --patience 10 --gcn_num 2 --max_step 2
```
For more execution arguments of KBGNN, please refer to `~/model/main.py` or run
```shell
python main.py -h
```