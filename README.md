# Measuring and Mitigating Social Biases in Language Models

## Contributors

Correspondence to: 
  - [Paul Pu Liang](http://www.cs.cmu.edu/~pliang/) (pliang@cs.cmu.edu)
  - Chiyu Wu (chiyuwu23@gmail.com)

## Motivation

As machine learning methods are deployed in real-world settings such as healthcare, legal systems, and social science, it is crucial to recognize how they shape social biases and stereotypes in these sensitive decision-making processes. Among such real-world deployments are large-scale pretrained language models (LMs) that can be potentially dangerous in manifesting undesirable representational biases - harmful biases resulting from stereotyping that propagate negative generalizations involving gender, race, religion, and other social constructs. As a step towards improving the fairness of LMs, we carefully define several sources of representational biases before proposing new benchmarks and metrics to measure them. This repository contains a set of tools to benchmark social biases in LMs.

## Datasets

To accurately benchmark LMs for both bias and context associations, it is also important to use \textit{diverse contexts} beyond simple templates used in prior work. Specifically, the Sentence Encoder Association Test~\citep{may2019measuring}, StereoSet~\citep{nadeem2020stereoset}), and templates in~\citet{sheng2019woman} are all based on combining bias terms (e.g., gender and race terms) and attributes (e.g., professions) with simple placeholder templates (e.g., \textit{The woman worked as}, \textit{The man was known for}). Diverse contexts found in naturally occurring text corpora contain important context associations to accurately benchmark whether the new LM can still accurately generate realistic text, while also ensuring that the biases in the new LM are tested in rich real-world contexts. To achieve this, we collect a large set of $30,000$ diverse contexts from $5$ real-world text corpora spanning \textsc{WikiText-2}~\cite{DBLP:journals/corr/MerityXBS16}, \textsc{SST}~\cite{socher-etal-2013-recursive}, \textsc{Reddit}, \textsc{MELD}~\citep{poria-etal-2019-meld}, and \textsc{POM}~\cite{Park:2014:CAP:2663204.2663260} which covers both spoken and written English language across formal and informal settings and a variety of topics (Wikipedia, reviews, politics, news, and TV dialog). We summarize these contexts and metrics in Table~\ref{sources} (see Appendix~\ref{app_data} for details).

## Evaluation metrics

### Fine-grained local biases

### High-level global biases

### LM performance

To accurately benchmark LMs for both fairness and performance, we use two sets of metrics to accurately estimate bias association while allowing for context association. To estimate for bias association, we measure whether $p_\theta(w_{t}|c_{t-1}^{(1)}) \approx p_\theta(w_{t}|c_{t-1}^{(2)})$ across the entire distribution of next tokens at time $t$ (i.e., local bias) as well as whether $g (s^{(1)}) \approx g (s^{(2)})$ for entire generated sentences (i.e., global bias). To estimate for context association, we measure whether $p_\theta(w^*|c_{t-1}^{(1)})$ and  $p_\theta(w^*|c_{t-1}^{(2)})$ for the ground truth word $w^*$ are both \textit{high} implying that the LM still assigns high probability to the correct next token by capturing context associations.
