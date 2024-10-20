# WIMU-Data-poisoning
## Description
Project developed as an approach to data poisoning for music generative models using musically-aware adversarial attacks.
## Design proposal
### Schedule
| **Week** | **TO-DO** |
|:-:|:-:|
|Week 1 (02.10 - 08.10)|  - |
|Week 2 (09.10 - 15.10)|  Nighshade/Glaze research|
|Week 3 (16.10 - 22.10)|  Watermarking research/design |proposal submission |
|Week 4 (23.10 - 29.10)| Preparing environment |
|Week 5 (30.10 - 05.11)| Generating and detecting watermarking in music generative models **(*)** |
|Week 6 (06.11 - 12.11)| Preparing dataset for simple "dirty-label" attack and analyzing results |
|Week 7 (13.11 - 19.11)| Preparing detailed attack design |
|Week 8 (20.11 - 26.11)| Selecting poison text prompts (pt. I) |
|Week 9 (27.11 - 03.12)| Selecting poison text prompts (pt. II) |
|Week 10 (04.12 - 10.12)| Generating audio files based on selected text prompts |
|Week 11 (11.12 - 17.12) |Constructing poison audio files (pt. I) |
|Week 12 (18.12 - 24.12) |Constructing poison audio files (pt. II) |
|Week 13 (25.12 - 31.12) |Constructing poison audio files (pt. III) |
|Week 14 (01.01 - 07.01) |Fine-tuning models on prepared poison dataset |
|Week 15 (08.01 - 14.01) |Testing and evaluation |
|Week 16 (15.01 - 21.01) |Project submission |
|Week 17 (22.01 - 28.01) |- |

**(*)** It means, If watermarking the data and verifying whether generative models like VampNet, MusicGen, or SampleRNN reproduce the watermark proves to be straightforward, we will proceed with implementing Nightshade for audio. However, if watermarking turns out to be more complex, we will change our schedule to solve the watermarking issue.

### Approach and planned experiments
Based on our research, we plan to focus on fine-tuning pre-trained text-to-audio models (we are also considering text-to-speech models) rather than training a model from scratch on large datasets. The main reason for this is the extended time required for training from scratch, along with the need for sophisticated graphics cards. We believe our approach is reasonable, and closer to real-world conditions, as suggested in the Nightshade paper.

If we proceed with reproducing Nightshade for audio, Our first step will be to empirically validate the effectiveness of a "dirty-label" poisoning attack on music generative models that we have identified. To measure the success of the attack, we will use two metrics: a CLAP-based similarity score and human inspection.

Following this, we will attempt to reproduce the Nightshade attack, adapting the three steps presented in the original paper by replacing image-specific elements with their audio equivalents. As with the "dirty-label" attack, we will validate our results using the two metrics mentioned above.

Once we have the outcomes for both attacks, we plan to compare their effectiveness, as well as the number of poisoned samples required for each.

### Functionality
Our main goal is to reproduce a similar attack to Nightshade, but for music generative models. We aim to test the effectiveness of this approach, which theoretically should outperform the simpler "dirty-label" attack. Additionally, we plan to develop a specific CLI tool to automate the process of generating poisoned samples for selected music genres and fine-tuning the target model.

### Models
| **Model** | **Author** | **Module**  | **Type**  | **Fine-tuning**  |
|:-:|:-:|:-:|:-:|:-:|
| MusicGen  | Facebook  | transformers  | TTA  | Yes, via: [MusicGen dreamboothing](https://github.com/ylacombe/musicgen-dreamboothing)|
|  AudioSeal | Meta   | audioseal   | ATA | Yes, via: [AudioSeal](https://github.com/facebookresearch/audioseal/blob/main/docs/TRAINING.md)   | 
|  VampNet | Hugo Flores García and Prem Seetharaman  | Directly from: [VampNet](https://github.com/hugofloresgarcia/vampnet)   | ATA   | Yes, via: [VampNet](https://github.com/hugofloresgarcia/vampnet)     |
|  SampleRNN | Soroush Mehri  | Directly from: [SampleRNN](https://github.com/soroushmehr/sampleRNN_ICLR2017/tree/master)  | ATA | Yes, via: [SampleRNN](https://github.com/soroushmehr/sampleRNN_ICLR2017/tree/master)   |
|  CLAP | LAION-AI  | transformers  | multimodal  | Yes, via: [CLAP](https://github.com/LAION-AI/CLAP)   | 

### Bibliography
- AudioSeal: https://arxiv.org/abs/2401.17264v2 / https://github.com/facebookresearch/audioseal/tree/main
- VampNet: https://arxiv.org/abs/2307.04686 / https://github.com/hugofloresgarcia/vampnet
- MusicGen: https://arxiv.org/abs/2306.05284 / https://github.com/facebookresearch/audiocraft/blob/main/docs/MUSICGEN.md
- SampleRNN: https://arxiv.org/abs/1612.07837 / https://github.com/soroushmehr/sampleRNN_ICLR2017/tree/master
- Nightshade: https://arxiv.org/pdf/2310.13828
- Glaze: https://www.usenix.org/system/files/usenixsecurity23-shan.pdf
