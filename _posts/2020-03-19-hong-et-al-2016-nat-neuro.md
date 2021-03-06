---
layout: post
title: Explicit information for category-orthogonal object properties increases along the ventral stream
date: 2020-03-19
categories: blog
---

[**Explicit information for category-orthogonal object properties increases along the ventral stream**][hong-natneuro-2016] Hong et al., Nat. Neuro (2016). All figures are from the linked paper.

#### Introduction & Quick Summary
We've looked at multiple papers exploring and expanding the paradigm developed
in [**Yamins et al (2014)**][yamins-pnas-2014]. Just as a recap, Yamins et al (2014).,
implemented a convolutional neural network optimized for object classification task
performance and was able to linearly decode macaque neural response that predicted
about 48% of the explainable IT neural response variance (visit [**Brain-Score**][brainscore]
for more recent developments in predicting neural response of various areas along the visual
stream). This CNN, which the paper calls hierarchical modular optimization (HMO) model, also
performed object classification at the human performance level.


This [paper][hong-natneuro-2016] probes whether ventral visual areas build a robust
representation of 'category-orthogonal' object properties such as position, size,
aspect ratio, etc. It also tackles whether these 'category-orthogonal' object property
information is lost or preserved along the visual stream.


Previous research have shown that robust representations of objects are built along
the ventral visual stream to support visual object categorization. However, it cannot
be the case that visual perception only concerns itself with categorization as humans
are able to estimate other object-related properties such as object position, size,
aspect ratio and orientation. While these category-orthogonal properties are often
considered to be 'nuisance' variables that are thrown away along the ventral visual
stream, our ability to relatively precisely estimate those properties show that some
of these information is preserved. 

