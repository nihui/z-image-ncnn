# Z-Image ncnn

:exclamation: :exclamation: :exclamation: This software is in the early development stage, it may bite your cat

ncnn implementation of Z-Image image generater.

z-image-ncnn uses [ncnn project](https://github.com/Tencent/ncnn) as the universal neural network inference framework.

## About Z-Image

Z-Image: An Efficient Image Generation Foundation Model with Single-Stream Diffusion Transformer

https://github.com/Tongyi-MAI/Z-Image

## Usages

Currently, this program requires a Vulkan capable graphics card with at least 16GB of VRAM to run.

This program requires code from the ncnn git master branch to achieve correct results and optimal performance.

Further performance and video memory usage optimizations are underway. Please stay tuned :)

### prepare model files

https://huggingface.co/nihui-szyl/z-image-ncnn/tree/main/z-image-turbo

```shell
$ hf download nihui-szyl/z-image-ncnn --local-dir ./models

$ ls -lh  models/z-image-turbo/
total 19G
-rw-r--r-- 1 user sudo 1.6M Jan 22 11:37 merges.txt
-rw-r--r-- 1 user sudo 1.5M Jan 22 11:37 vocab.txt
-rw-r--r-- 1 user sudo 7.4G Jan 22 12:43 z_image_turbo_text_encoder.ncnn.bin
-rw-r--r-- 1 user sudo 102K Jan 22 11:37 z_image_turbo_text_encoder.ncnn.param
-rw-r--r-- 1 user sudo 2.4M Jan 22 11:37 z_image_turbo_transformer_all_final_layer.ncnn.bin
-rw-r--r-- 1 user sudo  612 Jan 22 11:37 z_image_turbo_transformer_all_final_layer.ncnn.param
-rw-r--r-- 1 user sudo 488K Jan 22 11:37 z_image_turbo_transformer_all_x_embedder.ncnn.bin
-rw-r--r-- 1 user sudo  174 Jan 22 11:37 z_image_turbo_transformer_all_x_embedder.ncnn.param
-rw-r--r-- 1 user sudo  19M Jan 22 11:38 z_image_turbo_transformer_cap_embedder.ncnn.bin
-rw-r--r-- 1 user sudo  260 Jan 22 11:37 z_image_turbo_transformer_cap_embedder.ncnn.param
-rw-r--r-- 1 user sudo 676M Jan 22 11:45 z_image_turbo_transformer_context_refiner.ncnn.bin
-rw-r--r-- 1 user sudo 5.3K Jan 22 11:37 z_image_turbo_transformer_context_refiner.ncnn.param
-rw-r--r-- 1 user sudo 691M Jan 22 11:46 z_image_turbo_transformer_noise_refiner.ncnn.bin
-rw-r--r-- 1 user sudo 6.9K Jan 22 11:37 z_image_turbo_transformer_noise_refiner.ncnn.param
-rw-r--r-- 1 user sudo 1.1M Jan 22 11:37 z_image_turbo_transformer_t_embedder.ncnn.bin
-rw-r--r-- 1 user sudo  714 Jan 22 11:37 z_image_turbo_transformer_t_embedder.ncnn.param
-rw-r--r-- 1 user sudo  11G Jan 22 12:41 z_image_turbo_transformer_unified.ncnn.bin
-rw-r--r-- 1 user sudo 101K Jan 22 11:37 z_image_turbo_transformer_unified.ncnn.param
-rw-r--r-- 1 user sudo  95M Jan 22 11:38 z_image_turbo_vae.ncnn.bin
-rw-r--r-- 1 user sudo  11K Jan 22 11:37 z_image_turbo_vae.ncnn.param
```

## Build from Source

```shell
git clone https://github.com/nihui/z-image-ncnn.git
cd z-image-ncnn
git submodule update --init --recursive
mkdir build
cd build
cmake -DNCNN_VULKAN=ON ../src
make -j8
```

## Sample Images

```shell
$ ./z-image-ncnn ../models/z-image-turbo/ "風的彷徨.美少女.半身照."
```

```
prompt="風的彷徨."
size=1024x1024
steps=9
seed=77
```

![zimage](images/77.jpg)

```
prompt="風的彷徨."
size=1024x1024
steps=9
seed=777
```

![zimage](images/777.jpg)

## Original Z-Image Project

- https://github.com/Tongyi-MAI/Z-Image

## Other Open-Source Code Used

- https://github.com/Tencent/ncnn for fast neural network inference on ALL PLATFORMS
- https://github.com/futz12/ncnn_llm for BPE tokenizer
