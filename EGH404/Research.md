**EER - Application of Deep Learning to RF Spectrum Sensing**
problem - poor performance of deep learning-based spectrum sensing models in different environments and low SNR
	- Narrowed to just environments, low SNR is contained in the problem domain

## Search Query
"transfer learning" AND ( "domain adaptation" OR "multi-task learning" OR "self-supervised learning" OR "Multi-Task Learning" OR "Adversarial Transfer Learning" ) AND ( "spectrum sensing" OR "cognitive radio" ) AND ( "Cross Domain" OR "unseen" OR "environments" ) AND ( "CNN" OR "convolutional neural network" ) AND PUBYEAR > 2020 AND PUBYEAR < 2026


Improving the performance of deep learning-based Spectrum Sensing models in low SNR environments

Enhancing Deep Learning-Based Spectrum Sensing in Low Signal-to-Noise Ratio (SNR) Environments by utilising Transfer Learning to increase model robustness

## 1 Subtopics
Low SNR Spectrum sensing performance
How transfer learning can make models more robust to noise -Noise included in the challenges of new environments, approach to solving not unique

Improving the performance of models in new environments using transfer learning
- Transfer learning used


## Challenges
- Transfer Learning only useful in similar environments, detrimental in dissimilar environments
	- how can you tell if an environment is similar if theres a lack of labelled data

## Research Question
### 1.1 Potential Alterations
- Enhancing Deep Learning-Based Spectrum Sensing in Low Signal-to-Noise Ratio (SNR) Environments by utilising Transfer Learning to increase model robustness
	- Question: How does Transfer Learning improve the robustness of Deep Learning-based spectrum sensing models in low SNR environments

How can Transfer Learning be used to improve the robustness and performance of Deep Learning-based Spectrum Sensing in terms of its adaptability to differing environments or low SNR

How can Transfer Learning be used to improve the robustness and adap

### Industry Report
https://www.acma.gov.au/sites/default/files/2024-04/Draft%20FYSO%202024-29.pdf
We anticipate that growing need for data will drive spectrum demand for 5G uses.
Reviewing arrangements for access to bands already licensed for WBB is important to
ensure existing allocations are efficient and can cater for new technology
developments, such as 5G. This has to be balanced with the need to manage
interference with other licensed services. Our work program includes projects that
consider optimising existing planning frameworks and have resulted in mobile network
operators deploying 5G (or being in the process of) in existing spectrum holdings

#### 1.1.1 Could Split it up
**How can Transfer Learning be used to improve the robustness of Deep learning-based Spectrum Sensing in terms of its adaptability to differing environments and low SNR.**

reviewed?: How can Transfer Learning improve the robustness of Deep Learning-based Spectrum Sensing in terms of its adaptability when introduced to new environments or low SNR

**Review with info of other TF techniques**
**How can Transfer Learning be used to improve the robustness of Deep Learning-based Spectrum sensing to new environments by reducing the reliance on target domain data**
- "by reducing the reliance on target domain data" - answers question?? rephrase
- Further refined:
	- How can Transfer Learning improve the robustness of Deep Learning-based Spectrum Sensing in new environments while reducing the reliance on target domain data.
How can Transfer Learning be leveraged to improve the adaptability of Deep Learning-based Spectrum Sensing to unseen environments with limited labeled data?

How can Transfer Learning improve the adaptability of Convolutional Neural Network-based Spectrum Sensing to unseen environments with limited labeled data

How can Transfer Learning be used to reduce the reliance of Neural Network-based Spectrum Sensing on labelled data in unseen environments.

### Research Question
How can Transfer Learning improve the adaptability of Neural Network-based Spectrum Sensing to unseen environments with limited labeled data?

