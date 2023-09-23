# undetectable-scrapy-selenium

Scrapy middleware to handle javascript pages using undetectable-selenium.

## Installation
```
$ pip3 install git+https://github.com/ProlorenzoAndrii/undetectable-scrapy-selenium.git
```

## Usage
Use the `SeleniumRequestUc` instead of the scrapy built-in `Request` like below:
```python
import scrapy


from scrapy_selenium_ud import SeleniumRequestUc


class TestUcSpider(scrapy.Spider):
    version = 3
    name = "test_uc"

    custom_settings = {
        "DOWNLOADER_MIDDLEWARES": {
            "scrapy_selenium_ud.middlewares.SeleniumUcMiddleware": 900,
        },
    }

    def start_requests(self):
        url = f"https://www.elcorteingles.es/electronica/A40408610-auriculares-samsung-galaxy-buds-2-blancos/?parentCategoryId=999.26048525013"
        yield SeleniumRequestUc(url=url, callback=self.parse)


    def parse(self, response, **kwargs):
        ...
```
