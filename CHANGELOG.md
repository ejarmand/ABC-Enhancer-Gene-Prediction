# Changelog
## [Unreleased]
- Include cell type tss selection as part of ABC / include it as an option
- Include documentation for `--score_column powerlaw.Score` for predictions that do not use HiC
- Look into how ABC Score is calculated for alt_tss and see if anything needs to be changed.

## [0.2.0] - 2021-10-10

Many changes. Introduced multiple features to improve speed and functionality of ABC code. 

### Added
- in src/predict.py, added `--include_self_promoters` to include self promoters in the output file (i.e EnhancerPredictionsFull.txt)
- both makeCandidateRegions.py and run.neighborhoods.py can now take in multiple DHS, H3K27ac files 
- Added alternative TSS code to pick celltype specific TSS 
- Introduced snakemake wrapper for downloading and processing input files from ENCODE and to fully run ABC code
- Introduced `Snakefiles/workflow/scripts/metrics.py` script to automatically calculate metrics from predictions file 
- Introduced `Snakefiles/workflow/scripts/getVariantOverlap.py` script to generate prediction file for downstream variant overlap analysis
- Introduced .yml files for calling macs2 peaks and running ABC code
- Added hg38 resource files and documentation for running altTSS

### Changed
- Modified `make_predictions` function in Snakefiles/workflow/scripts/predictor.py to improve speed of calculating predictions
- Introduced pyranges as a way to perform intersections to improve speed of calculating predictions
- If multiple DHS, H3K27ac files are introduced, code will take the average counts of the multiple input files
- To allow for multiple TSS, adjusted `--fail_on_nonunique==False` flag in `process_gene_bed` function in Snakefiles/workflow/scripts/neighborhoods.py 
- Updated `Snakefiles/workflow/scripts/getGenomeTSS.py` code for speed up + annotations updated to use gencode v26 annotations as INPUT

## [0.1.0]
### Added
- First version of ABC Code from the ABC Paper released

--- 
The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).
