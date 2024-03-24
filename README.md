# Mistake Notebook

### Machine Translation Model
* Create Attention Mask in Pytorch Transformer: There should not be **a whole line for "True" in src_mask or "True" be in front of "False" in src_key_padding_mask**.
Otherwise, Nan value will be raised.
* Create Word2idx Dict: Training data and testing data should share the same Dict from training data.
* NMT Loss function should ignore (index == padding).
* PyTorch -> Float32
