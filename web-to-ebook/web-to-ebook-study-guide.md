# Web to EPUB Converter 📚

## 🌟 Projeto
Um script Python para converter páginas web em livros eletrônicos no formato EPUB.

## 🛠 Tecnologias
- Python
- Requests
- BeautifulSoup
- EbookLib

## 📦 Instalação

### Pré-requisitos
- Python 3.x
- pip

### Dependências
```bash
pip install requests beautifulsoup4 ebooklib
```

## 🚀 Uso Básico
```python
from web_to_epub import create_ebook

create_ebook('https://exemplo.com/artigo', 'Meu E-book')
```

## 🔍 Funcionalidades
- Extração de conteúdo web
- Conversão para formato EPUB
- Geração de e-book personalizado

## 📝 Próximos Passos
- [ ] Suporte a múltiplos capítulos
- [ ] Tratamento de erros
- [ ] Personalização de formatação

# Conversor Web para E-book em Python

## Bibliotecas Utilizadas
- `requests`: Baixar conteúdo web
- `BeautifulSoup`: Parsear HTML
- `ebooklib`: Criar e-books EPUB

## Passos para Criar o E-book

### 1. Importações
```python
import requests
from bs4 import BeautifulSoup
from ebooklib import epub
```

### 2. Função Principal: `create_ebook(url, book_title)`

#### a. Baixar Conteúdo Web
```python
response = requests.get(url)
soup = BeautifulSoup(response.content, 'html.parser')
```
- Faz requisição HTTP GET
- Parseia o conteúdo HTML

#### b. Criar Objeto E-book
```python
book = epub.EpubBook()
book.set_title(book_title)
```
- Inicializa livro EPUB vazio
- Define título do livro

#### c. Criar Capítulo
```python
chapter = epub.EpubHtml(title='Chapter 1', file_name='chap_01.xhtml')
chapter.content = soup.prettify()
book.add_item(chapter)
```
- Cria capítulo HTML
- Define conteúdo formatado
- Adiciona capítulo ao livro

#### d. Salvar E-book
```python
book.spine = ['nav', chapter]
epub.write_epub(f'{book_title}.epub', book, {})
```
- Configura navegação
- Salva arquivo EPUB

### 3. Exemplo de Uso
```python
create_ebook('https://example.com/your-favorite-article', 'My eBook')
```

## Commits e Boas Práticas

### Tipos de Commits
- `feat`: Nova funcionalidade
- `chore`: Tarefa de manutenção
- `build`: Preparação de estrutura
- `test`: Demonstração/teste

### Commits do Projeto
1. Importações e Setup
   - "feat: setup inicial do conversor web para e-book"

2. Baixar Conteúdo Web
   - "feat: baixa conteúdo web e transforma em objeto BeautifulSoup"

3. Criar E-book
   - "feat: cria objeto de e-book com título personalizado"

4. Adicionar Capítulo
   - "feat: create and add HTML chapter to EPUB book"

5. Salvar E-book
   - "chore: configure EPUB navigation and export book"

## Instalação
```bash
pip install requests beautifulsoup4 ebooklib
```

## Possíveis Melhorias
- Extrair múltiplos capítulos
- Adicionar metadados
- Personalizar formatação
- Tratamento de erros
