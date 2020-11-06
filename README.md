# A Gold Standard Methodology for Evaluating Accuracy in Data-To-TextSystems
Supporting materials for INLG2020 paper "A Gold Standard Methodology for Evaluating Accuracy in Data-To-TextSystems".

## What is in this repo
This repository contains:
* The MS Word documents given to our Mechanical Turk workers and returned to us with annotations.  Each of these contains:
  * Our instructions for the workers.
  * A fixed example of annotation.
  * The text which the workers were tasked to annotate, along with their annotations.
  * The workers found a similar volume of texts to each other and demonstrated a high level of agreement.
* The texts we annotated ourselves
  * These are the same texts the workers annotated, we did this as a check to ensure that workers were finding roughly the correct volume of errors.
  * These texts are not part of the experimental results.
* An Excel document containing:
  * The list of all reported errors by any of our workers.  This includes cases where there was disagreement and the file can be filtered on this.
  * The generated texts which we evaluated, along with game and other information for them.  Note that the IDs for these texts are not sequential, i.e. they are not S01 through S21.  The gaps in the numbering are intended and are the result of us initially planning to annotated 30 texts but then dropping 3 from each system before annotation due to time constraints.
  * The demographic information for our three Mechanical Turk workers.
  
## How we recruited and worked with Mechanical Turk workers (Turkers)
It was important to us that we carefully select and engage these workers.  This was both to ensure we recruited the correct people, and also to ensure that we paid them fairly for their time.  The recruitment process was as follows:

After annotating a small number of texts ourselves, we selected one of them as a qualifying text and created a HIT (Mechanical Turk job) for it.  We had found 20 errors in this text after comparing and combining our annotations.  We decided that workers should find at least 70% (14/20) of the errors we did.  In our own pilot annotations we had found that it could take 20-30 minutes to annotate each text.  We therefore decided on a payment to the Turkers of $8 per hit, or approximately $20 per hour.  One of the Turkers commented in free text comments that we were "spot on" with this estimate.  We also paid a $4 one-off bonus for passing the qualification.  We recieved 18 repsonses to our qualification task.

* 10 workers who did supply annotations, we did not pay them.  These 10 were done as a first batch, following this failure we restricted work to "Amazon Masters" workers, from the US, who held a US Bachellors degree.
* 4 workers who supplied annotations but in the 30-60% range.  We paid these workers, and also paid them the bonus as we fel this was fair given it would take a little time to read our instructions, and these workers did try.
* 4 workers who achieved 70% or more, we paid these workers, gave them a bonus, and granted them a custom qualification which we used to restrict our experiment to this group.

Following qualification we offered work to our qualified group were we collected 3 annotated texts for each of the 21 generated texts.  We had offered this to all qualifying workers, it just happened that only 3 of these workers took up the work, each doing all 21 texts.

## Our process on the Mechanical Turk UI
We created a simple web interface where workers could read instructions which directed them to download the appropriate word document (see this repo for those documents).  They then had to upload the document on the form, which sent it to Amazon S3.  They then submitted the hit.  We experienced no problems where our qualified workers could not follow this process.  The only issues we encountered was with out first batch of candidates in the qualification task, who submitted no annotations.  We believe these workers were simply uploading the blank document in the hope we would accidentally pay them.  One of them in fact uploaded a short video clip of a basketball game.  This all stopped when we restricted the work to more qualified workers.

## Total cost and work quality
In total, this experiment cost us approximately £600 / $750 US, with about 80% going to the workers and the remainder being Amazon fees.  The workers appeared happy with out rate, our time estimate, and did good work.  We were initially a little skeptical about the level of work we could expect on this platform but were very happy with the work done.

## Combining the annotations
We went through each generated text, sentence by sentence, looking at annotations from all three workers for that sentence.  We combined these annotations to form our Gold Standard Mistake List (GSML).  Where annotators had marked similar errors but with slightly differing spans of words, we combined them if we felt the annotator was meaning the same thing.  For example if one annotator marked the name error "Hawks" and another marked "the Hawks" we treated this as the same intended error.  Likewise, with "on the road" vs "road" as a word error.  This could be difficult to do for some errors, especially if the number of words highlighted was large.  Any errors which could not be easily combined like this were included seperately and therefore show up in our inter-annotator agreement measures.

A note on the proposed shared task:  We have refined the process slightly for our proposed shared task in this area, based on our experiences here.  Our GSML for the shared task will include token positions for all errors, and we will also have a more clearly defined procedure for when error annoatations can be combined at this stage.  For example we will define operations such as combining errors where the only difference is in the combination of determiners and prepositions included.


