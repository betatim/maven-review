# The Maven Review

Here we propose an updated methodology of a 2-tiered collaborative review process of scientific analyses for large collaborations, such as LHCb. The proposal is based on the [current model used by LHCb](http://lhcb.web.cern.ch/lhcb/lhcb_page/collaboration/organization/editorial_board/Publication_Procedure-Sept2011.pdf) and aims at improving in several points.

## The aim of the proposal
We try to adress three issues that are recurring problems within the current review process:

1. Feedback on the strategy and technique of the analysis has to be made available to the analysts as early as possible. Few things are as wasteful and frustrating as when someone works for quite some time on a project but gets feedback that requires substantial changes only once the analysis is finished and thought to be ready to be published. 
2. Currently the only basis for a review is the analysis note. The actual tools to obtain the results are largely absent from the discussion. This makes it very hard to ensure the reproducibility of the result and the sustainability and relevance of the work invested for future projects. 
3. To make best use of the limited available resources, feedback has to be well structured. In most cases it is straight forward to request a large number of cross checks and systematic studies. It is less obvious how the available time is spent most usfully. There are two issues connected to this: the ability of the reviewers to ask the right questions, based on the material presented to them; and the priorisation of tasks, possibly requiring triage if the collaboration wants to hit a particular deadline.

The proposal presented here adresses all of these issues while preserving the essential and valuable features of the present review process, in particular the requirement that an analysis is reviewed by independent minds. In fact most actions proposed -- with one exception -- do not touch on the content of the current publication procedure. Instead we try to flesh out some crucial details of the early stages of the review process in the working groups.

## A few simple tools
To attack the problems stated above we propose to adopt the following tools as part of the review process:

### Maven reviewers
On the working group level, **as soon as an analysis is proposed**, a working group reviewer is assigned. They should be experienced in the respective kind of analysis and take the role of a [maven reviewer] [1]. A maven reviewer accompanies and counsels the analysts during the whole analysis. His first responsibility is to help the analysis team achieve the highest possible physics goals in the limitations of the available resources. His second responsibility is to make sure that the analysis is carried out according to adequat technical standards by making detailed feedback available as early as possible. The main tools that helps him achieve this are the analysis backlog and the code review discussed below.
A maven reviewer does not engage in the day-to-day business of implementing the analyis but is available for questions and clarifications. He meets regularly (biweekly) with the analysis team, outside of the working group meetings, to discuss the progress of the analysis.
The maven reviewer clears an analysis for working group approval once all "must have" items on the analysis backlog are completed.

Due to the intense involvement such an interpretation of the role of working group reviewer is in conflict with the requirement to have the analysis checked by a independent minds. However, this check is already covered by the collaboration reviewers. 

### Analysis backlog
A backlog is nothing else than a ToDo list with prioritised items. The backlog should be easily accessible to the analysis team and the working group. There are a few rules that have been proven to be useful when working with such a backlog:

* Items on the backlog should be described as clearly and as specifically as possible. Larger items may be needed to be broken down into several chunks.
* Only the analysts themselves choose what they want to pick from the backlog to work on next.
* The maven reviewer is responsible to always have a clear order of priority of all the items in the list. Only he can remove items from the list or demote them to lower priorities. He assists the analysis team in the decision what to spend their time on. 
* Every working group member (in the later stages every member of the collaboration) can add items to the list. The maven reviewer has the last word on assigning priorities.
* The maven reviewer has the last word on when they consider an item done. In that case the item is clearly marked as done.

### Code review
In our view a data analysis consists of the following artefacts
* The input data as delivered by the experiment;
* The computer programs encoding the full analysis algorithm;
* The analysis note that explains, documents and justifies the applied techniques;
* The paper that summarises the analysis algorithm and presents the physics results obtained by applying it to the input data;

The actual work delivered as the outcome of a typical analysis project are the code, the note and the paper. While the note and the paper are crucial documentations, the code is the actual tool to perform the study. As such it in itselve often represents a substantial investemnt of time and effort. Furthermore the code contains the most precise (but not most readable) documentation of what has actually been done. It should be reviewed on equal footing with the ANA note and the paper. Given the nature of code the focus of such a review will be different than a paper-review.

The basic necessity to enable code review is that **the complete analysis code is made available to the collaboration**. This is also the only requirment that should be formalised in the review process. Hosting the code on a repository sevice such as http://gitlab.cern.ch will be the most practical solution.

The maven reviewer checks that the code is made available, is complete and documented well enough such that the analysis can (at least in principle) be rerun by any member of the collaboration.

This last statement has some implications on how analyses are implemented. All of these implications are desired and encouraged by the design of this review process. 

1. The analysis code has to be complete and automatic. The complete recipe, including all the systematic checks has to be made available. It will be convenient to write down this recipe in machine-executable form. This implies that all plots and numbers have to be generated in a scripted manner.
2. The code has to be documented well enough that a skilled person can install and run it. Ideally with the help of a self-executing analysis recipe.
3. All dependencies of the code are well documented. It is known that some of the programs in use are highly specialised and might require special hardware (such as a GPU cluster) to run in a finite time. In that case the dependencies have to be explained well enough that a reproduction is in principle possible. This might require giving the maven reviewer access to specialised computing hardware.
4. It will be convenient, but not necessary, to make intermediate results (ntuples, results of expensive fits,...) available and to finely subdivide the analysis workflow such that a user can rerun only those parts which interest them.

The analysis code repsoitory should be made available as soon as the project starts. Ideally the maven reviewer can run the current state of the analysis for himself as a preparation for the regular (biweekly) meetings with the analysis team.
 
The complete working group is invited to contribute improvements to the analysis code. It is the decision of the analysis team wether to accept these contributions. A well tested workflow for this can be found [here](https://gitlab.cern.ch/help/workflow/forking_workflow.md).

Requests for improvements to the code can be put onto the analysis backlog. But the analysis should only be delayed by this if either a bug causes wrong results or if the public code is in an incomplete state that does not allow it to be reused.




[1] : the term `maven` comes from Hebrew, loosely translated to "one who understands". There is no particular significance attached to the expression. You can substitute it with "mentor", "senpai", or just "working group reviewer"


