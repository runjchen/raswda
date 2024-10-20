# Processing textgrids with python

## Textgrid Packages
There are a few different options available for python packages that process textgrids:
- textgrid: https://github.com/kylebgorman/textgrid
- TextGridTools: https://github.com/hbuschme/TextGridTools
- praat-textgrids: https://pypi.org/project/praat-textgrids/
- praatIO: https://github.com/timmahrt/praatIO

We use **praatIO**, which has the best documentation.

## Goal
We would like to automate the process of an initial check of textgrid alignment for the following:
- Are the Token (transcript) and DA tiers aligned?
- Any empty intervals?
- Any incorrect DA tags?


For the minor misaligned interval boundaries, we can automate the snapping process.

`from praatio.praatio_scripts import alignBoundariesAcrossTiers`

`tg_aligned = alignBoundariesAcrossTiers(tg, "Token", maxDifference=0.005)`

## Other potential usage:

Q: How do I shift all the timestamps by 5s?

A: `[TIER_OBJECT_NAME].editTimestamps(offset=5)`
https://github.com/timmahrt/praatIO/blob/9e01fdc4240524f70c1025a84625ae777474d989/praatio/data_classes/interval_tier.py#L240


Q: How do I spellcheck the transcript: 

A: Use `spellCheckEntries` + any custom spell check function on the word level:
https://github.com/timmahrt/praatIO/blob/9e01fdc4240524f70c1025a84625ae777474d989/praatio/praatio_scripts.py#L142

`from praatio.praatio_scripts import spellCheckEntries`

`tg_errors = spellCheckEntries(tg, "DA", "DA_errors", check_func)`