{% figure caption: "**Figure 1**: Illustration of possible scenarios"%}
![figure-1](https://i.imgur.com/iRvpK5H.png)
{% endfigure %}

Hong et al., catalogs four hypotheses about the pattern of information for category-orthogonal 
properties across the ventral visual stream:

* **H1**. ‘local coding’. View tuned units are aggregated across identity-preserving
transformations at each scale to produce partially view-invariant units, which are themselves
aggregated to produce invariance at a larger scale. Trade-off between increasing receptive field
size and {categorization ability, orthogonal task performance}. 

* **H2**. Non-categorical properties rely on intermediate visual features, analogous to
‘border-ownership cells’ that have been discovered in V2. Therefore, information for
category orthogonal properties peak in the middle of the ventral stream.

* **H3**. Information for low-level orthogonal properties is not lost along the
ventral hierarchy, but is instead preserved because it may be behaviorally useful.

* **H4**. Information increases for the category-orthogonal object tasks, similar 
to the increase in information for categorization task.

This manuscript identified the pattern of information by recording neural response in IT and V4
as well as testing simulated V1 neural response to a large image set of real-world objects with
simultaneous variations in object position, size, pose and background scene. In doing so,
the authors quantified the amount of explicitly available information in each ventral stream
processing stage. Moreover, they assessed the dependence of information amount on image complexity
and how the information is distributed across neural population.

Hong et al., found that
* *for all tasks in the high variation image set...*
  * amount of explicitly available information progressively increased along the ventral stream,
  consistent with **H4**
  * task information is broadly distributed throughout the IT population
* *for all tasks in the low variation image set...*
  * increase in information along the ventral stream **attenuated**
  * in some cases, the pattern of information reversed

Furthermore, convolutional neural network optimized for *categorization task performance*, was
sufficient in accurately predicting patterns of information along the ventral stream across tasks
and image variation levels. Thus, the authors claim these results are evidence that the perception of 
category-orthogonal properties, like object category perception, is constructed by the
ventral visual hierarchy and that the neural network model provides an insight
into the principles of the underlying hierarchy.


#### Comparing task representations across cortical areas
Some individual sites displayed high level of task selectivity. For example, the sites in **Supp. Fig. 2a**
displayed high object category selectivity for different objects while the sites in **Supp. Fig. 2b** shows
positional selectivity response. As visible in **Fig 3a**, the performance of single best sites from IT (blue)
always outperformed the single best sites from V4 (green).

{% figure caption: "**Supplementary Figure 2 {a,b}**: Characterization of IT and V4 responses"%}
![supp-figure-2](https://i.imgur.com/SVrRO0N.png)
{% endfigure %}

The authors then compared visual property encoding at the neural population level. As visible in comparing
the performance levels shown in **Fig. 3a** and **Fig. 3b**, neural population performance levels for
representing a task were higher than single site performance levels. And following the trend in single site
performance comparison, IT populations (**Fig. 3b** blue) always performed better than V4
populations(**Fig. 3b** green). Furthermore, both IT and V4 populations were better
performing than V1 models (**Fig. 3b** grey) and pixel controls (**Fig. 3b** black). 

{% figure caption: "**Figure 3**: Comparison between ventral cortical areas of object property information encoding in high-variation stimuli"%}
![figure-3](https://i.imgur.com/nuPzxti.png)
{% endfigure %}

#### Neural consistency with human performance patterns
To bring human performance patterns into the picture, the manuscript estimated, across neural population
and tasks, the number of neural sites required to reach parity with human performance levels. For all
tasks, IT population reached human performance parity with at most 2000 sites, with a mean of about a third
of those sites. V4 population needed several orders of magnitute more sites and V1 population needed several
orders of magnitude more than V4 population -- so much so that V1 reaching human performance parity
is essentially intractable. 


#### Distribution of Information across IT sites
Next, the authors characterized whether category-orthogonal properties are estimated by dedicated subpopulations
in the IT or are jointly distributed over IT neurons in an overlapping manner. Previous studies showing
modularity of face, body and place selective neurons suggest the former hypothesis while studies that demonstrate
IT units tuned to multiple visual properties suggest the former.


To test these hypotheses, the paper took a two step approach:
1. Quantify distribution of information across sites for each task
2. Quantify information overlap between pairs of tasks


Two metrics, sparseness and imbalance, were used for the first step.
* ***Sparseness*** measures the distribution of task-response correlation
* ***Imbalance*** measures relative dominance of task-response correlated vs anticorrelated sites

Positive weights of the linear decoder for each of 266 IT sites was defined to be task-response
correlation while negative weights was defined to be a task-response anticorrelation. **Fig. 6a** show
that the distribution of task-response correlated units were sparse (At P=0.5 level, nearly half
of the tasks had sparseness indistinguishable from the standard normal distribution). Not only was the
information sparsely distributed across sites for most tasks, imbalance metric were also similar to
an equivalently sized standard normal distribution at the P=0.5 level (**Fig. 6b**). These results
suggest that other from few tasks that require relatively selective units, information for most
category-orthogonal tasks was normally distributed.


{% figure caption: "**Figure 6**: Distribution and overlap of IT cortex site contribution across tasks"%}
![figure-6](https://i.imgur.com/byrmlPd.png)
{% endfigure %}

### Questions
1. **Fig. 6c** show that face discrimination task required neither high-sparseness nor high-imbalance.
[Studies][tsao-pnas-2008-face-patch] conjecture and prove the existence of face patches in IT cortex.
If face patches were real, shouldn't the face discrimination task require a high level of sparseness
as only a few sites should be highly informative for the task? I can accept the low measure of imbalance
but very low measure of sparseness seems contradictory to previous studies.


[hong-natneuro-2016]:https://www.nature.com/articles/nn.4247
[yamins-pnas-2014]:https://www.pnas.org/content/111/23/8619
[kell-neuron-2018]:https://www.sciencedirect.com/science/article/pii/S0896627318302502?via%3Dihub
[brainscore]:www.brain-score.org
[tsao-pnas-2008-face-patch]:https://www.pnas.org/content/105/49/19514