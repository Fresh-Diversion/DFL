# Install DeepFaceLab
**Note:** This installation method uses Anaconda to install DFL on Centos 7/8 or Ubuntu 18.04  
To install CentOS, refer [here](install_CentOS.md)

**Note:** The directory structure is important.  
This is how the project tree will look like:  
```bash
DeepFaceLab_NVIDIA_Linux
|-- _internal               
|   |-- DeepFaceLab         # Created via git clone command (Step #2)
|   |-- pretrain_CelebA     # Manually copied after extracting .EXE (Step #3)
|   `-- pretrain_Quick96    # Manually copied after extracting .EXE (Step #3)
|-- install_script          # Created via git clone command (Step #0)
|-- scripts                 # Created via git clone command (Step #0)
`-- workspace               # Created through one of the scripts in /scripts
```

## Step #0: Preparation
Clone this repository  
```sh
git clone https://github.com/jwchoi09/DeepFaceLab_NVIDIA_Linux.git
cd DeepFaceLab_NVIDIA_Linux
```

### Step #0-1: Install NVIDIA driver and Dependencies
Navigate to <b>`DeepFaceLab_NVIDIA_Linux/install_script`</b> directory and run:
<ol type="a">
    <li><b>CentOS:</b><pre>bash 1_CentOS_install_dependencies.sh</pre>  
    <li><b>Ubuntu:</b><pre>bash 1_Ubuntu_install_dependencies.sh</pre>
</ol>


## Step #1: Install Anaconda
URL #4: https://www.anaconda.com/distribution/#linux  
URL #5: https://docs.anaconda.com/anaconda/install/linux/

**Note:** Download Python 3.7 version (at the time of writing: 03/16/2020)  
Through the terminal, locate to Anaconda download destination and run the following:  
```sh
bash Anaconda3-2020.02-Linux-x86_64.sh
```

The installer prompts "In order to continue the installation process, please review the license agreement."  
Click Enter to view license terms.  
Scroll to the bottom of the license terms and enter "Yes" to agree.  
Accept the default install location.  
Type "yes" to the prompt, "Do you wish the installer to initialize Anaconda3 by running conda init?"  
Close and open your terminal window for the installation to take effect, or you can enter the command:  
```sh
source ~/.bashrc
```


## Step #2: Install DeepFaceLab_NVIDIA
Create the DeepFaceLab environment with the following libraries.  
Enter the following in the terminal:  
```bash
conda create -n deepfacelab -c main python=3.6.8 cudnn=7.6.5 cudatoolkit=10.0.130
```

Activate the environment  
```bash
conda activate deepfacelab
```

Navigate to `_internal` directory in `DeepFaceLab_NVIDIA_Linux`  
```sh
cd DeepFaceLab_NVIDIA_Linux/_internal
```

Install Python Dependencies
```sh
python3 -m pip install -r ./DeepFaceLab/requirements-cuda.txt  
```

Delete the already existing DeepFaceLab directory, and  
Clone DeepFaceLab from the main repository to the `_internal` directory  
```sh
sudo rm -rf DeepFaceLab
git clone https://github.com/iperov/DeepFaceLab.git
```

## Step #3: Download CelebA Dataset and Quick96 Model

Download the latest NVIDIA build(.EXE) from the main repo for Windows  
To download, refer to the Google Drive link provided in here: https://github.com/iperov/DeepFaceLab/  
Extract the build.  
```sh
7z x DeepFaceLab_NVIDIA_build_XX_XX_XXX.exe
```

Once the build has been extracted, there will be `_internal` directory.  
From it, copy both `pretrain_CelebA` and `pretrain_Quick96` to the directory `DeepFaceLab_NVIDIA_Linux/_internal/`  


## Step #4: Navigate to the scripts directory and begin using DeepFaceLab
(Further guide coming soon!)  
https://mrdeepfakes.com/forums/thread-guide-deepfacelab-2-0-explained-and-tutorials-recommended  
  
Confirm the build directory is set up properly  
  
There are many scripts. We will choose from each category to execute the extraction/trainging/merging process 
  
The Scripts: 
SETUP  
1_clear_workspace.sh  

EXTRACT:  
2_extract_images_from_video_data_src.sh  
3_cut_video_drop_video_on_me.sh  
3_extract_images_from_video_data_dst_FULL_FPS.sh  
4.2_data_src_sort.sh  
4.2_data_src_util_add_landmarks_debug_images.sh  
4.2_data_src_util_faceset_enhance.sh  
4.2_data_src_util_faceset_metadata_restore.sh  
4.2_data_src_util_faceset_metadata_save.sh  
4.2_data_src_util_faceset_pack.sh  
4.2_data_src_util_faceset_unpack.sh  
4.2_data_src_util_recover_original_filename.sh  
4_data_src_extract_full_face_MANUAL.sh  
4_data_src_extract_full_face_S3FD.sh  
4_data_src_extract_whole_face_MANUAL.sh  
4_data_src_extract_whole_face_S3FD.sh  
5.2_data_dst_sort.sh  
5.2_data_dst_util_faceset_pack.sh  
5.2_data_dst_util_faceset_unpack.sh  
5.2_data_dst_util_recover_original_filename.sh  
5.3_data_dst_mask_editor.sh  
5_data_dst_extract_full_face_MANUAL_RE-EXTRACT_DELETED_ALIGNED_DEBUG.sh  
5_data_dst_extract_full_face_MANUAL.sh  
5_data_dst_extract_full_face_S3FD_+_manual_fix.sh  
5_data_dst_extract_full_face_S3FD.sh  
5_data_dst_extract_whole_face_MANUAL_RE_+_EXTRACT_DELETED_ALIGNED_DEBUG.sh  
5_data_dst_extract_whole_face_MANUAL.sh  
5_data_dst_extract_whole_face_S3FD_+_manual_fix.sh  
5_data_dst_extract_whole_face_S3FD.sh  
5.XSeg_data_dst_edit.sh  
5.XSeg_data_dst_merge.sh  
5.XSeg_data_dst_split.sh  
5.XSeg_data_src_edit.sh  
5.XSeg_data_src_merge.sh  
5.XSeg_data_src_split.sh  
5.XSeg_train.sh  

