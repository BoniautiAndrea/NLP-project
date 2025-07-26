# NLP-project
A reimplementation of the paper "Translate to Disambiguate: Zero-shot Multilingual Word Sense Disambiguation with Pretrained Language Models" with some difference and corrections.

This paper is the reimplementation of 'Translate to Disambiguate: Zero-shot Multilingual Word Sense Disambiguation with Pretrained Language Models' from https://arxiv.org/pdf/2304.13803.pdf with some improvements, more details can be found in the Report delivered with this notebook.

All cells before Dataset Run are required to run if the user wants to use the Dataset run (it may take around 30/40 minutes if using bloom-3b)

For the the Example run, the Data Loading section can be skipped, but as explained in the specific section, it uses BabelNet so it is incompatible with Colab, you will need to download the notebook and its Google Drive folder (or just create an examples/ folder in the same place). Also be sure to have a BabelNet API key, if not, one comes with the folder.

This project is delivered with original samples data (in data/ folder) and with already sampled data (in samples/ folder), the code automatically check if already sampled data exists and if not it loads original data and samples it.

If you want to try the sampling procedure just empty the /samples folder in the Google Drive repository.

The Dataset run is based on some XL-WSD files and on the 'best-ensemble settings' as said in the paper, in which the language of the prompt is in English and the target languages (the ones in which the words are translated) are English, Russian and Chinese. If one of the target languages is selected as source language, it will just not be translated in the same one.

To try the code with a new {new_lang}, you will need to: Download from https://github.com/mk322/contextual-word-level-translation the following files:

test-{new_lang}.data.xml and test-{new_lang}.gold.key.txt from xl-wsd-data/evaluation_datasets/test-{new_lang}
correct_trans_{new_lang}{tlang}.json, wrong_trans{new_lang}{tlang}.json and all_sense_labels{new_lang}_{tlang}.txt from xl-wsd-files/{new_lang}/, where {tlang} is 'en', 'ru' and 'zh'. Add these files to data/ folder and write as parameter of wsd_on_dataset() function the iso of the new language (es. 'es' for spanish)
These files were created by paper authors, they allow the run without using BabelNet, incompatible with Colab environment.
