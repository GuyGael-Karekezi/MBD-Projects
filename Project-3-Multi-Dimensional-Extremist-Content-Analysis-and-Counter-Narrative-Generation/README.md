# Project 3 README

## Team
- Lynne Chepkwony (`lchepkwo`)
- Mohammed Abubakari Sadic (`abubakam`)
- Emile Lucky Muhigira (`emuhigir`)
- Ishimwe Karekezi Guy Gael (`iguygael`)

## Main Notebook
- `MBD_Project_3.ipynb`

This notebook is designed to run in **Google Colab**.

## Colab Secrets Required
Before running the notebook, add these keys in **Colab Secrets**:
- `CMU_API_KEY`
- `KAGGLE_USERNAME`
- `KAGGLE_KEY`

These are required because:
- the notebook downloads the Kaggle dataset directly inside Colab
- the notebook uses the CMU AI Gateway for LLM calls

## Important Manual File Requirement
The notebook requires the completed human annotation file:
- `mbd_annotation_filled_30.csv`

This file is manually created by the team after filling in the annotation sample. If it is missing, the annotation-analysis cells will fail with `FileNotFoundError`.

## Expected Files for a Smooth Run
For the fastest and most reliable execution in Colab, upload the notebook together with these files:
- `mbd_annotation_sample_30.csv`
- `mbd_annotation_filled_30.csv`
- `errors_validation_10.csv`
- `classified_pool_progress.csv`
- `ve_nve_classifications.csv`
- `all_severity_results.csv`
- `condition1_temp1_both_prompts.csv`
- `condition2_temp04_both_prompts.csv`
- `task1_counter_narratives.csv`
- `task2_counter_narratives.csv`
- `all_counter_narratives_with_scores.csv`

If these CSV files are uploaded before running the notebook, the professor can skip expensive regeneration and use the saved outputs directly.

## Quick Run / Resume Files
These files are especially helpful for quick reruns:
- `classified_pool_progress.csv`
  Purpose: resumes Part A candidate classification
- `all_severity_results.csv`
  Purpose: skips recomputing Part B severity results
- `condition1_temp1_both_prompts.csv`
  Purpose: preserves Part B condition 1 outputs
- `condition2_temp04_both_prompts.csv`
  Purpose: preserves Part B condition 2 outputs
- `task1_counter_narratives.csv`
  Purpose: skips regenerating Part C Task 1 outputs
- `task2_counter_narratives.csv`
  Purpose: skips regenerating Part C Task 2 outputs
- `all_counter_narratives_with_scores.csv`
  Purpose: skips rerunning LLM clarity scoring
- `ve_nve_classifications.csv`
  Purpose: preserves the final Part A balanced classification file

## Full Run Instructions
1. Open `MBD_Project_3.ipynb` in Google Colab.
2. Add Colab Secrets:
   - `CMU_API_KEY`
   - `KAGGLE_USERNAME`
   - `KAGGLE_KEY`
3. Upload `mbd_annotation_filled_30.csv` if it is not already present.
4. Optionally upload the saved CSV files listed above for a faster run.
5. Run the notebook from top to bottom.

## Notes
- The notebook was updated so it no longer depends on personal Google Drive paths.
- Intermediate and output files are saved locally in the Colab runtime.
- Some old output cells may still display historical Colab paths from earlier runs, but the active code now uses local runtime files.

## Deliverables
Primary deliverables for Project 3 include:
- `MBD_Project_3.ipynb`
- `ve_nve_classifications.csv`
- required analysis CSV files
- this README / write-up
