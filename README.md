---
language:
- en
- de
- fr
- it
- pt
- hi
- es
- th
library_name: transformers
pipeline_tag: text-generation
tags:
- facebook
- meta
- pytorch
- llama
- llama-3
---

This repository is an early access checkpoint for Llama 3.2 3B Instruct.

This repo contains two versions of the model, for use with `transformers` and with the original `llama3` codebase (under the `original` directory).

### Use with transformers

Here is an example of simple usage with `transformers`

```python
from transformers import pipeline
import torch

model_id = "nltpt/Llama-3.2-3B-Instruct"

pipe = pipeline(
    "text-generation",
    model=model_id,
    model_kwargs={"torch_dtype": torch.bfloat16},
    device_map="auto"
)

messages = [
    {"role": "user", "content": "What is the capital of France?"},
]
pipe(messages, max_length=50)
```

### Use with `llama3`

Please follow the instructions provided for that repository. To download the checkpoints from the Hub, see this example command using `huggingface-cli`:

```bash
huggingface-cli download nltpt/Llama-3.2-3B-Instruct --include "original/*" --local-dir Llama-3.2-3B-Instruct
```
