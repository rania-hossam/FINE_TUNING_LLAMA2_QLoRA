# FINE_TUNING_LLAMA2_QLoRA
fine-tune a Llama 2 model with 7 billion parameters on a T4 GPU with high RAM using Google Colab (2.21 credits/hour). Note that a T4 only has 16 GB of VRAM, which is barely enough to store Llama 2–7b’s weights (7b × 2 bytes = 14 GB in FP16). In addition, we need to consider the overhead due to optimizer states, gradients, and forward activations . This means that a full fine-tuning is not possible here: we need parameter-efficient fine-tuning (PEFT) techniques like LoRA or QLoRA.
we will use QloRA:
While LORA helps in reducing the storage requirements, you would still need a large GPU to load the model into the memory for LoRa training. This is where QLORA, or Quantized LORA, comes into the picture. QLORA is a combination of LORA and Quantization.

Currently, we store the weight para- meters in FP32. What does it mean? Each element in the matrix is stored in 32 bits. What if we can store the same information in 8 bits? 4 bits? Before I throw some math at you, let me give you a brief overview of QLoRa.

QLORA: Here, you first quantize the LLM and then perform LoRa training. That's it.

