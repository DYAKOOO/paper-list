* Mdnotes File Name: [[MAP-Neo Highly Capable and Transparent Bilingual Large Language Model Series]]

# ### Annotations 6-4-2024, 4-41-26 PM

### Annotations 6/4/2024, 4:41:26 PM  

* “OLMo [36] has made a great stride in narrowing this gap by improving pre-training data and data processing pipelines, and introducing more open-source components, including training logs and ablations.” (Zhang et al., 2024, p. 4)

* “we introduce MAP-Neo, a fully open-source and transparent bilingual LLM suite that achieves superior performance to close the gap with closed-source models.” (Zhang et al., 2024, p. 4)

* “Our model, MAP-Neo-7B, emerges as the new lead in this evolving landscape, as shown in Table 1, which balances performance and transparency.” (Zhang et al., 2024, p. 5)

* “Moreover, OLMo cannot handle languages beyond English” (Zhang et al., 2024, p. 5)

* [[Interesting]] “3 Tokenizer” (Zhang et al., 2024, p. 5) Tokenizer [!tags] #Tokenization

* [[note]] “We train our tokenizer using the byte-pair encoding (BPE) algorithm [88] via the implementation of SentencePiece [56].” (Zhang et al., 2024, p. 5) SentencePience[56] , BPE [!tags] #BPE #SentencePiece

* [[confusion]] “The character coverage rate is set to 0.9999.” (Zhang et al., 2024, p. 5) Character Convergence? [!tags] #Convergence

* “We encountered a specific issue during the initial phase of our model’s pre-training.” (Zhang et al., 2024, p. 6)

* [[disagreement]] “To address this issue, we fixed this bug in the second phase of our training (§6.2), which stabilizes and significantly improves the code metrics. Furthermore, we observe that this issue is well addressed in the decay phase training stages under the new tokenizer settings, where rapid improvements are achieved.” (Zhang et al., 2024, p. 6) Not well adressed in the decay phase training stage?

* “Moreover, we also investigate the compression rates across various categories of data, categorized by both language (Chinese and English) and data source quality (high-quality and web-sourced) as shown in Table 2.” (Zhang et al., 2024, p. 6)

* “The HQ cn category has a compression rate of 1.577, while the HQ en category exhibited a higher rate of 3.311 characters per token. Second, data sourced from the web (Web) also comprise more characters than Chinese ones.” (Zhang et al., 2024, p. 6)

* “Therefore, it remains necessary to further investigate tokenization strategies for subsequent usage scenarios.” (Zhang et al., 2024, p. 6)

* “4 Matrix Data Pile” (Zhang et al., 2024, p. 6)

* “It is widely recognized that a well-constructed training corpus is essential for training LLMs.” (Zhang et al., 2024, p. 6)

* “Additionally, we design Matrix based on the idea of retrieving, filtering, and cleaning high-quality data under various practical circumstances, which are discussed as follows:” (Zhang et al., 2024, p. 7)

* “The final composition of the corpus is as follows: 52.55% from Common Crawl, 22.29% from programming code, and the rest from academic papers, books, and other printed materials, as illustrated in Figure 2.” (Zhang et al., 2024, p. 7)

* “The source comes from the Head and Middle parts of RedPajama-Data-V2 [25], CC part of Dolma [95], the EN part of Cultrax [72], the Refined-Web part of Amber [66], SlimPajama [94] and falcon [74].” (Zhang et al., 2024, p. 7)

* “4.1.1 Filtering” (Zhang et al., 2024, p. 7)

* “we adapt well-designed cleaning methods [74, 14, 76, 78] and tailor our rules for each one to ensure quality consistency.” (Zhang et al., 2024, p. 7)

* “For datasets lacking quality annotations, we apply the established rules and thresholds derived from RedPajama-V2, while customizing them to align with the unique characteristics of each dataset.” (Zhang et al., 2024, p. 7)

* “Given the unique characteristics of each subset, we conduct individual sampling and evaluation to ensure that the modifications in rules and thresholds are aligned with our filtering requirements” (Zhang et al., 2024, p. 7)

