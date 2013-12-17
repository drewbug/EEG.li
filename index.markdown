---
layout: default
title: "Electroencephalography: An Amateur Scientist's Guide"
---

{{ page.title }}
================

> <q>As they could not reach me, they resolved to punish my body</q><br>
> &ndash;Henry David Thoreau, on being jailed

Now is the autodidact's golden age. The Internet puts a wealth of near-instant knowledge at our fingertips, and the state-of-the-art of yesteryear is now affordable for lone individuals.

For less than €100, you can join the quest to unravel the mysteries of the universe.

Electroencephalography (EEG) is the recording of electrical current passing through neurons. This allows for measuring brain activity as it unfolds.

For most of human history, our only way of communicating with the outside world was with muscle movements. In the past century, this has changed. With EEG, paralyzed people are [communicating with the world around them](http://www.medscape.com/viewarticle/496019), and even [walking around in it](http://neurogadget.com/2013/03/13/mindwalker-exoskeleton-uses-eeg-cap-to-help-disabled-people-walk-again/7532).

A common sentiment among sufferers of epilepsy is that the constant worry that comes from not knowing _when_ a seizure will strike is as bad as, if not worse than, the seizures themselves. [The ability to predict a seizure before it happens](https://en.wikipedia.org/wiki/Seizure_prediction) is made possible by EEG, and for many patients, including those who are not responsive to anticonvulsant medications, this could be a godsend.

Many of the cognitive algorithms our brains use are not be able to be perceived consciously. [Using EEG (and other technologies), we can watch our brains at work](http://lesswrong.com/lw/j2p/research_on_unconscious_visual_processing/). Reverse engineering is the only way we are going to obtain the blueprints of the mind, and EEG just might be the best gross level analysis tool at our disposal.

Hardware
--------

The current state of consumer EEG hardware is very friendly to the citizen scientist.

On the asbsolute lowest end of the price scale, I know of at least one inexpensive [toy](http://frontiernerds.com/brain-hack) that can be repurposed as passable equipment. However, I'm of the opinion that the best wallet-friendly option is the [Olimex EEG-SMT](https://www.olimex.com/Products/EEG/OpenEEG/EEG-SMT/), which comes pre-assembled and requires no prior electronics experience. For more possibilites, see [**EEG hardware possibilities for research**](http://openvibe.inria.fr/forum/viewtopic.php?t=526#p3251).

One thing that is important to keep in mind is that some manufacturers design their equipment to offer only preprocessed data, rather than the raw EEG stream that you want. The canonical example of this is Emotiv, who deliberately crippled their EPOC device in a scheme aimed at making more money through the sale of their "Research Edition" SDK. Luckily, [keeping a determined hacker down is not an easy task](http://daeken.com/2010-09-13_Emokit__Hacking_the_Emotiv_EPOC_Brain-Computer_Interface.html), and open-source software has been written that subverts the restrictions.

Software
--------

For purposes of acheiving interoperability between various software components, it is useful to make a distinction between the acquisition and the processing of EEG data. One extremely helpful tool for this is the FieldTrip Buffer, created by the great people over at the [Donders Institute for Brain, Cognition and Behaviour](http://fieldtrip.fcdonders.nl/). In their own words:

> <q>The FieldTrip buffer is used to communicate between separate application programs. One application program is responsible for the acquisition of the data, and it will write the data (and optionally also trigger events) to the buffer. Other application programs can connect to read the data and the events from the buffer and optionally also write new events (e.g. as output of some BCI classification algorithm) to the buffer.</q>

The FieldTrip Buffer is cross-platform, open-source, actively maintained, language-agnostic, and easy to use. For a quick demonstration of how it works, see [**How should I get started with the FieldTrip realtime buffer?**](http://fieldtrip.fcdonders.nl/faq/how_should_i_get_started_with_the_fieldtrip_realtime_buffer). 

### Acquisition

There are different possibilities for streaming data from your hardware into the FieldTrip Buffer. As an example, users of the Olimex EEG-SMT can use [modeeg2ft](http://fieldtrip.googlecode.com/svn/trunk/realtime/src/acquisition/modeeg/modeeg2ft.cc). For more implementations, see [**Implementations for aquisition systems**](http://fieldtrip.fcdonders.nl/development/realtime/implementation#implementations_for_aquisition_systems).

If nobody has programmed an aquisition system for your hardware yet, do not fret. Writing to a FieldTrip Buffer is a lot easier than it may sound.
