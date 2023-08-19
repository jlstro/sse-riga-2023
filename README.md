# 2023 SSE Riga Summer School

Training files and command line cheat sheet for Summer School at SSE Riga 2023

## Cheat Sheet

### Basic commands and symbols

| Command | Function |
| ----------- | ----------- |
| ls | list files and directories |
| cat | show file content |
| less | show file content page by page |
| pwd |  print working directory |
| mkdir | make directory |
| touch | make file |
| cd | change directory |
| rm | remove |
| find | find files or directories |
| clear | clear screen |
| / | the root directory |
| . | your current directory |
| ~ | your home directory |
| &#124; | chain commands together |
| > | redirect input |
| TAB | autocomplete! |
| CTRL+C | cancel command |

### Examples
### Examples
```bash
# List directory content with details
ls -lha

# Find all pdf files in the current directory and all subdirectories
find . -name "*.pdf"

# Navigate to your home directory
cd ~

# Create a new directory named "reports"
mkdir reports

# Create an empty text file named "notes.txt"
touch notes.txt

# Remove a file named "obsolete.txt"
rm obsolete.txt

# Remove a directory and its contents recursively
rm -r directory_to_remove

# Find all files modified within the last 7 days
find . -type f -mtime -7

# Search for a specific file by name
find /path/to/search -name "target_file.txt"

# Use the pipe symbol to chain commands: list files, then show their contents
ls | cat

# Autocomplete filenames by pressing TAB
ls doc[TAB]

# Redirect command output to a file
ls > file_list.txt 
```

### Installing things
```bash
# on MacOS:
brew install wget
brew install ocrmypdf
pip3 install csvkit

# For some programs:
pip3 install PACKAGE_NAME

# on Debian/Ubuntu (Linux)

apt install wget
pip3 install ocrmypdf
pip3 install csvkit

```

### Downloading files
```bash
wget --version
wget --help

wget https://github.com/jlstro/sse-riga-2023/blob/main/commanlinetraining.zip 

# Navigate to ./commanlinetraining/WGET - then type:
wget -i links.txt

```
#### Other uses of wget
```bash
# download all files of specific types from a server
wget -r -A jpg,jpeg,png,gif https://example.com/images/

# throttle download speed
wget --limit-rate=500k https://example.com/large_file.zip

# continue a download
wget -c https://example.com/big_data.zip

# And more - see wget --help

```

### OCR'ing PDFs
```bash
# example command
ocrmypdf supreme_court_no_ocr.pdf supreme_court_with_ocr.pdf

# combine find and ocrmypdf
find . -name '*.pdf' -execdir ocrmypdf {} ocr_{} \;

# Extract text from a PDF and create a searchable PDF
ocrmypdf input.pdf output.pdf

# Perform OCR in English and German languages
ocrmypdf -l eng+deu input.pdf output.pdf

# Deskew an image before performing OCR
ocrmypdf --deskew input.png output.pdf

# Rotate pages and output as PDF
ocrmypdf --rotate-pages --output-type pdf input.png output.pdf

# Force OCR even if a text layer exists
ocrmypdf --force-ocr input.pdf output.pdf
```

## Taming CSV files

```bash
# Navigate to the CSV folder
csvlook Chicago_Crime_2021.csv

csvlook Chicago_Crime_2021.csv | less

csvcut -c date,primary_type,location Chicago_Crime_2021.csv | less


```

| Command | Function |
| ----------- | ----------- |
| csvlook data.csv | Display a CSV file in a table |
| csvcut -c column1,column2 data.csv | Select specific columns |
| csvsort -c column data.csv | Sort a CSV file by a column |
| csvfilter -c column -m value data.csv | Filter rows based on a condition |
| csvjoin -c column data1.csv data2.csv | Join two CSV files |
| csvstat data.csv | Display summary statistics |
| csvformat -D "|" data.csv | Convert CSV to another delimiter |

### Examples
```bash
# Display a CSV file in a tabular format
csvlook data.csv

# Select specific columns from a CSV file
csvcut -c column1,column2 data.csv

# Sort a CSV file by a specific column
csvsort -c column data.csv

# Filter rows based on a specific condition
csvfilter -c column -m value data.csv

# Join two CSV files based on a common column
csvjoin -c column data1.csv data2.csv

# Display summary statistics of a CSV file
csvstat data.csv

# Convert CSV to another delimiter (e.g., pipe "|")
csvformat -D "|" data.csv
```