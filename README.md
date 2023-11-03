# character_meme_generator
> To create your own character image using **DreamBooth** and **Inpaint Anything**
- This repository has not been cleaned up yet
## Overview

We can create a total of 6 characters :
`Gromit`, `Pingu`, `Zzangu`, `Loopy` , `Kuromi`, and `Elmo`.


## Dataset
ormally, 5 to 10 images are enough, but due to the characters' less distinct features, we prepared 30 to 45 images to generate high-quality images.
| **Character**| **Number** |
| ------------ | ------ | 
| Gromit       | 19     |
| Pingu        | 45     | 
| Zzangu       | 39     |
| Loopy        | 37     |
| Kuromi       | 30     |
| Elmo         | 40     |




## Training
### DreamBooth with LoRA
This has trained the model with default settings, including 512x512 resolution, 8GB GPU memory occupied, 1 image per batch, a learning rate of 1e-4, and the training step is set to the value obtained by multiplying the number of training images by 200.

First, Initialize 🤗Accelerate environment with:
 ```
  accelerate config
 ```
 It is developed by Hugging Face.

 Then, Run the training script. 

 ```bash
accelerate launch train_dreambooth_lora.py \
--pretrained_model_name_or_path="runwayml/stable-diffusion-v1-5" \
--instance_data_dir="images/zzangu" \
--instance_prompt="A wkdrn zzangu" \
--validation_prompt="A wkdrn zzangu standing" \
--resolution=512 \
--train_batch_size=1 \
--gradient_accumulation_steps=1 \
--learning_rate=1e-4 \
--lr_scheduler="constant" \
--lr_warmup_steps=0 \
--max_train_steps=400 \
--validation_epochs=50 \
--seed="0" \
--push_to_hub
```

## Inference
