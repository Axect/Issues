# PyTorch

## undefined symbol: [SOME_LONG_MESSAGE] version libcudnn_cnn_infer.so.8

- **Reason**: The PyTorch binaries ship with their own CUDA dependencies (including cuDNN), but if you installed cuDNN locally then it causes error.

- **Solution**: Remove local `cudnn` (i.e. `paru -R cudnn`)

- **Reference**: - [Could not load library libcudnn_cnn_train.so.8](https://discuss.pytorch.org/t/could-not-load-library-libcudnn-cnn-train-so-8-but-im-sure-that-i-have-set-the-right-ld-library-path/190277)
