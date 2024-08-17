# Relatório Técnico sobre MongoDB

Autores:

- Denis de Souza Cordeiro
- Luis Felipe Costa Teixeira
- Ronald de Souza Galdino

### GitHub Pages: [Link](https://www.mongodb.com/what-is-mongodb](https://denisdesouzac.github.io/trabalho-mkdocs/index.html))

## Sumário
1. [Introdução](#introducao)
2. [Histórico](#historico)
3. [Descrição Técnica](#descricao-tecnica)
4. [Aplicações](#aplicacoes)
5. [Vantagens e Desvantagens](#vantagens-e-desvantagens)
6. [Comparações](#comparacoes)
7. [Casos de Uso](#casos-de-uso)
8. [Implementação com Mkdocs](#implementacao-com-mkdocs)
   8.1 [Instalação e Configuração](#instalacao-e-configuracao)
   8.2 [Estrutura do Site](#estrutura-do-site)
   8.3 [Customização](#customizacao)
   8.4 [Publicação](#publicacao)
9. [Conclusão](#conclusao)
10. [Referências](#referencias)

## 1. [Introdução](#introducao)
O MongoDB é um banco de dados NoSQL orientado a documentos que permite armazenar dados em um formato flexível e escalável. Este relatório tem como objetivo apresentar uma visão abrangente sobre o MongoDB, destacando seus principais aspectos, funcionamento e aplicações práticas.

## 2. [Histórico](#historico)
O MongoDB foi lançado pela 10gen (agora MongoDB Inc.) em 2009. Ele foi desenvolvido para lidar com grandes volumes de dados e proporcionar escalabilidade horizontal. Desde seu lançamento, o MongoDB se tornou um dos bancos de dados NoSQL mais populares no mercado.

## 3. [Descrição Técnica](#descricao-tecnica)
- Arquitetura: Orientado a documentos, armazena dados em formato BSON (uma extensão binária do JSON).
- Modelagem de Dados: Flexível, sem esquema fixo, suporta documentos aninhados.
- Consultas: Suporta consultas ad hoc, índices secundários, e agregações.
- Replicação: Suporta réplicas para alta disponibilidade.
- Sharding: Suporta partição horizontal dos dados para escalabilidade.

## 4. [Aplicações](#aplicacoes)
- Web Applications
- Big Data
- Real-time Analytics
- Internet of Things (IoT)

## 5. [Vantagens e Desvantagens](#vantagens-e-desvantagens)

### Vantagens:
- Flexibilidade na modelagem de dados.
- Alta escalabilidade.
- Suporte a consultas complexas.
- Foco em alta disponibilidade.

### Desvantagens:
- Pode ser menos eficiente para certas operações transacionais.
- Necessidade de uma boa gestão de índices para performance.
- Curva de aprendizado para administração e tuning.

## 6. [Comparações](#comparacoes)
### Comparação com bancos de dados relacionais (SQL):
- Estrutura de dados flexível vs. esquema fixo.
- Escalabilidade horizontal nativa vs. escalabilidade vertical.
- Suporte a dados aninhados vs. tabelas relacionais.

### Comparação com outros bancos NoSQL (e.g., Cassandra):
- Document-oriented vs. column-oriented.
- Suporte a consultas ad hoc vs. consulta otimizada para leitura rápida.

## 7. [Casos de Uso](#casos-de-uso)
- Airbnb: Utiliza MongoDB para armazenar dados de listagens e reservas.
- Uber: Usa MongoDB para armazenar dados de geolocalização e fornecer informações em tempo real.

## 8. [Implementação com Mkdocs](#implementacao-com-mkdocs)

### 8.1 [Instalação e Configuração](#instalacao-e-configuracao)

1. **Instalar Mkdocs:**
   ```bash
   pip install mkdocs

2. **Criar um novo projeto Mkdocs:**
   ```bash
   mkdocs new relatorio-mongodb
   cd relatorio-mongodb

3. Estrutura do Projeto Mkdocs:

Dentro da pasta relatorio-mongodb, você encontrará um arquivo mkdocs.yml (configuração do site) e uma pasta docs (conteúdo do site).

8.2 Estrutura do Site

- No arquivo mkdocs.yml, configure a navegação e o tema do site:

    ```bash
    site_name: Relatório Técnico sobre MongoDB
    nav:
    - Home: index.md
    - Introdução: introducao.md
    - Histórico: historico.md
    - Descrição Técnica: descricao_tecnica.md
    - Aplicações: aplicacoes.md
    - Vantagens e Desvantagens: vantagens_desvantagens.md
    - Comparações: comparacoes.md
    - Casos de Uso: casos_de_uso.md
    - Implementação com Mkdocs: implementacao_mkdocs.md
    - Conclusão: conclusao.md
    - Referências: referencias.md
    theme: readthedocs

8.3 Customização

- Adicione conteúdo aos arquivos Markdown na pasta docs e personalize o tema conforme necessário.

8.4 Publicação

1. Iniciar o servidor local:
    ```bash
    mkdocs serve

- Acesse http://127.0.0.1:8000 no navegador para ver o site.

2. Build do Projeto para Produção:

    ```bash
    mkdocs build

3. Publicar no GitHub Pages:

Crie um repositório no GitHub.
Adicione o repositório remoto ao seu projeto
    ```bash
    git init
    ```bash
    git add .
    ```bash
    git commit -m "Initial commit"
    ```bash
    git remote add origin <URL-do-repositorio>
    ```bash
    git push -u origin master

- Configure o GitHub Pages no repositório:
- Vá para as configurações do repositório no GitHub.
- Na seção "GitHub Pages", escolha a branch gh-pages.

9. Conclusão

Neste relatório, exploramos o MongoDB, abordando seus principais aspectos técnicos, vantagens, desvantagens e aplicações. Com base nos dados apresentados, concluímos que o MongoDB é uma tecnologia poderosa para uma variedade de cenários de uso, oferecendo flexibilidade e escalabilidade.

10. Referências

[1] MongoDB Inc. (2024). [What is MongoDB?](https://www.mongodb.com/what-is-mongodb) Acesso em: 07 de agosto de 2024.

[2] Chodorow, K. (2013). *MongoDB: The Definitive Guide*. O'Reilly Media. ISBN: 978-1449344689.

[3] Banker, K. (2011). *MongoDB in Action*. Manning Publications. ISBN: 978-1935182870.

[4] MongoDB Inc. (2024). [MongoDB Documentation](https://docs.mongodb.com/) Acesso em: 07 de agosto de 2024.

[5] Dwight Merriman, Eliot Horowitz, e Kevin P. Ryan (2009). *MongoDB: A Database for the Cloud Era*. [white paper](https://www.mongodb.com/collateral/mongodb-a-database-for-the-cloud-era) MongoDB Inc.

[6] GitHub. (2024). [MongoDB on GitHub](https://github.com/mongodb/mongo) Acesso em: 07 de agosto de 2024.

[7] Harris, S. (2020). *Mastering MongoDB 4.x: Expert techniques to run high-volume and fault-tolerant database solutions using MongoDB 4.x*. Packt Publishing. ISBN: 978-1789617873.

[8] Holowaychuk, TJ. (2018). [MongoDB Performance Tuning](https://engineering.mongodb.com/post/mongodb-performance-tuning) Acesso em: 07 de agosto de 2024.












