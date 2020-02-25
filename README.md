# awesome-kaldi
This is a list of features, scripts, blogs and resources for better using Kaldi (http://kaldi-asr.org/). **Please fill free to contribute by adding more links!**

## Good resources for beginners:
1. [How to start with kaldi and speech recognition](https://towardsdatascience.com/how-to-start-with-kaldi-and-speech-recognition-a9b7670ffff6) - A Medium post (by me) regarding the general structure of the Kaldi project and its different parts. **In my opinion you should start here.**
2. [Kaldi for Dummies tutorial](http://kaldi-asr.org/doc/kaldi_for_dummies.html) - The basic tutorial in the Kaldi documentation. It is really good for "hands on" experience but it is not so well explained.
3. [How to Train a Deep Neural Net Acoustic Model with Kaldi](http://jrmeyer.github.io/asr/2016/12/15/DNN-AM-Kaldi.html) - A tutorial by Josh Meyer for specifically running Kaldi with DNN
4. [Building Speech Recognition Systems with the Kaldi Toolkit](https://engineering.jhu.edu/clsp/wp-content/uploads/sites/75/2016/06/Building-Speech-Recognition-Systems-with-the-Kaldi-Toolkit.pdf) - This presentation is extremely long but also extremely helpful. Its the most complete source of information about the training process and its development.
5. [Eleanor Chodroff Kaldi Tutorial](https://www.eleanorchodroff.com/tutorial/kaldi/) - A good in depth tutorial about the training process with a lot of code examples. 
6. [Speaker Diarization with Kaldi](https://towardsdatascience.com/speaker-diarization-with-kaldi-e30301b05cc8) - A tutorial about X-Vectors and Speaker Diarization.

## Good resources for more complex stuff:
1. [Some Kaldi Notes](http://jrmeyer.github.io/asr/2016/02/01/Kaldi-notes.html) - Some advanced notes that is highly recommended to read if you want to be a more trained user.
2. [Decoding graph construction in Kaldi: A visual walkthrough](http://vpanayotov.blogspot.com/2012/06/kaldi-decoding-graph-construction.html) - If you want to understand the different parts of the Decoding graph you should probably read this. It is required to understand those concepts for debugging your graph in the development of a new model.

## Good Utils
Deep in the utils folder inside the wsj recipe there are some interesting scripts that helped me a lot during my work. Knowing all of them will probably help you a lot, here are some basic ones that you should probably start with:
1. [perturb_data_dir_speed_3way.sh](https://github.com/kaldi-asr/kaldi/blob/master/egs/wsj/s5/utils/data/perturb_data_dir_speed_3way.sh) - this script will help you to change the speaking speed of different utterances without creating excess files. It does this by implementing an SoX command to your wav file and copying and editing all the other files in your folder. Using this script and also the next one is a must-have in most state-of-the-art systems and will help your model to generalize better.
2. [perturb_data_dir_volume.sh](https://github.com/kaldi-asr/kaldi/blob/master/egs/wsj/s5/utils/data/perturb_data_dir_volume.sh) - this script will do exactly the same but will change the volume of the utterances.
3. [resample_data_dir.sh](https://github.com/kaldi-asr/kaldi/blob/master/egs/wsj/s5/utils/data/resample_data_dir.sh) - You want to make a new model for different sampling rate but you don't want to manually re-sample you entire data? this script will help you to do it, again with a SoX command.
4. [combine_data.sh](https://github.com/kaldi-asr/kaldi/blob/master/egs/wsj/s5/utils/combine_data.sh) - If you have multiple datasets and you want to combine all of the manually, there is no need to do it file after file. this script will take an entire data directory and will combine all the files into the same new directory.
5. [summarize_logs.pl](https://github.com/kaldi-asr/kaldi/blob/master/egs/wsj/s5/utils/summarize_logs.pl) & [summarize_warnings.pl](https://github.com/kaldi-asr/kaldi/blob/master/egs/wsj/s5/utils/summarize_warnings.pl) - When you run a process in Kaldi with multiple jobs, each job will have different a log file. when you are using a lot of jobs it might be hard to look at all of those logs. those scripts will help you to summarize all of the logs into one readable file.

## Good Kaldi "production ready" examples 
There are some open-source projects around that use Kaldi as a platform for building an ASR systems for real-time usage. by seeing those projects you can learn a lot about how to implement such system of you own.
1. [online2-tcp-nnet3-decode-faster](https://github.com/kaldi-asr/kaldi/blob/master/src/online2bin/online2-tcp-nnet3-decode-faster.cc) - A new excutable that was [added](https://github.com/kaldi-asr/kaldi/pull/2938) to kaldi that creates a basic TCP server that can read the model and transcribe raw audio. **If you want an easy to implement solution just to check your models easily, you should probably start here.**
2. [kaldi-gstreamer-server](https://github.com/alumae/kaldi-gstreamer-server) - this is a nice project that will help you to integrate Kaldi toolkit and the [GStreamer framework](https://gstreamer.freedesktop.org/documentation/application-development/introduction/gstreamer.html), a popular framework that will help you to make a scalable ASR server
3. [kaldi-offline-transcriber](https://github.com/alumae/kaldi-offline-transcriber) - A good example for a project that handles both training and decoding. It is being build for Estonian but can be easily transformed into any language.
4. [compile Kaldi for android](http://jcsilva.github.io/2017/03/18/compile-kaldi-android/) - You can also compile the Kaldi project in a way that will work directly on android devices. That might not be a good idea with a heavy model, but can be used to more constrained models.
5. [VBDiarization](https://github.com/Jamiroquai88/VBDiarization) - A good implementation of Speaker Diarization, it can be used with Kaldi pre-trained Xvector model.
6. [tf-kaldi-speaker](https://github.com/mycrazycracy/tf-kaldi-speaker) - A framework that combines TensorFlow and Kaldi in the context of speaker verification/identification tasks. The project has some pretrained model that were trained on huge datasets.
7. [kaldi-adapt-lm](https://github.com/gooofy/kaldi-adapt-lm) - A tool that helps to adapt nnet3 chain models to a different language model.

## Resources for understanding the math/science behind Kaldi better:
1. [Speech Recognition with Weighted Finite-State Transducers](https://cs.nyu.edu/~mohri/pub/hbka.pdf) - The "bible" for understanding WFST-based systems for Speech recognition. **This should probably be your first read.**
2. [Semirings and WFST](https://www.youtube.com/watch?v=1aEinrlyp8w&list=PLxbPHSSMPBeicXAHVfyFvGfCywRCq39Mp) - A good small course (~3 hours) from Nanyang technological university that covers the idea of WFSTs in a really straight forward and visual way.
3. [The HTK book](http://www.dsic.upv.es/docs/posgrado/20/RES/materialesDocentes/alejandroViewgraphs/htkbook.pdf) - The HTK book is for another ASR toolkit but it highlihts the basics of speech recognition in a a really intuitive and graphic way.
4. [A Bit of Progress in Language Modeling](http://www-labs.iro.umontreal.ca/~felipe/IFT6285-Automne2018/resources-2011/Articles/goodman2001.pdf) *J. Goodman, 2011* - The most basic and comprehensive article about the creation of Language-Models
5. [GMM Acoustic Modeling and Feature Extraction](https://web.stanford.edu/class/cs224s/lectures/224s.17.lec5.pdf) - A really good presentation by Andrew Maas for better understanding the GMM-based phoneme alignment.

## Important articles
1. [The Kaldi Speech Recognition Toolkit](https://homepages.inf.ed.ac.uk/aghoshal/pubs/asru11-kaldi.pdf) *D. Povey et al., 2011* - The original article that described Kaldi and the different parts of the project. It should be noted that some parts of that article are outdated.
2. [A time delay neural network architecture for efficient modeling of long
temporal contexts](https://www.danielpovey.com/files/2015_interspeech_multisplice.pdf) *V. Peddinti, D. Povey, S. Khudanpur, 2015* - The article that describes the usage of TDNNs in Kaldi
3. [Hybrid speech recognition with Deep Bidirectional LSTM](https://www.cs.toronto.edu/~graves/asru_2013.pdf) *A. Graves, N. Jaitly and A. Mohamed, 2013* - an article about the BLSTM basic recipe in Kaldi.