### Papers
1. Spectrum sensing based on deep learning classification for cognitive radios
2. Robust Deep Sensing through Transfer Learning in Cognitive Radio
3. A Deep convolutional neural network based transfer learning method for non-cooperative spectrum sensing
4. Spectrum-Agile Cognitive Radios Using Multi-Task Transfer Deep Reinforcement Learning -
5. Spectrum sensing based on adversarial transfer learning
6. TFF-aDCNN: A Pre-Trained Base Model for Intelligent Wideband Spectrum Sensing
7. Spectrum Sensing in Cognitive Radio Using CNN-RNN and Transfer Learning
8. Limited Data Spectrum Sensing Based on Semi-Supervised Deep Neural Network
9. SDR implementation of a light deep learning model based CNN for joint spectrum sensing and AMC


### Gaps And Callenges
 Few papers explore lightweight or real-time-compatible adaptation techniques suitable for edge devices.
More work is needed on robust self-training frameworks and confidence-based filtering of pseudo-labels.

Limitations:
limited labeled data shows good adaptability when the source model shares similarities to the target domain, limited applicability elsewhere and shifts onus of data requirement onto source model. Not too useful but good for local adaptation
Unseen training with no data seems promising by harvesting large amounts of target domain data, but latency is a concern that is unexplored
SNR generalisation seems solid and well suited to transfer learning

No other model had analysis done on it when moving from differing SNR ranges than what it was trained on

### TL
There are three different general approaches for
transfer learning, i.e., inductive, transductive, and unsuper-
vised [33]. In the inductive approach, the source and target
domains are the same, yet the source and target tasks differ
from each other. In the transductive case, the source and target
tasks are identical, but the corresponding domains are differ-
ent. In addition, the source domain has many labeled data,
while the target domain has none. Finally, in the unsupervised
approach, the source and target domains are similar, but the
tasks are different, with emphasis on unsupervised tasks in
the target domain. Deep learning models are representative
of inductive learning, where the algorithm works with a set
of assumptions related to the distribution of the training data,
known as inductive bias. Since inductive transfer techniques
utilize the inductive biases of the source task to assist the
target task, we apply transfer learning using this approach.

### 1.2 Cognitive Radio Networks
Cognitive radio (CR) is a form of wireless communication in which a transceiver can intelligently detect which communication channels are in use and which ones are not. The transceiver then instantly moves into vacant channels, while avoiding occupied ones. These capabilities help optimize the use of the available radio frequency (RF) spectrum.
It also minimizes interference to other users. And, by avoiding occupied channels, it increases spectrum efficiency and improves the quality of service (QoS) for users.

Usually, the performance of SS is evaluated by false alarm
probability and detection probability [6]. A lower false alarm
probability denotes a higher system throughput while a higher
detection probability signifies a better capability to protect PUs.


### 1.3 Sources
1. Spectrum sensing based on deep learning classification for cognitive radios 
(uses transfer learning and trains their model against many signals to increase robustness)
https://www.scopus.com/record/display.uri?eid=2-s2.0-85081649682&origin=resultslist&sort=cp-f&src=s&sot=b&sdt=b&s=%28TITLE-ABS-KEY%28transfer+AND+learning%29+AND+TITLE-ABS-KEY%28deep+AND+learning%29+AND+TITLE-ABS-KEY%28%22spectrum+sensing%22%29%29&sessionSearchId=e36885f3398f1d40df5de33c13b1372d

2. Robust Deep Sensing through Transfer Learning in Cognitive Radio 
(uses transfer learning to make their model more robust when placed in a new scenario)
https://www.scopus.com/record/display.uri?eid=2-s2.0-85078464224&origin=resultslist&sort=cp-f&src=s&sot=b&sdt=b&s=%28TITLE-ABS-KEY%28transfer+AND+learning%29+AND+TITLE-ABS-KEY%28deep+AND+learning%29+AND+TITLE-ABS-KEY%28%22spectrum+sensing%22%29%29&sessionSearchId=e36885f3398f1d40df5de33c13b1372d&relpos=5

