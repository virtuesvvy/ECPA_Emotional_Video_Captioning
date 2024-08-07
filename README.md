# ECPA_Emotional_Video_Captioning
Human-centric Emotional Video Captioning (H-EVC) aims to generate fine-grained, emotion-related sentences for human-based videos, enhancing human emotions and facilitating human-computer emotional interaction.
# Quick Demo
We provide a demo to run end-to-end inference on the test video. Our inference code will take a human-based video as input and generate an emotional video caption.
# After launching the docker container 
EVAL_DIR='./models/table1/MAFW/best-checkpoint/'
CHECKPOINT='./models/table1/MAFW/best-checkpoint/model.bin'
VIDEO='./docs/G0mjFqytJt4_000152_000162.mp4'
CUDA_VISIBLE_DEVICES=0 python src/tasks/run_caption_VidSwinBert_inference.py \
       --resume_checkpoint $CHECKPOINT  \
       --eval_model_dir $EVAL_DIR \
       --test_video_fname $VIDEO \
       --do_lower_case \
       --do_test 
 
 

 [![Watch the video](https://img.youtube.com/vi/dQw4w9WgXcQ/0.jpg)](https://www.youtube.com/watch?v=dQw4w9WgXcQ)

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Video Embed</title>
</head>
<body>
    <div>
        <h3>Video Description</h3>
        <iframe width="640" height="360" src="https://youtu.be/AtGwEnN-5zk?si=lQX1nusmo2MWOz66" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen style="max-width: 100%; border-radius: 8px;"></iframe>
       
    </div>
</body>
</html>


