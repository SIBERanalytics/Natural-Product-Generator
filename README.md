### Generation of Natural Product-like molecules 

This repository (imported from https://github.com/skinnider/NPS-generation.git; Citation: Skinnider, M.A., Wang, F., Pasin, D. et al. A deep generative model enables automated structure elucidation of novel psychoactive substances. Nat Mach Intell 3, 973–984 (2021). https://doi.org/10.1038/s42256-021-00407-x) was used to generate natural product(NP)-like molecules by learning the molecular language of ~400,000 known natural product molecules found in the COCONUT(https://coconut.naturalproducts.net) database. 

The results of the experiment and the description of the data generated are presented in the manuscript titled "67 million natural product-like compound database generated via molecular language processing" (DOI: https://doi.org/10.1038/s41597-023-02207-x)

### Usage

`NPG` is defined as the root directory of GitHub Repository "https://github.com/SIBERanalytics/Natural-Product-Generator"

#### Augmenting COCONUT SMILES by a factor of 10 to improve validity of generated SMILES

`python NPG/python/augment-SMILES.py --input_file='/path/to/smiles/coconut_smiles_nostereo_sample80.smi' --output_file='/path/to/augmentedsmiles/coconut_augsmiles.smi' --enum_factor=10  > augment-SMILES.out`

#### Train LSTM model with augmented SMILES and sampling 100M SMILES from the model

`python NPG/python/train_model.py --smiles_file='/path/to/augmentedsmiles/coconut_augsmiles.smi' --output_dir='/path/to/model' --rnn_type='LSTM' --sample_size=100000000  --patience=10000 > train_model.out`

#### Sampling more NP-like SMILES with the trained model 

Note: Output will be written as `sampled-SMILES-$(sample_idx).smi`. We are sampling 1000 more SMILES in the following example.

`python NPG/python/sample_molecules.py --model_file='/path/to/augmentedsmiles/coconut_rnn_model.pt --smiles_file='/path/to/augmentedsmiles/coconut_augsmiles.smi' --mols_per_file=1000 --output_dir=/path/to/output_smiles --sample_idx=1 > sample_molecules.out`

For more advanced options (not used in this study), please visit https://github.com/skinnider/NPS-generation.git

Figshare link to data for training of LSTM model will be provided upon publication of manuscript. 

### Environment

The python packages in the conda environment for running the experiment are identical to that of https://github.com/skinnider/NPS-generation.git. Yaml file is provided as `environment.yml`

```
# Name                    Version                   Build  Channel
_libgcc_mutex             0.1                        main
beautifulsoup4            4.9.3              pyhb0f4dca_0
blas                      1.0                         mkl
brotlipy                  0.7.0           py36h27cfd23_1003
bzip2                     1.0.8                h7b6447c_0
ca-certificates           2021.4.13            h06a4308_1
cairo                     1.14.12              h8948797_3
certifi                   2020.12.5        py36h06a4308_0
cffi                      1.14.0           py36h2e261b9_0
chardet                   3.0.4           py36h06a4308_1003
conda                     4.9.2            py36h06a4308_0
conda-build               3.20.5                   py36_1
conda-package-handling    1.7.2            py36h03888b9_0
cryptography              3.3.1            py36h3c74f83_0
cudatoolkit               10.0.130                      0
cudnn                     7.6.5                cuda10.0_0
deepsmiles                1.0.1                    pypi_0    pypi
et_xmlfile                1.0.1                   py_1001
fcd-torch                 1.0.7                    pypi_0    pypi
filelock                  3.0.12                     py_0
fontconfig                2.13.0               h9420a91_0
freetype                  2.10.4               h5ab3b9f_0
glib                      2.63.1               h5a9c865_0
glob2                     0.7                        py_0
icu                       58.2                 he6710b0_3
idna                      2.10                       py_0
intel-openmp              2020.2                      254
jdcal                     1.4.1                      py_0
jinja2                    2.11.2                     py_0
jpeg                      9b                   h024ee3a_2
lcms2                     2.11                 h396b838_0
ld_impl_linux-64          2.33.1               h53a641e_7
libarchive                3.4.2                h62408e4_0
libboost                  1.73.0              h37e3b65_11
libedit                   3.1.20191231         h14c3975_1
libffi                    3.2.1             hf484d3e_1007
libgcc-ng                 9.1.0                hdf63c60_0
libgfortran-ng            7.3.0                hdf63c60_0
liblief                   0.10.1               he6710b0_0
libpng                    1.6.37               hbc83047_0
libstdcxx-ng              9.1.0                hdf63c60_0
libtiff                   4.1.0                h2733197_1
libuuid                   1.0.3                h1bed415_2
libxcb                    1.14                 h7b6447c_0
libxml2                   2.9.10               hb55368b_3
lz4-c                     1.9.2                heb0550a_3
markupsafe                1.1.1            py36h7b6447c_0
mkl                       2020.2                      256
mkl-service               2.3.0            py36he8ac12f_0
mkl_fft                   1.2.0            py36h23d657b_0
mkl_random                1.1.1            py36h0573a6f_0
ncurses                   6.2                  he6710b0_1
ninja                     1.10.2           py36hff7bd54_0
numpy                     1.19.2           py36h54aff64_0
numpy-base                1.19.2           py36hfa32c7d_0
olefile                   0.46                       py_0
openpyxl                  3.0.7              pyhd3eb1b0_0
openssl                   1.1.1k               h27cfd23_0
pandas                    1.1.3            py36he6710b0_0
patchelf                  0.12                 h2531618_1
pcre                      8.44                 he6710b0_0
pillow                    8.0.1            py36he98fc37_0
pip                       20.3.1           py36h06a4308_0
pixman                    0.40.0               h7b6447c_0
pkginfo                   1.6.1            py36h06a4308_0
psutil                    5.7.2            py36h7b6447c_0
py-boost                  1.73.0          py36h962f231_11
py-lief                   0.10.1           py36h403a769_0
pycosat                   0.6.3            py36h27cfd23_0
pycparser                 2.20                       py_2
pyopenssl                 20.0.0             pyhd3eb1b0_1
pysocks                   1.7.1            py36h06a4308_0
python                    3.6.10               h191fe78_1
python-dateutil           2.8.1                      py_0
python-libarchive-c       2.9                        py_0
pytorch                   1.1.0           cuda100py36he554f03_0
pytz                      2020.4             pyhd3eb1b0_0
pyyaml                    5.3.1            py36h7b6447c_1
rdkit                     2020.09.1.0      py36hd50e099_1    rdkit
readline                  7.0                  ha6073c6_4
requests                  2.25.0             pyhd3eb1b0_0
ripgrep                   12.1.1                        0
ruamel_yaml               0.15.87          py36h7b6447c_1
scipy                     1.5.2            py36h0b6359f_0
selfies                   1.0.2                    pypi_0    pypi
setuptools                51.0.0           py36h06a4308_2
six                       1.15.0           py36h06a4308_0
soupsieve                 2.0.1                      py_0
sqlite                    3.33.0               h62c20be_0
tk                        8.6.10               hbc83047_0
tqdm                      4.54.1             pyhd3eb1b0_0
urllib3                   1.25.11                    py_0
wheel                     0.36.1             pyhd3eb1b0_0
xlrd                      2.0.1              pyhd3eb1b0_0
xz                        5.2.5                h7b6447c_0
yaml                      0.2.5                h7b6447c_0
zlib                      1.2.11               h7b6447c_3
zstd                      1.4.5                h9ceee32_0
```