3. Spectrum Sensing in Cognitive Radio Using CNN-RNN and Transfer Learning
(Uses transfer learning to increase the performance of their model in low SNR environments)
https://www.scopus.com/record/display.uri?eid=2-s2.0-85141935811&origin=resultslist&sort=cp-f&src=s&sot=b&sdt=b&s=%28TITLE-ABS-KEY%28transfer+AND+learning%29+AND+TITLE-ABS-KEY%28deep+AND+learning%29+AND+TITLE-ABS-KEY%28%22spectrum+sensing%22%29%29&sessionSearchId=e36885f3398f1d40df5de33c13b1372d&relpos=6

4. A Deep convolutional neural network based transfer learning method for non-cooperative spectrum sensing
(REALLY good, The performance of the proposed method is evaluated against benchmarks, based on over 29,000 spectrograms collected in UHF TV band from a recent measurement campaign. The experiments show that thanks to transfer learning, the proposed method is able to detect TV signals with high accuracy despite a significantly reduced amount of data, thereby providing a high adaptability to various locations, environments, and frequencies. )
https://www.scopus.com/record/display.uri?eid=2-s2.0-85102114260&origin=resultslist&sort=cp-f&src=s&sot=b&sdt=b&s=%28TITLE-ABS-KEY%28transfer+AND+learning%29+AND+TITLE-ABS-KEY%28deep+AND+learning%29+AND+TITLE-ABS-KEY%28%22spectrum+sensing%22%29%29&sessionSearchId=e36885f3398f1d40df5de33c13b1372d&relpos=7

5. Spectrum-Agile Cognitive Radios Using Multi-Task Transfer Deep Reinforcement Learning
(Not as noteworthy
A multi-task deep Q-network (DQN) is utilized to solve the underlying problem where communications over each sub-band represents a single task. The proposed technique exploits transfer learning between tasks to speed up learning operation for new tasks. The proposed multi-task transfer DQN is proved to be converged. It is shown through simulations that the radio is able to learn an efficient strategy to evade interference signals in a partially observable environment. The experimental results indicate that the proposed approach offers up to 24% improvement to the percentage of successful communications when compared to other RL-based approaches )
https://www.scopus.com/record/display.uri?eid=2-s2.0-85105847193&origin=resultslist&sort=cp-f&src=s&sot=b&sdt=b&s=%28TITLE-ABS-KEY%28transfer+AND+learning%29+AND+TITLE-ABS-KEY%28deep+AND+learning%29+AND+TITLE-ABS-KEY%28%22spectrum+sensing%22%29%29&sessionSearchId=e36885f3398f1d40df5de33c13b1372d&relpos=10

6. Spectrum sensing in cognitive radio networks: threshold optimization and analysis
(Could be good, tests in low SNR environments)
https://www.scopus.com/record/display.uri?eid=2-s2.0-85097496195&origin=resultslist&sort=cp-f&src=s&sid=20acac3bc65ac37007d4c5b9b07a988c&sot=a&sdt=cl&s=%28%22Deep+Learning%22+OR+%22Neural+Network%22%29+AND+%28%22Spectrum+Sensing%22+OR+%22Signal+Detection%22%29+AND+%28%22Low+SNR%22%29&sl=100&sessionSearchId=20acac3bc65ac37007d4c5b9b07a988c&relpos=4


7. Spectrum sensing based on adversarial transfer learning
(SEEMS REALLY PROMISING, uses transfer learning to adapt a mode trained on a central node to its local environment)
(Recently, deep learning (DL) based spectrum sensing (SS) has drawn much attention due to its better capacity of feature extraction and superb performance. However, the model robustness of the DL based scheme is limited by reason of the dynamic radio environment, leading to the floating of sensing performance. Motivated by this, adversarial transfer learning is applied to SS here, where the model is pre-trained at the central node firstly and fine-tuned at the local nodes. More specifically, a 2D dataset of the observed signal is constructed under various signal-to-noise-ratio (SNRs) and a convolution neural network (CNN) model is designed. Then a part of samples with various SNRs in the constructed dataset are employed to pre-train the proposed CNN model. After that, the pre-trained CNN model is distributed to local nodes with different SNRs and the pre-trained CNN model is fine-tuned. The proposed CNN model is pre-trained based on the samples under various SNRs, resulting in its stronger adaptability at the local node. The simulation experiments validate the effectiveness of the proposed scheme.)
https://ietresearch.onlinelibrary.wiley.com/doi/full/10.1049/cmu2.12459?sid=vendor%3Adatabase

