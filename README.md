# ECPA_Emotional_Video_Captioning
Human-centric Emotional Video Captioning (H-EVC) aims to generate fine-grained, emotion-related sentences for human-based videos, enhancing human emotions and facilitating human-computer emotional interaction.

# Requirements
We use [Docker image of SwinBert](https://hub.docker.com/r/linjieli222/videocap_torch1.7/tags) for easier reproduction. Please install the following:
Nvidia driver (418+),
Docker (19.03+),
nvidia-container-toolkit.
We only support Linux with NVIDIA GPUs. We test on Ubuntu 18.04 and RTX 3090 Ti card. 
# Download
## Create folders that store pretrained models, datasets, and predictions.
<div style="background-color: #f6f8fa; padding: 10px; border-radius: 5px;">

```bash
export REPO_DIR=$PWD
mkdir -p $REPO_DIR/models  # pre-trained models
mkdir -p $REPO_DIR/datasets  # datasets
mkdir -p $REPO_DIR/predictions  # prediction outputs
```
## Pretrained models.

Our pre-trained models can be downloaded with the following command.
<div style="background-color: #f6f8fa; padding: 10px; border-radius: 5px;">

```bash
cd $REPO_DIR
bash scripts/download_models.sh
```
The script will download our models that are trained for VATEX, MSRVTT, MSVD, TVC and YouCook2, respectively. It will also download our training logs and output predictions.
## Pretrained Video Swin Transformers.
To run our code smoothly, please visit [Video Swin Transformer](https://github.com/SwinTransformer/Video-Swin-Transformer) to download pre-trained weights models.
Download swin_base_patch244_window877_kinetics*_22k.pth, and place them under ${REPO_DIR}/models/video_swin_transformer directory.
# Quick Demo
We provide a demo to run end-to-end inference on the test video. Our inference code will take a human-based video as input and generate an emotional video caption. [MAFW](https://example.com/data.zip) | [EmoVidCap](https://example.com/checkpoint.zip)| [best-checkpoint](https://example.com/checkpoint.zip)

# After launching the docker container 
<div style="background-color: #f6f8fa; padding: 10px; border-radius: 5px;">

```bash
EVAL_DIR='./models/table1/MAFW/best-checkpoint/'
CHECKPOINT='./models/table1/MAFW/best-checkpoint/model.bin'
VIDEO='./docs/G0mjFqytJt4_000152_000162.mp4'
CUDA_VISIBLE_DEVICES=0 python src/tasks/run_caption_VidSwinBert_inference.py \
       --resume_checkpoint $CHECKPOINT  \
       --eval_model_dir $EVAL_DIR \
       --test_video_fname $VIDEO \
       --do_lower_case \
       --do_test 
```    

# Evakuation results
Performances w/o our ECPA under different captioning frameworks with various vision-language models. The best results are in bold, and the second is underlined.

![Example Image](samples/table5.png)

# ⭐ Demos


以下是三个GIF动画及其对应文字的示例：

<table>
  <tr>
    <td style="text-align: center; padding: 10px;">
      <img src="samples/02253.gif" alt="演示动画1" style="width: 300px; height: 200px; border-radius: 8px;">
      <div style="background-color: #f6f8fa; padding: 10px; border-radius: 8px; margin-top: 10px;">
        <p>GT: A man looks at his laptop and speaks.</p>
      </div>
    </td>
    <td style="text-align: center; padding: 10px;">
      <img src="samples/02358.gif" alt="演示动画2" style="width: 300px; height: 200px; border-radius: 8px;">
      <div style="background-color: #f6f8fa; padding: 10px; border-radius: 8px; margin-top: 10px;">
        <p>GIF 2 的描述文字</p>
      </div>
    </td>
    <td style="text-align: center; padding: 10px;">
      <img src="samples/01158.gif" alt="演示动画3" style="width: 300px; height: 200px; border-radius: 8px;">
      <div style="background-color: #f6f8fa; padding: 10px; border-radius: 8px; margin-top: 10px;">
        <p>GIF 3 的描述文字</p>
      </div>
    </td>
  </tr>
</table>

