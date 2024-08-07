# Mistake Notebook

### Machine Translation Model
* Create Attention Mask in Pytorch Transformer: There should not be **a whole line for "True" in src_mask or "True" be in front of "False" in src_key_padding_mask**.
Otherwise, Nan value will be raised.
* Create Word2idx Dict: Training data and testing data should share the same Dict from training data.
* NMT Loss function should ignore (index == padding).
* PyTorch -> Float32
* Time dimension in nn.LSTM: By default, PyTorch’s **nn.LSTM module assumes the input to be sorted as [seq_len, batch_size, input_size]**. Make sure that you do not confuse the sequence length and batch dimension. The **LSTM would still run without an error, but will give you wrong results**. If you want to change this behavior to accepting an input shape of [batch_size, seq_len, input_size], you can specify the argument batch_first=True when creating the LSTM object.


### General Pytorch
* The loss module nn.CrossEntropyLoss in PyTorch performs two operations: nn.LogSoftmax and nn.NLLLoss. Hence, the input to this loss module should be the output of your last linear layer. **Do not apply a softmax before the Cross-Entropy loss**. Otherwise, PyTorch will apply a log-softmax on your softmax outputs, which will significantly worsen the performance, and give you headaches. If you use the loss module nn.NLLLoss, you need to apply the log-softmax yourself. NLLLoss requires log-probabilities, not plain probabilities. Hence, make sure to apply nn.LogSoftmax or nn.functional.log_softmax, and not nn.Softmax.


### Fine-tuning LLMs
* QLoRA -> adds trainable weights to all the linear layers in the transformer architecture
* BitsAndBytesConfig -> 控制训练时模型参数储存精度和计算精度，load_in_4bit=True -> 牺牲一定的储存精度来显著减少LLM训练内存占用
