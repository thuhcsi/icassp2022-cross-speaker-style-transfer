
## Abstract

This paper introduces a chunk-wise multi-scale style modeling method for cross-speaker style transfer task. Multi-scale style modeling is adopted for explicit local prosody preservation during the transfer, which is absent in existing crossspeaker style models. A novel chunk-wise style module is proposed to improve the precision of speech style modeling. Switchable adversarial classifiers are designed to disentangle speaker timbre and speech style across disjoint datasets. Experiment results confirm that the model fairly transfers both local and global style to new target speaker.

## Dataset

Our cross-speaker style transfer experiments are conducted based on 3 disjoint datasets:

1. **MST-Originbeat:** A style-consistent Mandarin corpus offered by the ICASSP 2021 M2VOC challenge \[1\], with one female and one male speaker (named as `OF`, `OM`).
2. **Speaker F:** A private hybrid Mandarin dataset from another female Chinese speaker. It consists of two part (named as `F.N`, `F.S1`). The first is an utterance level neutral corpus. The second is an audio book corpus with another style.
3. **Speaker M:** A private Mandarin audio book dataset from another male Chinese speaker. Two different styles are included (named as `M.S2`, `M.S3`).

Following the common practice of cross-speaker style transfer model training on disjoint datasets \[2, 3\], a shared style category (`P`) that is established across different datasets, as shown in the table below. 
Consequently, the cross-speaker style transfer model is assigned
with 6 subtasks: to transfer target style T1 to speaker OF, OM,
M; and T2 to speaker OF, OM, F.

| Dataset | Speaker label | Style label |
|:--------|:--------------|:------------|
| OF   | OF | P  |
| OM   | OM | P  |
| F.N  |  F | P  |
| F.S1 |  F | T1 |
| M.S2  |  M | P  |
| M.S3 |  M | T2 |


## Cross-speaker style transfer results

To demonstrate the functionality of the proposed chunk-wise global style ensemble and switchable adversarial classifiers:

-  On the one hand, removes the chunk-wise style modeling mechanism (`Proposed w/o chunk`)
- On the other hand, replaces the switchable adversarial classifiers with one single adversarial classifier on each branch. (`Proposed w/o switchbox`)

The cross-speaker style transfer results of these baseline models and the proposed model are all provided here for comparison.
An ideal cross-speaker style transfer result is supposed to match the timbre of with the given speaker, while preserving both local prosody and global style of the reference speech.


### Task1: Transfer target style `T1` to speaker `M`

**A sample audio from speaker `M`**, to show the feature of the speaker's timbre:

<audio controls><source src="./static/some.wav" type="audio/wav">Your browser does not support the audio element.</audio>

**Style Transfer results:**

| Reference (with style `T1`)| `Proposed` | `Proposed w/o chunk` | `Proposed w/o switchbox` |
|:------------|:------------|:------------|:------------|
|<audio controls><source src="./static/some.wav" type="audio/wav">Your browser does not support the audio element.</audio>|<audio controls><source src="./static/some.wav" type="audio/wav">Your browser does not support the audio element.</audio>|<audio controls><source src="./static/some.wav" type="audio/wav">Your browser does not support the audio element.</audio>|<audio controls><source src="./static/some.wav" type="audio/wav">Your browser does not support the audio element.</audio>|

### Task2: Transfer target style `T1` to speaker `OM`

### Task3: Transfer target style `T1` to speaker `OF`

### Task4: Transfer target style `T2` to speaker `F`

### Task5: Transfer target style `T2` to speaker `OF`

### Task6: Transfer target style `T2` to speaker `OM`


## References

1. Qicong Xie, Xiaohai Tian, Guanghou Liu, Kun Song, Lei Xie, Zhiyong Wu, Hai Li, Song Shi, Haizhou Li, Fen Hong, Hui Bu, and Xin Xu, “The multi-speaker multi-style voice cloning challenge 2021,” in ICASSP 2021 - 2021 IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP), 2021, pp.8613–8617.
2. Matt Whitehill, Shuang Ma, Daniel McDuff, and Yale Song, “Multi-reference neural TTS stylization with adversarial cycle consistency,” in Proc. Interspeech 2020, 2020, pp. 4442–4446.
3. Tao Li, Xinsheng Wang, Qicong Xie, Zhichao Wang, and Lei Xie, “Controllable cross-speaker emotion transfer for end-to-end speech synthesis,” arXiv preprint arXiv:2109.06733, 2021.