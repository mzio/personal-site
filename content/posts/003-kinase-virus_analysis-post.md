---
title: "Mapping Kinases and Viral Drug Connectivity"
date: 2017-01-25T03:38:07+09:00
draft: false
summary: Changing gene expression to beat out viral infections
tags: ['biology']
---

{{< figure src="/images/003-kinase-02.png"  >}} 
_Source: [Maillard Lab](http://maillardlab.org/mechanisms-of-signal-transduction-in-pka/)_  

Kinases are pretty interesting to me. Sure I didn't have the best introduction with them - as with most proteins, they were portrayed in AP Biology as either overly simple cartoon squiggly shapes or hopelessly complex ribbon / space-filling models, playing some large role in cell signaling with an equally large number of chemicals and sub-products to memorize. But over time I was able to see past these offenses to arrive at my current sentiment: kinases are kind of cool. Not only do they phosphorylate proteins, playing a role in regulating most aspects of cell life, but abnormal phosphorylation is often the cause or consequence of disease). Accordingly, they've become an important group of drug targets that I wanted to take a look at.

In an attempt to unearth some computational biology skills, review some recent Pandas exposure, and get back into the spirit of biological research and discovery, I wanted to explore the relationship between kinase differential expression and viral infection. To do so, I ran a general query on the Gene Expression Atlas for all experiments that had to deal with viruses and for genes somehow related to kinases. Following this, the ultimate goal was to use connectivity mapping to find possible drug candidates correlated with a reversion in differential expression.

## Some Background + Motivation  
Recently, one of five 2016 Breakthrough Prizes in the Life Sciences was awarded to Professor Stephen Elledge, who among other incredible things is particularly known for his work in eludicating the human DNA damage response (DDR). Excitingly, this can basically be summarized as a protein kinase cascade, and so one could imagine directing their drug discovery search in regards to diseases that heavily involve DNA damage towards kinase inhibitors or activators. Cancers are probably what come to mind the most, and I had also done some Pandas notebook exploration into that, but many cells also undergo virus infection-associated DDR.  

### Picking the Right Virus Infection Targets  
Another motivating idea is that going after viruses is difficult, particularly because of their rapid mutation cycle frequently rendering drugs obsolete. While we typically think of targeting foreign proteins such as external envelope proteins, another path to take might involve looking elsewhere from the virus entirely, and instead at host targets. While this sounds kind of like targeting your own cells with a therapeutic meant to kill viruses, viral infection might cause the upregulation of certain genes in host cells that allow them to propogate. If we can disrupt these then, the virus has a much harder time of getting by, and can't quite rely on its typical mutation frequency to escape dependency as fast. The idea is that drugs that disrupt host pathways that the virus relies on can't be as easily overcome by the virus through mutation because that would require the virus to evolve an entirely different functionality, which is a much lower probability event then changing a few coat protein residues.

### Even More Motivation  
Along with talking to [Dr. Andrew Taube at DESRES](https://www.deshawresearch.com/people_c-b_taube.html) and learning about their group's work in MD with kinases, phosphatases, and viruses, and having my own probably far-fetched ideas about one day being able to engineer a sort of hyper DDR and immunity against the introduction of viral DNA, I was interested in seeing what I could find through a short exploration with publicly available datasets.

I had also just taken MCB60: Cellular Biology and Molecular Medicine, which involved a lab component exploring DDR in yeast (slides viewable here). Three months of intermittent web lab work is kind of naturally inconclusive, so I was eager to see if I could get some more definite results computationally.

While in the short time putting this together I could only get as far as generating possibly connected drugs that would work towards reversing host cell expression after virus infection, and there's still a ton of analysis to be done with more time, the exercise was pretty fun and interesting. The later parts of the notebook could also definitely be cleaned up. See the [original notebook and text here](https://michaelzhang.xyz/Kinase-Virus_Analysis/).
