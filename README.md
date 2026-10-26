# NISAR data processing
This reposiratory will demonstrate how to download NISAR data, and also get and visualize the interfeofram phase, coherence and correction files (ionosphere, troposhere).

## Set up conda enviorbment

First clone the repository and make a conda environment.

```bash
git clone https://github.com/nafissk/nisar_test.git
conda env create -f environment.yml
conda activate insar-env
```

## Set up EarthData account

Create a account in EarthData for downloading SAR images from this website. Link: https://urs.earthdata.nasa.gov/users/new

### Writing your EarthData account information to a `.netrc` file
A number of InSAR processing programs use a special hidden file called `.netrc` in the home directory of your account on the computer where you run them to get a saved version of your EarthData username and password. This allows them to download data without you having to enter the EarthData login every time.

You can create the `.netrc` file by running the command below in a terminal window substituting your username (instead of `myUsername`) and your password (instead of `myPassword`):

```bash
echo "machine urs.earthdata.nasa.gov login myUsername password myPassword" > $HOME/.netrc
```


Because the `.netrc` file has your personal password, you should change the file protections so that nobody can view it. Some programs will check the file permissions and refuse to run until you make the file not readable by anybody else.

We use the standard Linux or Unix file permission command `chmod` to change the file permissions. The permissions `600` means readable by you and nobody else. Again, you can do this in a terminal window or use the notebook cell below.

```bash
chmod 600 $HOME/.netrc
```
### Download data
For, demonastration we will download data for Venezuella earthquake. On June 24th, 2026, a pair of earthquakes of Magnitude 7.2 and Magnitude 7.5 occurred in northern Venezuela, west of Caracas. The interferogram was derived from NISAR (NASA-ISRO Synthetic Aperture Radar) data acquired on June 25 June (after the earthquakes) and June 13  (before the earthquakes).

```bash
!wget https://nisar.asf.earthdatacloud.nasa.gov/NISAR/NISAR_L2_GUNW_PROVISIONAL_V1/NISAR_L2_PR_GUNW_022_162_A_007_023_4000_SH_20260613T100656_20260613T100731_20260625T100655_20260625T100730_P05023_N_F_J_001/NISAR_L2_PR_GUNW_022_162_A_007_023_4000_SH_20260613T100656_20260613T100731_20260625T100655_20260625T100730_P05023_N_F_J_001.h5
```
