# Tracking People using YOLOv7 and DeepSORT

## Table of Contents

1. [Overview](#overview)
2. [Getting Started](#getting-started)
3. [Code](#code)
4. [External Work](#external-work)

## Overview

This repository provides a solution for tracking people in low-quality videos. It uses the **YOLOv7** object detector to identify people in each frame and combines these detections with previously tracked bounding boxes using the **DeepSORT** tracker. The **YOLO** and **DeepSORT** packages are located in the `yolo` and `deepsort` folders, respectively, and have been adapted from their official repositories to work with the scripts in this project.

## Getting Started

To set up the necessary Python environment, use the `setup_conda.sh` script. This script requires a working **conda** distribution (Miniconda or Anaconda) and takes one argument for the name of the new environment. The conda environment will include the following major packages:

1. **TensorFlow** 2.8.1 (with **GPU** support)
2. **CUDA** 10.2 (with **CuDNN** 7.6.5)
3. **PyTorch** 1.10.1 (with **TorchVision** 0.11.2)
4. **OpenCV** 4.6.0
5. **Matplotlib** 3.6.3
6. **Pandas** 1.5.3

**Note (1)**: The script may fail if conda packages are updated in their channels.  
**Note (2)**: If you encounter `import` errors, set "channel_priority" to "true" in the ".condarc" file with the priority order: "pytorch" > "conda-forge" > "defaults", and rerun the setup script.

## Code

After setting up the conda environment, run the pipeline with:

```bash
python main.py --input-vid=/path/to/input/video/file --save-path=/path/to/output/video/file
```

This command processes the input video, detects people using the **YOLO** API, and tracks them using the **DeepSORT** API. These APIs are located in the `api` folder. The processed frames with detected and tracked people are saved to the specified output video file.

### Data and Results

You can find the input video, versioned output videos, checkpoints, and a README with versioning details [here](https://drive.google.com/drive/folders/1R2AENddPC9sIk5Lp8nSDv2vLoeAyy8-L?usp=share_link). Download the checkpoints folder to the project root.
