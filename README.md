# Thinkful

Web scraping project from Thinkful Data Science bootcamp - scraping Ford Mustang vehicle information.

## Overview

This project demonstrates web scraping techniques using Selenium to extract vehicle data from Ford's website. It was created as part of the Thinkful Data Science curriculum to practice:

- Web scraping with Selenium
- Data extraction and parsing
- Pandas DataFrame manipulation
- Handling missing data

## Features

- **Selenium Web Scraping** - Automated browser to extract vehicle listings
- **Data Parsing** - Extract year, model, price, MPG, and lease information
- **Error Handling** - Gracefully handles missing data fields
- **Data Cleaning** - Removes non-ASCII characters and formats data

## Data Extracted

| Field | Description |
|-------|-------------|
| `year` | Vehicle model year |
| `car_name` | Model name (e.g., "Mustang EcoBoost") |
| `price` | MSRP starting price |
| `city_mpg` | City fuel economy |
| `hwy_mpg` | Highway fuel economy |
| `lease_mo` | Monthly lease amount |

## Setup

### Prerequisites

- Python 3.x
- Chrome browser

### Installation

```bash
pip install pandas numpy selenium
```

## Usage

```python
from selenium import webdriver

# Launch browser
driver = webdriver.Chrome()
driver.get("https://www.ford.com/cars/mustang/models/")

# Extract vehicle tiles
cars = driver.find_elements(by='xpath', value="//div[@class='vehicleTile section']")

# Parse each vehicle's information
for car in cars:
    info = car.text.split("\n")
    year = info[0][0:4]
    model = info[0][4:].strip()
    # ... extract other fields
```

## Output

Creates a pandas DataFrame with all extracted vehicle information:

```
   year          car_name  price city_mpg hwy_mpg lease_mo
0  2024  Mustang EcoBoost  32515       22      33      299
1  2024       Mustang GT   44090       15      24      449
...
```

## License

MIT

