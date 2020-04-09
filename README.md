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
There are many scripts. We will choose from each category to execute the extraction/trainging/faking process 
  
The Scripts:
1_clear_workspace.sh
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
6_train_Quick96.sh
6_train_SAEHD.sh
7_merge_Quick96.sh
7_merge_SAEHD.sh
8_merged_to_avi.sh
8_merged_to_mov_lossless.sh
8_merged_to_mp4_lossless.sh
8_merged_to_mp4.sh
env.sh

Navigate to the DeepFaceLab_NVIDIA_Linux directory 
cd ~/DeepFaceLab_NVIDIA_Linux 

give permissions on the scripts folder(check this)  
chmod +x scripts -R  

Navigate to the scripts directory 
cd ~/DeepFaceLab_NVIDIA_Linux/scripts  


run the scripts in this order
Set up  
This will create/clear the workspace folder - only use this at the beginning of the process.
./1_clear_workspace.sh  

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

Move the data_src.mp4 and data_dst.mp4 files into the workspace folder  

Extract from source files  
2_extract_images_from_video_data_src.sh  
3_extract_images_from_video_data_dst_FULL_FPS.sh  
4_data_src_extract_full_face_S3FD.sh  
4.2_data_src_util_add_landmarks_debug_images.sh
5_data_dst_extract_full_face_MANUAL_RE-EXTRACT_DELETED_ALIGNED_DEBUG.sh  
5_data_dst_extract_whole_face_S3FD.sh  
5.2_data_dst_sort.sh  
5.2_data_dst_util_recover_original_filename.sh  
  
batch rename for linux  
Preview the change  
rename 's/\_0//g' *.jpg -n  
  
Execute the command  
rename 's/\_0//g' *.jpg  

