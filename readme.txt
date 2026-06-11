ENEL445 Roy Smith Optimisation Study Pack
========================================

This repo is a study pack for the Roy Smith part of ENEL445 Applied
Engineering Optimisation.  The main topic spine is:

least squares
-> statistical least squares / BLUE
-> regularisation and validation
-> convex optimisation
-> LMIs and SDP
-> model predictive control

The files are organised for revision, not for reading every raw source in
date order.


Recommended reading order
-------------------------

1. Start with the main guide:

   final_notes/roy_smith_optimisation_learning_guide.pdf

   This is the primary output.  It reorganises Roy's lecture material into a
   learning path with explanations, examples, exam traps, and self-check
   questions.

2. Use the companion note when the least-squares assumptions feel unclear:

   final_notes/ols_error_assumptions_big_picture.pdf

   This note focuses on OLS error assumptions, estimator uncertainty, and the
   difference between model error, measurement noise, bias, variance, and MSE.

3. Use the mindmap for navigation:

   chapter_mindmap_markmap.md

   Open this in VS Code with a Markdown/Markmap preview if you want an editable
   overview of the chapter structure.

4. Only then go back to the transcripts if you need Roy's exact wording:

   transcribe/

   The transcripts are useful for checking context, but they are not the best
   first-pass study material.


Main deliverables
-----------------

final_notes/roy_smith_optimisation_learning_guide.qmd
    Source file for the main learning guide.

final_notes/roy_smith_optimisation_learning_guide.pdf
    Rendered main guide.  Read this first.

final_notes/ols_error_assumptions_big_picture.qmd
    Source file for the OLS assumptions companion note.

final_notes/ols_error_assumptions_big_picture.pdf
    Rendered companion note.

chapter_mindmap_markmap.md
    Editable mindmap-style overview.


Source and support folders
--------------------------

Least-Squares Problems and Methods/
    Lecture slides for the least-squares part.

Convex Optimisation, LMIs, and MPC/
    Lecture slides for convex optimisation, LMIs, SDP, and MPC.

transcribe/
    Cleaned lecture transcripts:

    20260504_Lecture_6_least_squares_regression_part_1.md
    20260505_Lecture_7_least_squares_statistics_BLUE.md
    20260506_Least_squares_regularisation_validation.md
    20260511_Lecture_8_convex_sets_cones_ellipsoid_method.md
    20260512_Lecture_9_LMI_SDP_control_design.md
    20260513_Lecture_10_model_predictive_control_MPC.md

exercises/
    Exercise material and local notes.

media/
    Raw media files.  These are support material, not the main revision output.

terminology.json
    Terminology mapping used to keep technical translations consistent.

transcription_prompt.md
    Prompt and terminology guidance for transcript cleanup.

mindmap_prompt.md
    Prompt guidance for creating or revising the chapter mindmap.

review_flow_prompt.md
    Local workflow note for building the study pack.


How to rebuild the PDFs
-----------------------

From the repo root, run:

    quarto render final_notes/roy_smith_optimisation_learning_guide.qmd

and, if needed:

    quarto render final_notes/ols_error_assumptions_big_picture.qmd

The project currently uses Quarto with XeLaTeX and the ctexart document class,
so Chinese text should render correctly if the local TeX environment is set up.


Study advice
------------

Do not treat regularisation, BLUE, validation, and MSE as isolated formulas.
Read them as one engineering workflow:

1. Build a meaningful Phi from system understanding, variables, and
   observations.
2. Check whether Phi has rank, conditioning, scaling, and coverage problems.
3. Ask what the estimation goal is: scientific explanation, inference,
   prediction, safety, or variable selection.
4. Choose the metric and estimator to match that goal.
5. Use validation or cross-validation when the tuning choice cannot be made
   from theory alone.

Important intuition:

Regularisation is not a substitute for a better Phi.  Better variables,
better experiment design, better measurement coverage, and better physical
understanding come first.  Regularisation stabilises estimation when the
available Phi is still noisy, ill-conditioned, underdetermined, or too flexible.


Scope note
----------

This repo is focused on Roy Smith's ENEL445 optimisation block.  Material from
other lecturers or non-exam enrichment topics should not be mixed into the main
guide unless it directly supports this scope.
