---
layout: post
title: "A Better Way To Read The News"
subtitle : "Solving my problem of spending too much time reading the news by building my own scraper."
date: 2025-05-24
project : 
    title : "Mini-Projects"
    description : "Small personal projects."
    color : "oklch(67.3% 0.182 276.935)"
categories: 
    - News
    - Python
    - AI
    - Generative AI
---

### The Problem
The internet has significantly changed how we consume media. News organizations have realized that they can now reach a global audience and have capitalized on it by expanding their digital presence and publishing stories for a wide, international audience. However, for the average reader, this has resulted in an overload of information. I often get news about the local politics of foreign countries that have little to no impact to my personal life. 

Social media platforms had the opportunity to fix this with personalized feeds. But, these platforms have become plagued with misinformation and sensational headlines over genuine reporting. I needed some place, where I can read summaries of news. Something that let me catch up with current affairs in 15-20mins, ignoring the sensationalism and the  irrelevant content.

### Scraper
I started by creating individual scrapers for each news website I regularly read. These scrapers - I refer to them as slave scrapers - would first fetch a list of all the headlines from the site. It would then follow each link and scrape the content storing them as JSON. Once I had three slave scrapers, I designed a `master scraper` in order to coordinate them. This uses Python's `ThreadPoolExecutor` to run the slave scrapers in parallel.

```python
from concurrent.futures import ThreadPoolExecutor, as_completed

# Imports for individual news sites
from slave_scrapers.fe_scrapper import get_news_content as get_fe
from slave_scrapers.fpj_scrapper import get_news_content as get_fpj
from slave_scrapers.toi_scrapper import get_news_content as get_toi


def run_scrapers() :
    scrapers = [get_fe, get_fpj, get_toi]
    results = []
    with ThreadPoolExecutor(max_workers=3) as executor :
        futures = [executor.submit(scraper) for scraper in scrapers]
        for future in as_completed(futures) :
            try :
                result = future.result()
                if isinstance(result, list) :
                    results.extend(result)
                else :
                    print(f"Warning : Scarper expected to return a list, returned {type(result)}")
            except Exception as e :
                print("Error running the scraper ", e)
    return results
```