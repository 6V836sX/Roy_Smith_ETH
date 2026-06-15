# ENEL445 Roy Smith Exam Context Map

Purpose: this file is the single entry point for thinking across all Roy Smith exam media together. It connects final notes, transcripts, slides, and exercises by topic.

Use this before deep work:

1. Read `final_notes/roy_smith_optimisation_learning_guide.pdf` or `.qmd` for the organised explanation.
2. Use the table below to jump from topic to Roy transcript, lecture slides, and practice material.
3. Use transcripts only when exact wording or lecture emphasis matters.
4. Use raw `media/` only if transcript context is insufficient.

## Main Outputs

| Role | File |
|---|---|
| Main bilingual guide | `final_notes/roy_smith_optimisation_learning_guide.qmd` |
| Rendered guide | `final_notes/roy_smith_optimisation_learning_guide.pdf` |
| OLS assumptions companion | `final_notes/ols_error_assumptions_big_picture.qmd` |
| Rendered OLS companion | `final_notes/ols_error_assumptions_big_picture.pdf` |
| Editable overview | `chapter_mindmap_markmap.md` |
| Terminology consistency | `terminology.json` |

## Lecture-to-Topic Map

| Exam topic | Transcript | Slides | Main guide anchor |
|---|---|---|---|
| Least squares regression part 1 | `transcribe/20260504_Lecture_6_least_squares_regression_part_1.md` | `Least-Squares Problems and Methods/Lecture 6 Least squares regression part 1.pdf` | least squares, normal equations, geometry |
| Statistical least squares / BLUE | `transcribe/20260505_Lecture_7_least_squares_statistics_BLUE.md` | `Least-Squares Problems and Methods/Lecture 7 Least squares regression part 2.pdf` | estimator, variance, confidence interval, BLUE |
| Regularisation and validation | `transcribe/20260506_Least_squares_regularisation_validation.md` | lecture media/transcript only | Ridge, LASSO, Elastic Net, validation, metric choice |
| Convex sets and functions | `transcribe/20260511_Lecture_8_convex_sets_cones_ellipsoid_method.md` | `Convex Optimisation, LMIs, and MPC/Lecture-8-Convex-optimisation-part-1.pdf` | convex sets, cones, functions, quasi-convexity, ellipsoid method |
| LMI / SDP / control design | `transcribe/20260512_Lecture_9_LMI_SDP_control_design.md` | `Convex Optimisation, LMIs, and MPC/Lecture-9-Convex-optimisation-part-2.pdf` | cone programs, Schur complement, LMI, Lyapunov, congruence |
| Model predictive control | `transcribe/20260513_Lecture_10_model_predictive_control_MPC.md` | `Convex Optimisation, LMIs, and MPC/Lecture-10-Convex-optimisation-part-3-model-predictive-control-(MPC).pdf` | MPC, hard/soft constraints, explicit MPC, KKT |

## Exam Revision Order

1. Least squares as geometry: projection, residual, normal equations.
2. Least squares as statistics: estimator, uncertainty, BLUE, confidence intervals.
3. Regularisation: why penalise, Ridge/LASSO/Elastic Net, validation and metric choice.
4. Convex geometry: hyperplane, halfspace, cone, convex cone, norm cone, PSD cone.
5. Convex functions: vector/matrix notation, norms, quasi-convexity, bisection.
6. Algorithms: ellipsoid method as theory/cutting-plane intuition, not practical first choice.
7. Cone programs and LMIs: LP/QP/SOCP/SDP links, Schur complement, PSD constraints.
8. Control connection: Lyapunov inequality, congruence transformation, MPC formulation.
9. Explicit MPC: KKT, active constraints, piecewise affine controller.

## Practice Material

| Practice type | File | Notes |
|---|---|---|
| Least squares | `exercises/LS_exercises.pdf` | Generally harder than exam; use for formula fluency. |
| Convex optimisation | `exercises/Convex_Opt_exercises.pdf` | Useful for set/function/LMI practice. |
| Statistics | `exercises/Statistics_exercises.pdf` | Use for BLUE, estimator variance, CI background. |
| Exercise note | `exercises/readme.txt` | Exercises may be harder than Roy exam level. |

## How to Ask Future Questions

Best prompt pattern:

> Use `exam_context.md` as the map. Explain [topic] by connecting the guide, transcript, slides, and likely exam style. Keep it bilingual and beginner-friendly.

For exam drill:

> Use `exam_context.md`. Generate 3 exam-style questions on [topic], then solve one step by step.

For weak concept repair:

> Use `exam_context.md`. I do not understand [concept]. Teach it from zero, then connect it to Roy's notation and one exam-style problem.

## Folder Policy

Do not flatten the repo into one physical folder. Keep source types separated:

- `final_notes/`: final study products and render sources.
- `transcribe/`: cleaned text evidence from lectures.
- `Least-Squares Problems and Methods/`: least-squares slides.
- `Convex Optimisation, LMIs, and MPC/`: convex/LMI/MPC slides.
- `exercises/`: practice material.
- `media/`: raw audio/video/subtitles.

The "one folder" effect should come from this index, not from mixing raw files. This preserves traceability and avoids breaking references.
