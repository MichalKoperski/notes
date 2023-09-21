---
layout:
  title:
    visible: false
  description:
    visible: false
  tableOfContents:
    visible: false
  outline:
    visible: false
  pagination:
    visible: false
---

# web communication

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (7).jpg" alt=""><figcaption></figcaption></figure>

</div>

```python
#w windows jeśli trzeba zainstalować urllib3 w cmd
curl https://bootstrap.pypa.io/get-pip.py
python .\get-pip.py
pip install urllib3
```

```python
import urllib3

http=urllib3.PoolManager()
r=http.request("GET","google.com")
print(f"{r.status}")
print(f"{r.data.decode('utf-8')}")
```

```python
import urllib3

links=["asd","policies"]
http=urllib3.PoolManager()

for i in links:
  final_link="https://"+i+".google.com"
  r=http.request("GET","https://google.com/")
  print(f"{r.status}")
```

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (8).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/2 (4).jpg" alt=""><figcaption></figcaption></figure>

</div>

```python
import requests

r=requests.get("https://google.pl")
print(r.status_code)
print(r.headers)
print(r)
```

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (9).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/2 (5).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/3 (3).jpg" alt=""><figcaption></figcaption></figure>

</div>

```python
import requests

link="https://hack-yourself-first.com/Account/Login"
payload={"Email":"asdf@asdf.pl","Password":"123456"}

r=requests.post(link,data=payload)

if "Log in" in r.text:
  print("Sukces")
else:
  print(":(")
```

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (10).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/2 (6).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/3 (4).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/4 (3).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/5 (2).jpg" alt=""><figcaption></figcaption></figure>

</div>

```python
import requests
from bs4 import BeautifulSoup

r=requests.get("http://wp.pl/")
soup=BeautifulSoup(r.text, 'html.parser')

for line in soup.find_all("script"):
  link=line.get('src')
  if link.endswith('js'):
  print(link)
```

```python
import requests
from bs4 import BeautifulSoup

requests.packages.urllib3.util.ssl_.DEFAULT_CIPHERS += 'HIGH: !DH: !aNULL'
requests.adapters. DEFAULT_RETRIES = 5
session = requests.session ()
session.keep_alive = False

r = session.get("https://dziennikustaw.gov.pl/DU")
soup=BeautifulSoup(r.text, 'html.parser')

for url in soup.find_all('a'):
  link=str(url.get('href'))
  if link.endswith(".pdf"):
    params=link.split("/")
    nazwa_pdf=params[len(params)-1]
    tmp=r"https://dziennikustaw.gov.pl/DU".format(link)
    print(tmp)
    r_dwn=requests.get(tmp,allow_redirects=true)
    with open(fr"{nazwa_pdf}", "wb") as f:
      f.write(r_dwn.content)
  else:
    continue
```
