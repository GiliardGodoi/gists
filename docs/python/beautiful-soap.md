# Beautiful Soap
```python
from bs4 import BeautifulSoup
```

Basic usage.

```python
    from bs4 import BeautifulSoup

    filename = 'index.html'

    html_doc = open(filename, 'r', encoding='utf-8').read()
    soup = BeautifulSoup(html_doc,'html.parser')

    links = soup.find_all('a',href=True)
    lts = soup.find_all('ul',class_='visualNoMarker')
```

## Outras codificações
- utf-8
- iso-8859-1
- latin-1
