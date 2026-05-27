# Social_media_scrapper

A Python-based web scraper that extracts posts from an HTML file simulating a social media feed and saves the data to a structured CSV file.

---

 Features

- Parses HTML files using **BeautifulSoup4**
- Extracts **username**, **post content**, and **timestamp** from each post
- Saves extracted data to a clean **CSV file** using Python's built-in `csv` module
- Modular code structure with separate functions for loading, extracting, and saving data

---

##  Tech Stack

| Tool | Purpose |
|------|---------|
| Python 3.x | Core language |
| BeautifulSoup4 | HTML parsing |
| csv (built-in) | Data storage |

---

## Project Structure

```
social-media-scraper/
│
├── scraper.py              # Main scraper script
├── social_media.html       # Sample HTML input file
├── social_media_posts.csv  # Output CSV (generated on run)
└── README.md               # Project documentation
```

---

##  Installation

**1. Clone the repository**

```bash
git clone https://github.com/your-username/social-media-scraper.git
cd social-media-scraper
```

**2. Install dependencies**

```bash
pip install beautifulsoup4
```

> Python's `csv` module is built-in — no extra install needed.

---

##  Usage

**1. Make sure your HTML file is in the project folder**

The scraper expects an HTML file named `social_media.html` with posts structured like:

```html
<div class="post">
  <h2 class="username">Alice</h2>
  <p class="content">Hello, world!</p>
  <span class="timestamp">2024-01-01 10:00 AM</span>
</div>
```

**2. Run the scraper**

```bash
python scraper.py
```

**3. Check the output**

A file named `social_media_posts.csv` will be created in the same directory:

```
username,content,timestamp
Alice,Hello world!,2024-01-01 10:00 AM
Bob,Python is awesome!,2024-01-01 11:30 AM
```

---

##  How It Works

```
social_media.html
      │
      ▼
load_html()        → reads the raw HTML file
      │
      ▼
BeautifulSoup()    → parses HTML into a navigable tree
      │
      ▼
extract_posts()    → finds all div.post elements and pulls
                     username, content, timestamp from each
      │
      ▼
save_posts_to_csv() → writes results to social_media_posts.csv
```

---

##  Code Overview

### `load_html(file_path)`
Opens and reads the HTML file, returning its content as a string.

### `extract_posts(soup)`
Accepts a BeautifulSoup object and finds all `div.post` elements. For each post, it extracts:
- `h2.username` → post author
- `p.content` → post text
- `span.timestamp` → time of post

Returns a list of dictionaries.

### `save_posts_to_csv(posts, output_path)`
Writes the list of post dictionaries to a CSV file using `csv.DictWriter`, with a header row automatically added.

---

##  Future Improvements

- [ ] Add `requests` support to scrape live URLs
- [ ] Add error handling for missing HTML elements
- [ ] Store data in a SQLite database instead of CSV
- [ ] Add CLI arguments using `argparse` for custom input/output paths
- [ ] Support pagination for multi-page scraping
- [ ] Write unit tests using `pytest`
- [ ] Add rate limiting and polite delays for live scraping

---

##  Disclaimer

This project is for **educational purposes only**. Always check a website's `robots.txt` and Terms of Service before scraping any live site. Do not use this tool to scrape private or authenticated data.

---

##  Author

Yogesh Morwal
[GitHub](https://github.com/imyogii001)            • [LinkedIn](https://linkedin.com/in/yogesh-morwal)

---

