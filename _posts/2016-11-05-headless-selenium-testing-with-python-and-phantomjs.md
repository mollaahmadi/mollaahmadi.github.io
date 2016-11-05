---
layout: post
title: Headless Selenium Testing With Python and PhantomJS 
description: lxc network
tags: PhantomJS Python Selenium
comments: false
permalink: headless-selenium-testing-with-python-and-phantomjs
sitemap:
  lastmod: 2016-11-05
---
[PhantomJS](http://phantomjs.org/) is one of the best headless Webkits. To install on ubuntu follow these instructions:

* install phantomjs 

```bash
npm install phantomjs
```

* install selenium

```bash
pip install selenium
```

* run a sample

```python
import platform
from selenium import webdriver
from selenium.webdriver.common.keys import Keys

# PhantomJS files have different extensions
# under different operating systems
if platform.system() == 'Windows':
    PHANTOMJS_PATH = './phantomjs.exe'
else:
    PHANTOMJS_PATH = '/usr/local/bin/phantomjs'

driver =webdriver.PhantomJS(PHANTOMJS_PATH)

driver.set_window_size(1120, 550)
driver.get("https://duckduckgo.com/")
driver.find_element_by_id('search_form_input_homepage').send_keys("realpython")
driver.find_element_by_id("search_button_homepage").click()
print (driver.current_url)
driver.quit()
~              

```


