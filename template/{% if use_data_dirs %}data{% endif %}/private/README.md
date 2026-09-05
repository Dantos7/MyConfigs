# 🚫 data/private

Keep here documents and files that should remain private. No tracking method at all is used here.

## Structure

- `raw/`: Keep raw data files here. These files are never modified once placed here.
- `interim/` (optional): Keep intermediate data files here. These files are generated from raw data through some initial processing steps. Can be used as a base for further automated processing when the initial processing is expensive and it is desirable to not repeat it often.
- `processed/`: Keep processed data files here. These files are generated from raw data through a automated pipeline.
