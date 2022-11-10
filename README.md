# Mission_to_Mars

import pandas as pd
from splinter import Browser
from bs4 import BeautifulSoup as soup
from webdriver_manager.chrome import ChromeDriverManager

executable_path = {"executable_path": ChromeDriverManager().install()}
browser = Browser("chrome", **executable_path, headless=False)

url = "https://redplanetscience.com/"
browser.visit(url)

redplanet_urls = []

for redplanet in range(4):
    browser.links.find_by_text("redplanet")
    
    
    html = browser.html
    redplanet_soup = soup(html, "html.parser")
    
    title = redplanet_soup.find("h2", class_="title").text
    img_url = redplanet_soup.find("li").a.get("href")
    
    redplanet = {}
    redplanet["img_url"] = f"https://redplanetscience.com/{img_url}"
    redplanet["title"] = title
    redplanet_image_urls.append(redplanet)
    
    browser.back()
    
redplanet_urls
