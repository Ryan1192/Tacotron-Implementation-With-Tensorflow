# Tacotron-Implementation-With-Tensorflow

An implementation of Tacotron (Text-to-Speech) using Tensorflow 2.0.0, significantly influenced by the following works:

General algorithmic structure: [https://github.com/Kyubyong/tacotron](https://github.com/Kyubyong/tacotron)
Korean language training: [https://github.com/hccho2/Tacotron2-Wavenet-Korean-TTS](https://github.com/hccho2/Tacotron2-Wavenet-Korean-TTS)
Attention mechanism: [https://www.tensorflow.org/tutorials/text/nmt_with_attention](https://www.tensorflow.org/tutorials/text/nmt_with_attention)
Please note that I have avoided using the `tensorflow_addon` library as it does not appear to be fully compatible with Tensorflow versions >= 2.0.0.
Additionally, I've included an option to select between standard and monotonic attention, because monotonic attention demonstrates quicker convergence for both languages.

## Prerequisites

- Python=3.7
- tensorflow-gpu >= 2.0.0
- librosa
- tqdm
- matplotlib
- jamo
- unidecode
- inflect

## Datasets

For English, the LJSpeech 1.1 dataset was utilized ([https://keithito.com/LJ-Speech-Dataset/](https://keithito.com/LJ-Speech-Dataset/)).
For Korean, the KSS dataset was employed ([https://www.kaggle.com/bryanpark/korean-single-speaker-speech-dataset](https://www.kaggle.com/bryanpark/korean-single-speaker-speech-dataset)).

## Training Process

First, configure your parameters (including directories, language settings, etc.) in `hyperparams.py`. For generating sample outputs, I have set the "use_monotonic" and "normalize_attention" parameters to `True`.
Then, you can initiate the training by running the `training.py` file as shown below:

```bash
python training.py
```

## Outcomes

To demonstrate some sample results, I trained the model with both English and Korean datasets, applying Bahdanau monotonic attention with normalization.
Outcomes from training with English data (LJSpeech) are presented below:

Outcomes from training with Korean data (KSS) are presented below:
Both models were trained for approximately 15 hours.

## Sample Generation

Initially, set your parameters within `hyperparams.py`. Note that you must set the "use_monotonic" and "normalize_attention" parameters to `True` if the model was trained in that configuration. Then, utilize the "synthesizing" function to generate the desired sentence. <br>

synthesizing("The boy was there when the sun rose", hp)
synthesizing(hp)

Finally, execute `synthesizing.py` using a console command:

```bash
python synthesizing.py
```

For audio examples, I have uploaded a synthesized English sentence, "The boy was there when the sun rose," and a Korean sentence, into a folder named "sample_synthesis". The model was trained for 77,000 steps for English (around 40 hours) and 67,000 steps for Korean (around 15 hours).

## Additional Remarks

- Although I endeavored to convert Kyubyoung's Tensorflow 1.12 code to Tensorflow 2.0 code as accurately as possible, some discrepancies might exist between my version and Kyubyoung's. I would appreciate it if you notice any differences and inform me. Also, since I directly implemented Kyubyoung's code, any deviations from the original paper present in that code are also reflected here.
- As mentioned previously, training the Korean dataset requires considerably less time than training the English dataset. Consequently, if you understand both languages, you might find that the Korean synthesized results sound superior to the English ones. The English results would likely improve with additional training time.
- Any suggestions for improving the code or questions are welcome, though it may take some time for me to provide a response.