* “For the Gutenberg subset, which predominantly contains book texts, we apply only a few rules to avoid the time-consuming process of executing extensive heuristic checks on long texts.” (Zhang et al., 2024, p. 8)

* “3) Sensitive word check to eliminate texts containing any terms from a blacklist” (Zhang et al., 2024, p. 8)

* “4.1.2 Deduplication” (Zhang et al., 2024, p. 8)

* “Repetitions can be categorized into exact duplicates and near duplicates. For exact duplicates, we employ exact document deduplication to remove them. For near duplicates, we utilize Minhash LSH deduplication to remove them as much as possible.” (Zhang et al., 2024, p. 8)

* “For processing data in English, Spark is employed to handle the dataset.” (Zhang et al., 2024, p. 8)

* “Minhash LSH Deduplication” (Zhang et al., 2024, p. 8)

* “The principle of MinHash is to represent a set with smaller hash values, which can then be used to estimate the Jaccard similarity [47] between two sets: Jaccard(A, B) = (A ∩ B)/(A ∪ B).” (Zhang et al., 2024, p. 8)

* “Thus, each set can be represented by a vector of these minimum hash values, forming the set’s MinHash signature. For text data, an n-gram approach can be used to construct a set.” (Zhang et al., 2024, p. 8)

* “Another hash function is then used to map each band to a hash bucket.” (Zhang et al., 2024, p. 8)

* “Here, we utilize 128 unique hash functions to form signatures, divided into 9 bands, with each band containing 13 hash values. Consequently, the Jaccard threshold is set at 0.8.” (Zhang et al., 2024, p. 8)

* “For processing vast amounts of data efficiently, a distributed implementation [53] based on map-reduce is adopted.” (Zhang et al., 2024, p. 8)

* “Then, each paragraph is hashed using SHA256. Next, the hash values are deduplicated. After deduplication, the deduplicated text is restored according to the document ID and offset.” (Zhang et al., 2024, p. 8)

* “This method follows [58]. Given the diversity of languages, when the length of repeated text is sufficiently long, it is highly likely that they are either derived from one another or sourced from the same reference. Therefore, when two texts, ti and tj share sufficiently a long substring, that is ta..a+k i = tb..b+k j , one of them is removed. For the selection of the length threshold, we adhere to the setting in [58], choosing k=50.” (Zhang et al., 2024, p. 9)

* “Due to our distributed environment, the memory of a single node is insufficient to hold all the data.” (Zhang et al., 2024, p. 9)

* “Therefore, we did not adopt the implementation in [58]. In our work, we segment each text into sliding windows of 50 characters with a step size of 1. We then compute the SHA256 hash value for each window along with its corresponding document ID and offset” (Zhang et al., 2024, p. 9)

* “We further provide a pipeline to crawl and process the web content from scratch and showcase it with the Chinese language data, which could be a step-by-step guide for follow-up research to build a new up-to-date corpus.” (Zhang et al., 2024, p. 9)

* “4.2.1 Filtering” (Zhang et al., 2024, p. 9)

* “we focus intensively on eliminating HTML-related artifacts and rectifying textual inconsistencies.” (Zhang et al., 2024, p. 9)

* “For example, we refine the rules to distinguish between ‘characters’ and ‘words’ in Chinese texts, adapting the tokenization method accordingly.” (Zhang et al., 2024, p. 10)

* “Our Chinese filtering steps are similar to the rules adapted to filter Massive Appropriate Pre-train Chinese Corpus (MAP-CC) [30]:” (Zhang et al., 2024, p. 10)

* “4.2.2 Deduplication” (Zhang et al., 2024, p. 10)

* “Due to difficulties in deploying Spark in the environment for processing Chinese, we have re-implemented the first two methods.” (Zhang et al., 2024, p. 10)

* “we have adopted a Bloom Filter approach and set the false positive rate of the Bloom Filter to 0.001.” (Zhang et al., 2024, p. 10)

* “Discussions on Exact Document and MinHash LSH Deduplication can be found in §4.1.2.” (Zhang et al., 2024, p. 10)

