Microsoft COCO Caption Evaluation
===================

Evaluation codes for MS COCO caption generation, modified for running on Python 3

The code is tested with Python 3.6 and Python 2.7, and it seems that it is compatible with both Python 3.6 and Python 2.7.

- Some method calls are modified (such as .iteritems() method of defaultdict is changed to .items(), xrange() method is changed to range() ).
- Temporary file writing is modified, contents of temporary files are encoded in utf-8.
- Inter-process communications between main process and sub process is modified, it seems that subprocess.Popen of Python 2 and Python 3 behaves differently.
- The '-cache' option in SPICE command is removed (because I didn't solve the cache problem)

TODO: There are 3 different versions of Stanford CoreNLP jars used (PTBTokenizer uses stanford-corenlp-3.4.1.jar, spice uses stanford-corenlp-3.6.0.jar, Chinese tokenizer uses stanford-segmenter-3.9.1.jar) considering using one version

* When evaluating Chinese sentences, SPICE metric is inappropriate.

## Requirements ##
- java 1.8.0
- python 2.7 / python 3.6

## Files ##
./
- cocoEvalCapDemo.py (demo script)

./annotation
- captions_val2014.json (MS COCO 2014 caption validation set)
- Visit MS COCO [download](http://mscoco.org/dataset/#download) page for more details.

./results
- captions_val2014_fakecap_results.json (an example of fake results for running demo)
- Visit MS COCO [format](http://mscoco.org/dataset/#format) page for more details.

./pycocoevalcap: The folder where all evaluation codes are stored.
- evals.py: The file includes COCOEavlCap class that can be used to evaluate results on COCO.
- tokenizer: Python wrapper of Stanford CoreNLP PTBTokenizer
- bleu: Bleu evalutation codes
- meteor: Meteor evaluation codes
- rouge: Rouge-L evaluation codes
- cider: CIDEr evaluation codes
- spice: SPICE evaluation codes

## Setup ##

- You will first need to download the [Stanford CoreNLP 3.6.0](http://stanfordnlp.github.io/CoreNLP/index.html) code and models for use by SPICE. To do this, run:
    ./get_stanford_models.sh
- Note: SPICE will try to create a cache of parsed sentences in ./pycocoevalcap/spice/cache/. This dramatically speeds up repeated evaluations. The cache directory can be moved by setting 'CACHE_DIR' in ./pycocoevalcap/spice. In the same file, caching can be turned off by removing the '-cache' argument to 'spice_cmd'. 

## References ##

- [Microsoft COCO Captions: Data Collection and Evaluation Server](http://arxiv.org/abs/1504.00325)
- PTBTokenizer: We use the [Stanford Tokenizer](http://nlp.stanford.edu/software/tokenizer.shtml) which is included in [Stanford CoreNLP 3.4.1](http://nlp.stanford.edu/software/corenlp.shtml).
- BLEU: [BLEU: a Method for Automatic Evaluation of Machine Translation](http://www.aclweb.org/anthology/P02-1040.pdf)
- Meteor: [Project page](http://www.cs.cmu.edu/~alavie/METEOR/) with related publications. We use the latest version (1.5) of the [Code](https://github.com/mjdenkowski/meteor). Changes have been made to the source code to properly aggreate the statistics for the entire corpus.
- Rouge-L: [ROUGE: A Package for Automatic Evaluation of Summaries](http://anthology.aclweb.org/W/W04/W04-1013.pdf)
- CIDEr: [CIDEr: Consensus-based Image Description Evaluation](http://arxiv.org/pdf/1411.5726.pdf)
- SPICE: [SPICE: Semantic Propositional Image Caption Evaluation](https://arxiv.org/abs/1607.08822)

## Developers ##
- Xinlei Chen (CMU)
- Hao Fang (University of Washington)
- Tsung-Yi Lin (Cornell)
- Ramakrishna Vedantam (Virgina Tech)

## Acknowledgement ##
- David Chiang (University of Norte Dame)
- Michael Denkowski (CMU)
- Alexander Rush (Harvard University)