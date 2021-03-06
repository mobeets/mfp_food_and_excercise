A simple scraper for a user's Food and Exercise diary offered by MyFitnessPal.com.

Requirements: `pip install scrapy`

### Usage

```bash
mkdir output
cd mfp_food_and_excercise
USERNAME=your_fitnesspal_username
PASSWORD=your_fitnesspal_password
DATE='2016-05-21'
scrapy crawl -a username=$USERNAME -a password=$PASSWORD -a target_date=$DATE --nolog mfp
```

You can also add in a start date to grab all logs between the start date and the target date:

```bash
START_DATE='2016-05-01'
scrapy crawl -a username=$USERNAME -a password=$PASSWORD -a target_date=$DATE -a start_date=$START_DATE --nolog mfp
```

### Output

This will create files in the `output/` directory that look like this:

````
YYYY-MM-DD-excercise.csv
YYYY-MM-DD-food.csv
````

Columns in these tables are delimited with tabs.
Some of the rows in the food csvs will be meal names such as "BREAKFAST", "LUNCH", etc.
You can parse (and remove) these rows, as well as combine files across multiple dates, using the `combine.py` helper script:

```python
python combine.py output
```

This source is released to the Public Domain, do with it as you will (but please be nice to MFP in terms of rates). 