* “If they are similar, the subsequent line is removed. The division of lines includes the use of the following delimiters: “[”, “.”, “!”, “?”, “”, “. . . . . . ”, “]”. We use edit distance to judge whether two lines L1 and L2 are similar as follows:” (Zhang et al., 2024, p. 10)

* “where |L| is the length of line L and “editDist” is short for edit distance.” (Zhang et al., 2024, p. 10)

* “Due to the computational complexity of calculating edit distance being O(len(L1) × len(L2)), to accelerate this process, we additionally propose two methods to judge dissimilarity:” (Zhang et al., 2024, p. 10)

* “Note that the first method has a computational complexity of O(1), and the second method has a complexity of O(len(L1) + len(L2)).” (Zhang et al., 2024, p. 10)

* “Otherwise, we calculate isSimilar(L1, L2) to obtain the similarity between L1 and L2.” (Zhang et al., 2024, p. 10)

* “4.3 Document Conversion Pipeline” (Zhang et al., 2024, p. 10)

* “However, it seems to be a gold mine of high-quality corpus except that the golds lie deeply under the digital dirt” (Zhang et al., 2024, p. 10)

* “We observe two core issues in designing an effective conversion pipeline to extract plain text from documents: i) analyzing layout information and identifying different layout elements including text, titles, captions, images, tables, and formulas, and ii) recognizing the relationships among these layout components.” (Zhang et al., 2024, p. 11)

* “For example, we utilize Marker for enhanced language support and PP-StructureV2 for efficient layout parsing. As illustrated in Fig. 4, our document conversion framework is comprised of four parts:” (Zhang et al., 2024, p. 11)

* “Layout Detection” (Zhang et al., 2024, p. 11)

* “This model’s performance is further enhanced by employing the FGD (Feature Gradient Descent) algorithm, which optimizes feature extraction for more accurate layout detection” (Zhang et al., 2024, p. 11)

* “Text recognition employs PP-OCRv4, Text recognition employs PP-OCRv4, notable for its compatibility with multiple computing devices and boasts strong recognition capabilities; approximately one hundred language recognition models have been publicly released, applicable to a broader range of document recognition tasks.” (Zhang et al., 2024, p. 11)

* “Table reconstruction is achieved using SLANet, which represents tables in HTML format.” (Zhang et al., 2024, p. 11)

* “Other regions, such as headers, footers, and page numbers, are discarded and do not proceed to the post-processing and reconstruction stages.” (Zhang et al., 2024, p. 11)

* “The MAP-Neo model architecture is grounded on the transformer decoder as outlined by Vaswani et al. [103].” (Zhang et al., 2024, p. 13)

* “The essential parameters defining this architecture are detailed in Table 5.” (Zhang et al., 2024, p. 13)

* “These enhancements are listed below:” (Zhang et al., 2024, p. 13)

* “Multi-Query Attention [92].” (Zhang et al., 2024, p. 13)

* “This modification is based on ablation studies indicating that multi-query attention is particularly effective at more minor scales [92].” (Zhang et al., 2024, p. 13)

* “RoPE Embeddings [97].” (Zhang et al., 2024, p. 13)

* “RMSNorm.” (Zhang et al., 2024, p. 13)

* “is normalized using RMSNorm [120].” (Zhang et al., 2024, p. 13)

* “Activation Function” (Zhang et al., 2024, p. 13)

* “SwiGLU [93]” (Zhang et al., 2024, p. 13)

* “6 Pre-training” (Zhang et al., 2024, p. 13)

* “The distribution of data used across different phases is depicted in Figure 5. Note that we increase the volume of code data in the decay phase. Specifically, during the fundamental phase, since Stack V2 [68] was not yet available, we utilized Stack V1 [54] and repeated the dataset twice to achieve a balanced data ratio. In the decay phase, with the release of Stack V2 [68], we incorporated it as the code component for training.” (Zhang et al., 2024, p. 14)

* “The open-source data used for pre-training is shown in Table 16, the data repetition details are shown in Table 17 and the training hyperparameters are shown in Table 6.” (Zhang et al., 2024, p. 14)

