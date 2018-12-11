# PRIDE curator pipeline tutorial
					
written by Attila Csordas with edits from Juan Antonio Vizcaino, Tobias Ternent, Gerhard Mayer and Deepti Jaiswal Kundu
Version 0.9.2 (10 Dec 2018)

This document describes the steps regularly happening during the process of generally valid submissions. As such it serves the purpose of providing the basics for new PRIDE curators. For irregularities, common issues and their resolutions please see the other Google Document shared with curators called “Common PRIDE Submission Issues”.


## Table of contents

I. External Documentation
II. Important locations on the EBI filesystem and technical info
III. Google Spreadsheets used for curation work
IV. Software tools
V. Basic concepts
VI. Submission Overview
VII. RT ticket tracking system
VIII. Validation
IX. Submission
X. Submission annotation: dataset tags and country of origin
XI. Post-submission jobs
XII. Publication/reference
XIII. Common submission issues
XIV. Dataset resubmission
XV. Command Line Utilities: FTP and Aspera
XVI: How to create a new ticket 
XVIl. Updating px.xml on PC


:I. External Documentation

ProteomeXchange Submit data page: `http://www.proteomexchange.org/submission`

Submission Tutorial: `http://www.proteomexchange.org/sites/proteomexchange.org/files/documents/px_submission_tutorial.pdf`

Submission Guidelines: `www.ebi.ac.uk/pride/help/archive/submission`

FAQ: www.ebi.ac.uk/pride/help/archive/faq

PRIDE tools and libraries: http://www.ebi.ac.uk/pride/help/tools

Dataset tags: http://www.ebi.ac.uk/pride/help/archive/tags


II. Important locations on the EBI filesystem and technical info

Pipeline script directory:
/nfs/pride/work/archive/filtering_px_submission_pipeline - Main directory where all the submission pipeline scripts are saved and run.

Submission queue directory:
/nfs/pride/web/archive_submission_queue - Directory where all the incoming submission tickets are stored. Basically it generates to user automatically after the submission. A single ticket basically contains the path for the dropbox folder where data are stored immediately after the submission. User’s data will be taken from here for further submission process in PRIDE.
