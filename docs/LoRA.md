
## Demo (Web UI)
You need EarthDial-4B to run the demo locally. Download the model from [EarthDial-4B](https://huggingface.co/MBZUAI/EarthDial-4B). After loading the model, run this command by giving the model path to launch the gradio demo.
#### Launch the demo
```Shell
python earthdial_demo.py --model-path /path/to/model 
```

## Training

Please see sample training scripts for [LoRA]()

We provide sample DeepSpeed configs, [`zero3.json`](https://github.com/haotian-liu/LLaVA/blob/main/scripts/zero3.json) is more like PyTorch FSDP, and [`zero3_offload.json`](https://github.com/haotian-liu/LLaVA/blob/main/scripts/zero3_offload.json) can further save memory consumption by offloading parameters to CPU. `zero3.json` is usually faster than `zero3_offload.json` but requires more GPU memory, therefore, we recommend trying `zero3.json` first, and if you run out of GPU memory, try `zero3_offload.json`. You can also tweak the `per_device_train_batch_size` and `gradient_accumulation_steps` in the config to save memory, and just to make sure that `per_device_train_batch_size` and `gradient_accumulation_steps` remains the same.

If you are having issues with ZeRO-3 configs, and there are enough VRAM, you may try [`zero2.json`](https://github.com/haotian-liu/LLaVA/blob/main/scripts/zero2.json). This consumes slightly more memory than ZeRO-3, and behaves more similar to PyTorch FSDP, while still supporting parameter-efficient tuning.


