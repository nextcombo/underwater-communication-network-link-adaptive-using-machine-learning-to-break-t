# Underwater Communication Network Link Adaptive: Using Machine Learning to Break the Difficulty of Time-Varying Channels, Accuracy Approaches 100% [Attached MATLAB Code]

Underwater Communication Network Link Adaptation: Solving the Challenges of Time-Varying Channels with Machine Learning, Approaching 100% Accuracy
When rule-based algorithms struggle to handle strong time-varying channels, machine learning offers a more precise, stable, and engineering-friendly solution.
The study on adaptive link in underwater communication network based on machine learning - Enhanced Regression Tree and Lightweight Feature Selection
Abstract: Underwater acoustic communication (UAC) channels exhibit significant spatiotemporal fast-varying characteristics, influenced by factors such as water temperature, salinity, ocean currents, and depth. Traditional link adaptation (LA) methods based on fixed rules struggle to match dynamic channels, leading to low transmission efficiency and poor reliability. This paper relies on the South Korea Taejon and Incheon sea trial datasets, covering three typical transmission distances of 1km, 2km, and 3km. It first employs rule-based methods such as three-dimensional joint analysis, modulation type analysis, and a fixed SNR threshold strategy to verify the limitations of traditional LA in underwater scenarios. Subsequently, it introduces four machine learning algorithms: Support Vector Machine (SVM), K-Nearest Neighbors (KNN), Pseudo Linear Discriminant Analysis (PLDA), and Enhanced Regression Trees (BRT), for intelligent classification of modulation coding scheme (MCS) levels. The experimental results show that traditional rule-based strategies have limitations such as irreversible channel state, difficult threshold determination, and severe data overlap, failing to form a stable and usable LA mechanism. On the other hand, machine learning methods can fully learn the mapping relationship between channel features and MCS levels. Among them, the Enhanced Regression Tree algorithm achieves a 99.97% MCS classification accuracy, performing best among all algorithms. Further, through Principal Component Analysis (PCA), feature dimensionality is reduced, irrelevant parameters such as Doppler spread and frequency offset are eliminated, and only two to three core channel features are needed to achieve 96.83% modulation classification accuracy and 100% encoding rate classification accuracy, significantly reducing the computational burden and energy consumption of underwater nodes. The proposed solution can provide lightweight, high-reliability, and real-time LA technology support for next-generation distributed underwater monitoring networks.
Introduction: With the rapid development of next-generation marine observation and communication technologies, devices such as underwater sensor networks, autonomous underwater vehicles (AUVs), and submarine base stations have continuously increased their demand for high-speed, stable, and low-power communication. Among all underwater communication methods, underwater acoustic communication is currently the only technology capable of achieving long-range, wide coverage. It has been widely used in marine scientific research, maritime commercial operations, and underwater military security applications.
However, the underwater acoustic channel and the land wireless channel have fundamental differences, making it difficult to overcome technical challenges:
Firstly, the propagation delay is extremely long and the Doppler spread is large. The speed of sound in water is much lower than that of electromagnetic waves, resulting in significant feedback delay at both transmitters and receivers, leading to rapid time-variation and frequency-selective fading in the channel.
Secondly, the multipath effect is severe. The reflections from the sea surface, seabed, and obstacles cause inter-symbol interference, significantly increasing the bit error rate.
Thirdly, the bandwidth resources are extremely scarce, with narrow available frequency bands, making it impossible to directly reuse mature link adaptation models of terrestrial cellular networks (such as LTE and 5G).
Fourth, channel models are difficult to establish, influenced by day and night, seasons, tides, and currents, the statistical characteristics of the channel continue to change, traditional fixed thresholds and fixed mapping rules completely lack generalization capabilities.
To enhance system spectrum efficiency and transmission reliability, Adaptive Modulation and Coding (AMC) has become the core technology for underwater communication. Its goal is to dynamically select the optimal modulation method and coding rate based on real-time channel quality. However, traditional rule-based link adaptation methods rely on manual setting of mapping relationships between SNR, BER, and data rate, which exhibit significant deficiencies in real sea trial data: state irreversibility, threshold instability, limited number of MCS options, and a mismatch between high data rates and high SNR.
At the same time, underwater nodes are typically powered by batteries and have strict energy constraints, making it difficult to deploy complex algorithms in real-time. Therefore, developing an intelligent link adaptive method with low feature dimension, high classification accuracy, strong robustness, and lightweight inference has become an urgent need in the field of underwater communication. Machine learning, with its powerful nonlinear fitting, feature learning, and pattern classification capabilities, can automatically learn the channel-MCS mapping relationship from a large amount of actual measurement data without the need for manual modeling, making it the best choice to break through the bottleneck of underwater link adaptation.
Method Introduction: This paper is based on two sets of real sea trials datasets. It first completes the comparative verification of traditional rule-based methods, then constructs a machine learning classification framework, and finally forms a lightweight optimized solution for engineering deployment.
I. Experimental Data and Network Architecture
The experimental data and network architecture utilize a cellular underwater acoustic communication network architecture, consisting of Underwater Base Station Controller (UBSC), Underwater Base Station (UBS), and Underwater Equipment (UE). The FDD dual-mode operation is employed, with long-duration sea trials completed in the Tai'an (1km, 3km) and Incheon (2km) waters, collecting multidimensional channel parameters including SNR, bit error rate (BER), data rate, coherence bandwidth, maximum estimated delay, root mean square delay spread, pilot interval, repeat mode, Doppler spread, and frequency offset.
Tai'an dataset: 417 sets of experimental data, covering four modulation schemes: BPSK, QPSK, 16QAM, and 64QAM;
Incheon dataset: 10,105 sets of experimental data, with sufficient sample volume suitable for machine learning training and testing.
II. Traditional Rule-Based Link Adaptation Methods
To compare the effectiveness of machine learning, this paper first employs three typical rule-based methods for analysis:
1. Three-Dimensional Joint Analysis
Using SNR, data rate, and BER as dimensions, a three-dimensional scatter plot is drawn to attempt to find the optimal MCS combination. The results show that high BER areas are concentrated in low data rate intervals, with SNR distribution being discrete and unable to form a stable mapping.
2. Analysis by Modulation Type
By selecting stable repeat modes according to BPSK, QPSK, 16QAM, and 64QAM respectively, overlapping parameters are eliminated, but only 21 levels of MCS are selected, and SNR remains discontinuous, failing to meet the logic of link adaptation.
3. Fixed SNR Policy
Assigning fixed SNR ranges for each modulation scheme, attempting to simplify MCS selection. The results indicate that there are very few available MCS levels, preventing the use of the highest data rates, and the SNR ranges are completely misaligned in the 3km scenario, contradicting the objectives of link adaptation.
All three rule-based methods failed due to severe channel time-variability, nonlinear parameter relationships, and severe data overlap, proving traditional solutions cannot meet the requirements of real underwater scenarios.
III. Machine Learning-Based MCS Classification Method
2. Comparison of Four Types of Machine Learning Algorithms This paper selects four machine learning algorithms suitable for nonlinear classification, and classifies MCS levels. 70% of the data is used for training, and 30% for testing:
Support Vector Machine (SVM)
Constructing the optimal separating hyperplane, achieving 83.31% classification accuracy on the Incheon dataset and only 46.4% on the Tai'an dataset, with a general adaptability to small sample sizes and high data overlap.
K-Nearest Neighbors (KNN)
Classification based on distance measurement, with a classification accuracy of 96.83% under 2-3 dimensions and an encoding rate classification accuracy of 100%, lightweight, low complexity, suitable for underwater deployment.
Pseudo-linear discriminant analysis
Maximizing inter-class distance and minimizing intra-class variance, overall accuracy 81.99%, performance medium.
Boosted Regression Trees (BRT)
Adopting the idea of ensemble learning, a weighted fusion of multiple decision trees is implemented on the Incheon dataset to achieve an MCS classification accuracy of 99.97%. It exhibits robustness against missing values and outliers, making it the optimal algorithm in this paper.
3. Optimal feature combination for lightweight design, aiming at low power consumption in underwater applications, the following two sets of engineering-valued feature combinations were finally determined:
Two-parameter optimal combination: SNR + Coherence Bandwidth (CB)
Three-parameter optimal combination: Maximum Estimated Delay (MED) + Coherent Bandwidth (CB) + RMS of Squared Time Delay Spread (RMS)
Both groups of schemes can maintain over 96% classification accuracy in a very few feature dimensions, meeting the requirements of real-time inference and low energy consumption.
Conclusion 1
Traditional rule-based methods are completely inapplicable to underwater communication.
The underwater channel with strong time-varying, high dynamic and strong multipath characteristics leads to a nonlinear, non-monotonic, irreversible relationship between SNR, data rate, BER. The three-dimensional analysis, fixed SNR, modulation analysis and other rules strategies cannot form a stable and usable link adaptive mechanism.
1  
Machine learning significantly improves the classification accuracy of underwater MCS.
Enhanced Regression Trees (BRT) leverage the advantages of ensemble learning to achieve nearly perfect classification accuracy of 99.97%, accurately learning complex mapping between channel features and MCS levels; KNN algorithms perform outstandingly in lightweight scenarios, suitable for resource-constrained underwater nodes.
1  
PCA dimensionality reduction can achieve low power and high precision deployment.
By employing Principal Component Analysis to eliminate irrelevant features such as Doppler spread and frequency offset, only a few core channel parameters are needed to achieve high-precision modulation and coding rate classification. This significantly reduces computational overhead and node energy consumption, addressing the issue of limited computing power and battery capacity in underwater equipment.
1  
Possesses practical engineering implementation value.
The link adaptation scheme based on machine learning proposed in this paper can be directly applied to underwater buoys, base stations, sensor nodes, AUVs, etc., to achieve dynamic, real-time, intelligent MCS selection, significantly improve spectrum efficiency, communication rate, and system reliability, providing key technical support for the next generation of distributed underwater monitoring and communication networks.
In today's era of continuously advancing intelligent and broadband maritime communication, machine learning is opening a new path for underwater link adaptability, making it possible for underwater devices to "hear clearly, transmit quickly, and consume minimally."

## Images

![Underwater communication network link adaptive: Using machine learning to crack the problem of time-varying channels, with an accuracy approaching 100% [with MATLAB code].](01.jpg)
![Underwater communication network link adaptive: Using machine learning to crack the problem of time-varying channels, with an accuracy approaching 100% [with MATLAB code].](02.jpg)
![Underwater communication network link adaptive: Using machine learning to crack the problem of time-varying channels, with an accuracy approaching 100% [with MATLAB code].](03.jpg)
![Underwater communication network link adaptive: Using machine learning to crack the problem of time-varying channels, with an accuracy approaching 100% [with MATLAB code].](04.jpg)
![Underwater communication network link adaptive: Using machine learning to crack the problem of time-varying channels, with an accuracy approaching 100% [with MATLAB code].](05.jpg)

<!-- PAYMENT_BLOCK -->

## Get this dataset

- Payment link (Stripe): [Buy now](https://buy.stripe.com/3cs8yP7sY87d0vu9AB)
- Payment QR code: ![Payment QR code](pay.png)

<!-- /PAYMENT_BLOCK -->
