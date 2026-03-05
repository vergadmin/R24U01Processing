# R24 U01 Data Processing

## Files you will need
### From Qualtrics
You will need to download the following files from Qualtrics, and rename them. *It is important to rename the files EXACTLY as written below or the script won't work!!!*
* U01/R24 Universal Pre-Intervention Survey -> rename to **Prescreener.csv**
* U01 Aim 2 Post-Intervention Survey -> rename to **U01_Post.csv**
* R24 Aim 2 Post-Intervention Survey -> rename to **R24_Post.csv**
* R24/U01 Renumeration Survey -> rename to **Remuneration.csv**
### From Dev Team
These are old logs from a previous database. Ask the dev team for this if you don't have it. This never updates, so once you have it, you won't need to touch it.
* R24_Logs_Old.csv

## File Structure
Once you download this repo, put the **R24_Logs_Old.csv** at the root. Then, create a subfolder under **Data** (you can call it whatever you want, but standard is date of data pull, like **Data/[Date]**). You will need to create an **Outputs** folder (but don't have to do anything with it as outputs will be auto-generated). Here is an example of a working file structure: 
```
Main.ipynb
R24_Logs_Old.csv
Data/pip install
└── R24_Logs_Old.csv
└── March 2 2026/
    ├── Prescreener.csv
    ├── Remuneration.csv
    ├── U01_Post.csv
    └── R24_Post.csv
Outputs/
└── (empty at first, will be auto-generated from script)
```

## Running the Python Script
**Virtual Environment**: It is highly suggested to create some sort of virtual environment. We use [conda](https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html). Here are specific instructions:
1. After installing conda, open a terminal in the root `R24U01Processing` folder.
2. Run the command `conda env create -f environment.yaml`, this creates an environment called `r24u01logs` and installs the dependencies using `pip` to that environment.
3. Run the command `conda activate r24u01logs` to bring your terminal into the virtual environment.

**Jupyter Notebook**: We run the code using [jupyter notebook](https://jupyter.org/install).

**Before you run Main.ipynb**
You will only need one thing from the dev team -- and that is, in the second box, the details for `conn_str`. Reach out to someone from the dev team for this.

**Running Main.ipynb** Run the cells in sequential order. In the first box, it will ask you to put in a folder; here is where you'd put in 'March 2 2026' from the example file structure to get the data for that date. From there on, just run all the cells and it should all do it for you!

## Output
You will end up with the following output. You'll notice a bunch of items are auto-generated. The main interest here is, under **Outputs**, there is a new folder with the date matching the input data. You will find all processed CSV files here.

```
Main.ipynb  
Data/
└── R24_Logs_Old.csv
└── March 2 2026/
    ├── Prescreener.csv
    ├── Remuneration.csv
    ├── U01_Post.csv
    ├── R24_Post.csv
    ├── R24_Logs.csv (auto-generated from script)
    └── U01_Logs.csv (auto-generated from script)
Outputs/
└── March 2 2026 (auto-generated from script)/
    ├── R24_Complete.csv (auto-generated from script)
    ├── R24_Remuneration_With_Duplicates.csv (auto-generated from script)
    ├── R24_Remuneration.csv (auto-generated from script)
    ├── U01_Complete.csv (auto-generated from script)
    ├── U01_Remuneration_With_Duplicates.csv (auto-generated from script)
    ├── U01_Remuneration.csv (auto-generated from script)
    └── Subfiles (auto-generated from script)/
        └── (Subfiles created during data processing for reference)
```

### Notes for Rashi
1. be sure to activate proper conda environment: conda activate r24u01logs
2. run: jupyter notebook
3. install dependencies outside of jupyter notebook by running conda install 
4. put all qualtrics files in Data/[Date]