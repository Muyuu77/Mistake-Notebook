# Mistake Notebook

### Machine Translation Model
* Create Attention Mask in Pytorch Transformer: There should not be **a whole line for "True" in src_mask or "True" be in front of "False" in src_key_padding_mask**.
Otherwise, Nan value will be raised.
* Create Word2idx Dict: Training data and testing data should share the same Dict from training data.
* NMT Loss function should ignore (index == padding).
* PyTorch -> Float32


### General Pytorch
* The loss module nn.CrossEntropyLoss in PyTorch performs two operations: nn.LogSoftmax and nn.NLLLoss. Hence, the input to this loss module should be the output of your last linear layer. **Do not apply a softmax before the Cross-Entropy loss**. Otherwise, PyTorch will apply a log-softmax on your softmax outputs, which will significantly worsen the performance, and give you headaches. If you use the loss module nn.NLLLoss, you need to apply the log-softmax yourself. NLLLoss requires log-probabilities, not plain probabilities. Hence, make sure to apply nn.LogSoftmax or nn.functional.log_softmax, and not nn.Softmax.