![[Pasted image 20250317200815.png]]
---

8. TFF-aDCNN: A Pre-Trained Base Model for Intelligent Wideband Spectrum Sensing
https://www.scopus.com/record/display.uri?eid=2-s2.0-85159837922&origin=resultslist&sort=r-f&src=s&sot=b&sdt=b&s=%28TITLE-ABS-KEY%28%22transfer+learning%22%29+AND+TITLE-ABS-KEY%28%22spectrum+sensing%22%29%29&sessionSearchId=535dff9bbdc432011aa917d6b511f9e8&relpos=15

9. Cross-Domain Automatic Modulation Classification Using Multimodal Information and Transfer Learning
https://www.scopus.com/record/display.uri?eid=2-s2.0-85167783524&origin=resultslist&sort=r-f&src=s&sid=7a8a4d19a2775e9beb3665028e9ec14a&sot=a&sdt=a&s=%22transfer+learning%22+AND+%28%22domain+adaptation%22+OR+%22multi-task+learning%22+OR+%22self-supervised+learning%22+OR+%22Multi-Task+Learning%22+OR+%22Adversarial+Transfer+Learning%22%29+AND+%28%22spectrum+sensing%22+OR+%22cognitive+radio%22%29+AND+%28%22Cross+Domain%22+OR+%22unseen%22+OR+%22environments%22%29&sl=257&sessionSearchId=7a8a4d19a2775e9beb3665028e9ec14a&relpos=5


Generative adversarial learning for spectrum sensing
https://www.scopus.com/record/display.uri?eid=2-s2.0-85050300761&origin=resultslist&sort=r-f&src=s&sid=e5e1d93d2047b0ca3fda4bf59807cf69&sot=a&sdt=a&s=%22transfer+learning%22+AND+%28%22domain+adaptation%22+OR+%22multi-task+learning%22+OR+%22self-supervised+learning%22+OR+%22Multi-Task+Learning%22+OR+%22Adversarial+Transfer+Learning%22%29+AND+%28%22spectrum+sensing%22+OR+%22cognitive+radio%22%29&sl=206&sessionSearchId=e5e1d93d2047b0ca3fda4bf59807cf69&relpos=6

CCD-GAN for Domain Adaptation in Time-Frequency Localization-Based Wideband Spectrum Sensing
https://www.scopus.com/record/display.uri?eid=2-s2.0-85165905423&origin=resultslist&sort=r-f&src=s&sid=9ed80916b024fcd803828afb7a708205&sot=a&sdt=a&s=%28%22transfer+learning%22%29+AND+%28%22domain+adaptation%22+OR+%22multi-task+learning%22+OR+%22self-supervised+learning%22+OR+%22adversarial+transfer+learning%22+OR+%22few-shot+learning%22+OR+%22semi-supervised%22+OR+%22limited+labeled+data%22%29+AND+%28%22spectrum+sensing%22%29+AND+%28%22unseen+environment*%22+OR+%22cross-domain%22+OR+%22generalization%22+OR+%22robustness%22%29+AND+%22CNN%22+AND+%28PUBYEAR+%26gt%3B+2020+AND+PUBYEAR+%26lt%3B+2026%29&sl=370&sessionSearchId=9ed80916b024fcd803828afb7a708205

SDR implementation of a light deep learning model based CNN for joint spectrum sensing and AMC
https://qut.primo.exlibrisgroup.com/discovery/fulldisplay?docid=cdi_webofscience_primary_001199599300001CitationCount&context=PC&vid=61QUT_INST:61QUT&lang=en&search_scope=MyInst_and_CI&adaptor=Primo%20Central&tab=Everything&query=any,contains,CNN%20Spectrum%20Sensing%20Transfer%20Learning&pfilter=rtype,exact,articles&offset=0