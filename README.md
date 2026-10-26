# NISAR data processing
This repository demonstrates how to download NISAR data and retrieve and visualize interferometric phase, coherence, and correction files (e.g., ionospheric and tropospheric corrections).

## Set up the Conda environment

First, clone the repository and create a Conda environment.

```bash
git clone https://github.com/nafissk/nisar_test.git && cd nisar_test
conda env create -f environment.yml
conda activate insar-env
```

## Set up EarthData account

Create an Earthdata account to download SAR images: https://urs.earthdata.nasa.gov/users/new

### Writing your Earthdata account information to a `.netrc` file
A number of InSAR processing programs use a special hidden file called `.netrc` in your home directory on the computer where you run them to access your saved Earthdata username and password. This allows them to download data without requiring you to enter your Earthdata login every time.

You can create the `.netrc` file by running the command below in a terminal window. Replace `myUsername` with your username and `myPassword` with your password:

```bash
echo "machine urs.earthdata.nasa.gov login myUsername password myPassword" > $HOME/.netrc
```


Because the `.netrc` file contains your personal password, you should change its permissions so that nobody else can read it. Some programs check the file permissions and refuse to run until the file is not readable by anyone else.

Use the standard Linux or Unix file permission command `chmod` to change the file permissions. The `600` permission allows you to read and write the file while preventing others from accessing it. Run this command in a terminal:

```bash
chmod 600 $HOME/.netrc
```
### Download data
For the demonstration, we will download data for the Venezuela earthquakes. On June 24, 2026, two earthquakes with magnitudes of 7.2 and 7.5 occurred in northern Venezuela, west of Caracas. The interferogram was derived from NISAR (NASA-ISRO Synthetic Aperture Radar) data acquired on June 25 (after the earthquakes) and June 13 (before the earthquakes).

```bash
wget https://nisar.asf.earthdatacloud.nasa.gov/NISAR/NISAR_L2_GUNW_PROVISIONAL_V1/NISAR_L2_PR_GUNW_022_162_A_007_023_4000_SH_20260613T100656_20260613T100731_20260625T100655_20260625T100730_P05023_N_F_J_001/NISAR_L2_PR_GUNW_022_162_A_007_023_4000_SH_20260613T100656_20260613T100731_20260625T100655_20260625T100730_P05023_N_F_J_001.h5
```
