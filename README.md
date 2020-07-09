##  Extraindo dados da web com Python

Aplicação em Python para extrair dados de um site e tratar esses dados de acordo com a necessidade

  ###  Site utilizado

https://www.uol.com.br/esporte/

###  Dependências

> $pip install requests
>
> $pip install beautifulsoup4

### Código

    res = requests.get("https://www.uol.com.br/esporte/")
    res.encoding  =  'utf-8'
    soup =  BeautifulSoup(res.text,  'html.parser')
    posts = soup.find_all(class_  ='thumbnail-standard')

    all_posts =  []
    for post in posts:
	    assunto = post.span.text
	    titulo = post.h2.text
	    imagem = post.img['src']
    l	ink = post.a['href']

    all_posts.append({'assunto': assunto,  'titulo': titulo,  'imagem': imagem,  'link': link})

### Salvando em arquivo

    with  open('posts.json',  'w')  as json_file:
    json.dump(all_posts, json_file,  indent=3,  ensure_ascii=False)
