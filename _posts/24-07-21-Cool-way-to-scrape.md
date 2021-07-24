---
title: 'Cool way to scrape?'
date: 2021-07-24
layout: post
comments: false
tags:
  - Scarping
  - Cli
---
For scraping my workflow was to make a get request to obtain the HTML and then
use BeautifulSoup to scrape. Is there any way around? a way to get structured data?

I always use [ytfzf](https://github.com/pystardust/ytfzf) to search youtube videos, it is very convenient because
I can skip the recommendation on the homepage on youtube, which is a huge
distraction. One part I was missing was the comment section. I was looking if
there is a way to obtain comments in the terminal. In my quest I found [this](https://github.com/egbertbouman/youtube-comment-downloader).
I was curious how this package was implemented. I found this cool way of doing
requests.

If we want to make several requests to the same host we can use [requests.Session()](https://docs.python-requests.org/en/master/user/advanced/#session-objects),
It will use the same TCP connection. As a stock market enthusiast, I was looking
if this can be used to get a live stock price from the NSE. Well, we can! There
is a reload button and when it is pressed, a hell lot of requests are sent to the
server. This URL seems to return the data that we are looking for
`https://www.nseindia.com/api/quote-equity?symbol=TCS`. Without a prior connection
to NSE, this might give you an error. That's where the session helps.

```python
import json

import requests

USER_AGENT = 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) '\
             'AppleWebKit/537.36 (KHTML, like Gecko) '\
             'Chrome/79.0.3945.130 Safari/537.36'

BASE_URL = 'https://www.nseindia.com/'

session = requests.Session()
session.headers['User-Agent'] = USER_AGENT
# trying first connection
r = session.get(BASE_URL)


def get_price(ticker):
    session.headers['referer'] = f'{BASE_URL}get-quotes/equity?symbol={ticker}'
    payload = {'symbol': ticker}
    data = session.get(f"{BASE_URL}api/quote-equity", params=payload)
    data = data.text.strip()
    return json.loads(data)

get_price("TCS")
```

I was looking for a cli-watchlist, now I got the main ingredient.