* “6.1 Fundamental Phase: General Ability Acquisition” (Zhang et al., 2024, p. 14)

* “During the fundamental phase, we employ a two-stage learning rate scheduler (LRS) to equip the model with a robust capability for general text generation.” (Zhang et al., 2024, p. 14)

* “his is followed by a cosine decay phase, during which the rate gradually diminishes back to ηb = 2 × 10−5 over about 365k steps. The learning rate f (t) as a function of time t can be delineated as follows:” (Zhang et al., 2024, p. 14)

* “This learning phase processes about 3, 726 billion tokens, ensuring the model’s robust training on diverse textual data.” (Zhang et al., 2024, p. 14)

* “6.2 Decay Phase: Improvement and Rectification” (Zhang et al., 2024, p. 15)

* “The learning rate in this decay phase initiates at ηc = 2 × 10−4 and undergoes exponential decay over tdecay = 148k steps, with a half-life T corresponding to half the tdecay steps, similar to the decay phase employed by MiniCPM [44], which can be formulated as follows:” (Zhang et al., 2024, p. 15)

* “The deliberate enrichment of the dataset with a higher ratio of code, coupled with instructional inputs, ensures a more robust and versatile model, adept at tackling complex coding tasks as well as understanding and generating professional responses in different fields.” (Zhang et al., 2024, p. 15)

* “7 Alignment” (Zhang et al., 2024, p. 15)

* “7.1 Supervised Fine-tuning” (Zhang et al., 2024, p. 15)

* “In the first phase, we collect a large amount of instruction data to enhance the foundational abilities of LLMs.” (Zhang et al., 2024, p. 15)

* “This process finetunes a pre-trained LLM on chat-style data, including both queries and responses. We illustrate the details of data construction and training strategies.” (Zhang et al., 2024, p. 15)

* “Additionally, we incorporate the complete Code-Feedback [125] dataset and a subset of WebInstructSub [117] data.” (Zhang et al., 2024, p. 15)

* “Chat Phase: Enhancing Chat Abilities” (Zhang et al., 2024, p. 15)

* “Our experiments have demonstrated that this additional phase of SFT significantly boosts the model’s performance on chat benchmarks, such as MT-Bench [124] and AlpacaEval [62], without compromising its foundational abilities.” (Zhang et al., 2024, p. 15)

* “The model’s training process utilizes the AdamW optimizer with the hyperparameters in Table 6.” (Zhang et al., 2024, p. 15)

* “7.2 Iterative DPO” (Zhang et al., 2024, p. 16)

* “Using this dataset, DPO parameterizes a language model πθ and directly estimates its parameters through maximum likelihood estimation on the human preference dataset D as follows:” (Zhang et al., 2024, p. 16)

* “We utilize Nectar7 as our prompt dataset and Starling-RM-34B8 [126] as our reward model.” (Zhang et al., 2024, p. 16)

* “To preserve the multilingual capabilities of our model, we also adopt a preference dataset9 in Chinese in the 3-rd iteration.” (Zhang et al., 2024, p. 16)

* “8 Scaling Law of MAP-Neo” (Zhang et al., 2024, p. 16)

* “where A, B, E, α, β, αc, Dc, αN , Nc and d are hyperparameters to be optimized.” (Zhang et al., 2024, p. 16)

* “green” (Zhang et al., 2024, p. 17)

* “We fit the Chinchilla law and NEO law on 250M, 460M, and 980M and predict the model behavior on both training samples and samples from the 7B model.” (Zhang et al., 2024, p. 17)

* “However, our version of SMS law, as detailed in Eq. 6, is simpler and yields superior results compared to the corresponding model in the OpenAI framework.” (Zhang et al., 2024, p. 17)

* “This process is formalized as minimizing the validation cross-entropy loss L, subject to constraints imposed by available computational resources (C), specifically floating-point operations per second (FLOPs), as denoted below:” (Zhang et al., 2024, p. 17)

