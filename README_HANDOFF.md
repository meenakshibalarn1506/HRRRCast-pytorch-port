\# HRRRCast — PyTorch Port Progress and Handoff



\## 1. Project Overview



HRRRCast is a high-resolution weather forecasting system using HRRR (High-Resolution Rapid Refresh) and GFS (Global Forecast System) data. This repository contains the existing TensorFlow/Keras workflow and a PyTorch implementation intended to support model inference and forecast generation.



\*\*Current handoff status:\*\* Implementation files are present. PyTorch weight conversion, numerical parity validation, and a complete end-to-end PyTorch forecast have not yet been verified in the current environment.



\## 2. Existing TensorFlow/Keras Workflow



The repository contains the original model artifact and supporting forecasting code.



Key artifacts include:



\- `net-diffusion/model.keras` — existing Keras model artifact.

\- `net-diffusion/model\_fixed.keras` — repaired model artifact created during model inspection and repair work.

\- `net-diffusion/model\_original.keras` — preserved original model artifact.

\- `net-diffusion/normalize-stats.nc` — normalization statistics.

\- `src/fcst.py` — existing forecast workflow entry point.

\- `src/compute\_pmm.py` — supporting forecast computation code.



These files indicate existing model and pipeline work. The repaired model's numerical correctness and operational forecast performance still require verification.



\## 3. PyTorch Implementation



The `src\_torch/` directory contains the following modules:



| File | Purpose |

|---|---|

| `model.py` | PyTorch model architecture |

| `convert.py` | Model-weight conversion utilities |

| `inference.py` | Model loading and inference routines |

| `diffusion.py` | Diffusion sampling utilities |

| `rollout.py` | Forecast rollout logic |

| `validate.py` | Numerical validation and comparison harness |

| `output.py` | Forecast output handling |

| `variables.py` | Variable definitions and related metadata |

| `config.py` | Configuration and path settings |

| `cli.py` | Command-line interface |

| `profiling.py` | Performance profiling utilities |



The presence of these modules documents the implementation structure; it does not, by itself, establish successful execution or equivalence with TensorFlow.



\## 4. Intended Execution Workflow



The intended PyTorch workflow is:



1\. Inspect the source Keras model and its saved weights.

2\. Convert the model weights to the PyTorch architecture.

3\. Load the converted state dictionary.

4\. Run numerical parity tests against suitable TensorFlow reference outputs.

5\. Execute the PyTorch inference and forecast rollout.

6\. Inspect generated forecast files and visualizations.



The precise commands and required input artifacts must be confirmed against the current implementation and configuration before execution.



\## 5. Verification Status



| Check | Status |

|---|---|

| Existing Keras model artifacts present | Confirmed by directory inspection |

| PyTorch source modules present | Confirmed by directory inspection |

| PyTorch available in active `hrrrcast` environment | Not available at initial inspection |

| Converted PyTorch state dictionary generated and checked | Not yet verified |

| TensorFlow-to-PyTorch numerical parity | Not run |

| End-to-end PyTorch forecast | Not yet verified |

| Forecast output inspection | Pending |

| Reproducible environment setup | Pending |



No numerical accuracy, parity, or forecast-performance claims are made at this stage.



\## 6. Known Risks and Next Steps



\- Resolve a compatible PyTorch environment without disrupting the existing TensorFlow workflow.

\- Inspect the converter's expected inputs, output paths, and command-line options.

\- Confirm that the source model's layers and weights map correctly to the PyTorch architecture.

\- Generate or locate the TensorFlow reference tensors required for validation.

\- Run the numerical comparison and record the actual error metrics and pass/fail result.

\- Execute a small, controlled end-to-end forecast before attempting larger production runs.

\- Record dependencies, commands, input data requirements, outputs, and any unresolved limitations.



\## 7. Repository and Handoff Notes



The working tree contains existing modified and untracked files related to model repair and inspection. These should be reviewed and preserved deliberately; generated model artifacts and large data files should not be committed indiscriminately.



This document records the status observed during the current handoff preparation. Update the verification table only when the corresponding check has actually been executed and its result recorded.