TRAIN:  
6_train_Quick96.sh  
6_train_SAEHD.sh  

MERGE:  
7_merge_Quick96.sh  
7_merge_SAEHD.sh  

CONVERT TO VIDEO:
8_merged_to_avi.sh  
8_merged_to_mov_lossless.sh  
8_merged_to_mp4_lossless.sh  
8_merged_to_mp4.sh  
env.sh  
  
Navigate to the DeepFaceLab_NVIDIA_Linux directory 
```sh
cd ~/DeepFaceLab_NVIDIA_Linux 
```
  
give permissions on the scripts folder(check this)  
```sh
chmod +x scripts -R  
```

Navigate to the scripts directory 
```sh
cd ~/DeepFaceLab_NVIDIA_Linux/scripts 
```
  
The 3 main steps of creating a deepfake are Extract, Train, and Merge  
Run the scripts in this order:  

SET UP  
This will create/clear the workspace folder - only use this at the beginning of the process.  
```sh
./1_clear_workspace.sh  
```
  
Move the data_src.mp4 and data_dst.mp4 files into the workspace folder 
  
the folder should look like this:  
```bash
|-- workspace        
|   |-- data_dst 
|       |--aligned  
|   |-- data_src  
|       |--aligned  
|   |-- model  
|   -- data_dst.mp4  
|   -- data_src.mp4  
```
  

EXTRACT
Extract frames from src file  
The next script has 2 options:  
A) FPS -> you can choose the FPS. The greater the FPS the more material will be available to work with = longer time  
B) Output Image Format png/jpg ->  
```bash
./2_extract_images_from_video_data_src.sh  
```
When Finished, the data_src folder should have folder named aligned and the extracted frames from the data_src movie together   
  
Extract frames from dst file  
The next script has 1 option:  
A) Output Image Format png/jpg ->  
```bash
./3_extract_images_from_video_data_dst_FULL_FPS.sh 
```  
When finished, the data_dst folder should have folder named aligned and the extracted frames from the data_dst movie together  

Extract Faces,align the landmarks from the src 
The next script has 2 options:  
A)gpu or cpu  
B)choosing whether to generate "aligned_debug" folder or not. -> I think doing this is a good idea  
```sh
./4_data_src_extract_full_face_S3FD.sh
```
When finished, the data_src folder should have folder named aligned_debug with the extracted frames from the data_src frames inside. The frames in aligned_debug should have the alignments     
  
Clean the source faceset/dataset of false positives/incorrectly aligned faces  
The next script has 13 options:  
Choose sorting method:  
[0] blur  
[1] face yaw direction  
[2] face pitch direction  
[3] face rect size in source image  
[4] histogram similarity  
[5] histogram dissimilarity  
[6] brightness  
[7] hue  
[8] amount of black pixels  
[9] original filename  
[10] one face in image  
[11] absolute pixel difference  
[12] best faces  
[13] best faces faster  

```sh
./4.2_data_src_sort.sh
```
Choose 4 if you don't know what to choose  

Add land marks to debug images if the option was not chosen before
```sh
4.2_data_src_util_add_landmarks_debug_images.sh  
```

Extract Faces,align the landmarks from the dst  
The next script has 1 option:  
A)gpu or cpu  

```sh
./5_data_dst_extract_whole_face_S3FD.sh
```
When finished, the data_dst folder should have a folder named aligned_debug. The frames in aligned_debug should have the alignments.  
 
Clean the dst faceset/dataset of false positives/incorrectly aligned faces  
The next script has 13 options:  
Choose sorting method:  
[0] blur  
[1] face yaw direction  
[2] face pitch direction  
[3] face rect size in source image  
[4] histogram similarity  
[5] histogram dissimilarity  
[6] brightness  
[7] hue  
[8] amount of black pixels  
[9] original filename  
[10] one face in image  
[11] absolute pixel difference  
[12] best faces  
[13] best faces faster  

```sh
./5.2_data_dst_sort.sh  
```
Choose 4 if you don't know what to choose 

When finished, the data_dst folder should have a folder named aligned with the extracted faces from the data_dst frames inside  


TRAINING  
  
There are 2 methods for training:  
6_train_Quick96.sh - one option -> cpu/gpu  
6_train_SAEHD.sh - many options    
  
```sh
./6_train_Quick96.sh
```

The longer the training, the better
when finished - around 150000 iterations
press ctrl + c in the terminal to quit
  
MERGING  

There are 2 methods for merging:  
7_merge_Quick96.sh  
7_merge_SAEHD.sh  

```SH
./7_merge_Quick96.sh
```

CONVERSION
There are 4 methods for converging:
8_merged_to_avi.sh  
8_merged_to_mov_lossless.sh  
8_merged_to_mp4_lossless.sh  
8_merged_to_mp4.sh 
  
The next script has 1 option:  
bitrate - 16 is suggested  

```sh
./8_merged_to_mp4.sh 
```








not sure about this:
5.2_data_dst_util_recover_original_filename.sh  
  
batch rename for linux  
Preview the change  
rename 's/\_0//g' *.jpg -n  
  
Execute the command  
rename 's/\_0//g' *.jpg  