* “To evaluate the fit of the scaling law, we employ the Huber loss ( δ = 1e − 3) between the actual logloss and the predicted logloss, along with the R2 value between the true loss and predicted loss.” (Zhang et al., 2024, p. 17)

* “By leveraging these methods, we aim to ensure the accuracy and reliability of our scaling law predictions, enabling efficient training of large-scale language models.” (Zhang et al., 2024, p. 17)

* “To address this discrepancy between Chinchilla prediction and observation, we introduce the following equation, denoted as NEO scaling law, which includes one additional regularization term log(D) for datasets containing several trillion tokens across various corpora:” (Zhang et al., 2024, p. 17)

* “Therefore, for a dataset size less than hundreds of trillion tokens, the loss remains within a reasonable range.” (Zhang et al., 2024, p. 18)

* “From the following Table 8, we observe that the NEO scaling law equation yields significantly better results on the training set and testing set.” (Zhang et al., 2024, p. 18)

* “Meanwhile, after training, We observe that the real training loss in this configuration is 0.6591, which is close to the prediction loss value and demonstrates the effectiveness of the NEO scaling law” (Zhang et al., 2024, p. 18)

* “In contrast, our predictions of our NEO Scaling Law produce better fitting results when compared with the results of Chinchilla Law for MAP-Neo-7B and DeepSeek-67B” (Zhang et al., 2024, p. 18)

* “9 Infrastructure” (Zhang et al., 2024, p. 19)

* “Spark [118] is used for distributed computing, and object storage is used to save the data.” (Zhang et al., 2024, p. 19)

* “There are a total of 94 machines. For the Chinese data processing, there are a total of 14 machines. Among them, 6 machines have a 96-core CPU and 180GB of memory, while the other 8 machines have a 48-core CPU and 190GB of memory. Network File System (NFS)[84] is used as the distributed file storage system.” (Zhang et al., 2024, p. 19)

* “the usage of Megatron-core achieves a rate of 7200 TPS when training a 7B model, which surpasses the performance of 6400 TPS observed under the same settings without employing Megatron-core” (Zhang et al., 2024, p. 19)

* “Secondly, we make modifications to Megatron-LM to specifically prevent overflow issues detailed in A.3 when processing large data corpora” (Zhang et al., 2024, p. 19)

* “Our infrastructure utilizes distributed computing techniques to optimize the training of our models. Specifically, our 7B model is trained using an H800 configuration with 512 GPUs across 64 nodes and employs NCCL for backend distribution with ibp as the network interface and mlx5 of InfiniBand hardware to enhance inter-GPU communication. Tensor model parallelism is configured to utilize 2 GPUs,” (Zhang et al., 2024, p. 19)

* “This approach enables the management of more extensive datasets and more complex model training with significantly reduced memory overhead.” (Zhang et al., 2024, p. 19)

* “Our cluster consists of machines with dual Intel Xeon CPUs and eight NVIDIA H800 GPUs” (Zhang et al., 2024, p. 19)

* “Each machine’s network configuration includes four RDMA NICs, each offering 200 Gbps of full duplex bandwidth and integrated GPU Direct RDMA capabilities.” (Zhang et al., 2024, p. 19)

* “Notably, the GPU array is interconnected through four NVIDIA NVSwitches, enabling robust intra-GPU communication with a bandwidth of 400 Gbps.” (Zhang et al., 2024, p. 19)

* “This arrangement ensures a network convergence ratio of 1:1, a critical factor in maintaining optimal data flow and reducing bottlenecks. Connectivity within this structure is meticulously organized such that every two S0 switches serve 32 servers, with a total of 32 S0 switches networking within each minipod. This setup exemplifies an advanced implementation designed to maximize throughput and minimize latency in data center environments.” (Zhang et al., 2024, p. 19)

* “We do not perform any post-processing on the evaluation content, maintaining the integrity of the raw outputs.” (Zhang et al., 2024, p. 22)

* “The detailed results of our comparison with other base models are shown in Table 9.” (Zhang et al., 2024, p. 22)

* “Standard Benchmarks” (Zhang et al., 2024, p. 22)

* “10.1.2 Discussions” (Zhang et al., 2024, p. 22)