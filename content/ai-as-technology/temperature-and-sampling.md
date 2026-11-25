+++
date = '2026-11-22T21:20:44+11:00'
draft = false
title = 'Temperature and Sampling'
+++

A model predicts one token at a time, and each token is a probability spread over many possible tokens. Temperature and sampling decide how the next token is picked from the spread.  

1. A model gives probability for every possible next token. It does not output one word. For the next tojen it produces ranked spread, for example

cut off 55%
vendor 25%
network 15%
unknown 5%

2. Sampling picks one token from the spread. The tool rolls a weighted die. A 55% is chosen about 55 times in 100 runs, not everytime

3. Temperature reshapes the spread before the roll.
    Low temperature makes the most likely token much more dominant. 
    High temperature flattens the spread so unlikely tokens get picked more often
    At temperature 0, the tool always takes the top token

Once a token is different, the rest of the answer can change too.


Pitfalls
- Temperature 0 does not gurantee the same answer everytime.
Serving infrastructure, batching, and model updates can still change the output slightly. Treat low temperature as "less variation", not "fixed" answer.
- Many chat tools don't let set temperature at all. Some newer models also ignore it. CHeck settings and API documentation, before you rely on it.

# Example

The model is writing the next word.

Root cause is....

Next Token
cutoff 55%
vendor 25%
network 15%
unknown 5%

Temperature changes the spread. the data below raises each probability to power 1/T and then rescales the four values so they add to 100%. Read it as a rule of thumb, not standard you need to calculate:

Next token|Temperature 0.5 (sharper)| Temperature 1 (as above) | Temperature 2 (flatter)      
|:-------:|:-----------------------:|:------------------------:|:-----------------------:
cutoff    |about 78%                |55 %                      |about 40%
vendor|about 16%|25%|about 27%
network|about6%|15%|about 21%
unknown|about 1%|5%|about 12%

What this means?
- At temperature 0.5, "cutoff" wins about 78 times in 100 runs. Answers are more alike
- At temperature 2, "unknown" gets picked up 12 times in 100. Answers vary more, and some drift into weaker or odd phrasing
- At temperature 0, "cutoff" wins verytime. The anser is repeatable, but it is still only ,ost likely guess, not a checked fact. 

### Takeaway
Temperature changes how spread out the models choices are, not weather its true. For analysis, use low randomness and still check every claim against the source.