# headline-generation
Experiments of headline generation on the CNN Gigaword set. The models are based on TensorFlow's tutorial on machine translation: https://github.com/tensorflow/tensorflow/blob/r1.11/tensorflow/contrib/eager/python/examples/nmt_with_attention/nmt_with_attention.ipynb

The following table shows the experiment results. The experiments with batch size = 256 used Google colab with GPU, whereas the experiments with batch size = 64 and smaller use a local machine with GPU GeForce GTX 660 Ti.

| Attention | Embeddings initialisation | Trainable embeddings | Batch size | Epochs | val_loss |
| --------- | ------------------------- | -------------------- | ---------: | -----: | -------: |
| Yes       | Random                    | Yes                  | 64         | (9)    | (2.42)   |
| Yes       | Random                    | Yes                  | 64         | 9      | 2.47     |
| Yes       | Random                    | Yes                  | 256        | (20)   | (2.51)   |
| Yes       | Random                    | Yes                  | 256        | 16     | 2.52     |
| Yes       | Glove                     | No                   | 64         | 20     | 2.52     |
| Yes       | Glove                     | No                   | 256        | 20     | 2.67     |       
| Yes       | Glove                     | Yes                  | 64         | (7)    | (2.36)   |
| Yes       | Glove                     | Yes                  | 64         | 8      | **2.41** |
| Yes       | Glove                     | Yes                  | 256        | 16     | 2.52     |
| Yes       | Random                    | No                   | 256        | 20     | 2.66     |
| Yes       | Random                    | No                   | 64         | 18     | 2.51     |
| Yes       | Glove                     | Yes                  | 32         | 6      | 2.36     |
| Yes       | Glove                     | Yes                  | 16         | 4      | **2.29**

With batch size = 256:

| [Batch size = 256] | Random | Glove |
| ------------------ | -----: | ----: |
| **Trainable**      | 2.52   | 2.52  |
| **Not trainable**  | 2.66   | 2.67  |

| [Batch size = 64] | Random | Glove |
| ----------------- | -----: | ----: |
| **Trainable**     | 2.42   | 2.41  |
| **Not trainable** | 2.51   | 2.52  |

The experiments suggest that using pre-trained Glove embeddings do not help. Also, it seems that a smaller batch size gives better results.
