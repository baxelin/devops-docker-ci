# DevOps Docker CI

Projeto de um site estático containerizado com Docker e validado automaticamente com GitHub Actions.

## Visão geral

Este projeto demonstra um fluxo simples e profissional de containerização e integração contínua para uma aplicação web estática. O conteúdo é servido por Nginx dentro de um container Docker, enquanto o pipeline de CI valida se a imagem pode ser construída e se o container responde corretamente.

## Objetivo

O objetivo deste projeto é mostrar, de forma clara e prática, fundamentos de Docker e CI em um cenário realista para portfólio e recrutamento.

O projeto foca em:

- containerizar uma aplicação web estática;
- automatizar validações com GitHub Actions;
- documentar o processo de execução local;
- criar uma base simples para evolução futura para CD.

## Tecnologias utilizadas

- Docker
- Nginx
- GitHub Actions
- HTML
- Tailwind CSS via CDN

## Estrutura do projeto

```text
.
├── Dockerfile
├── frontend/
│   └── index.html
└── .github/
	└── workflows/
		└── ci.yml
```

## Como funciona

O Dockerfile usa a imagem oficial do Nginx em uma versão leve. Durante o build, o arquivo `frontend/index.html` é copiado para o diretório padrão do servidor web, que é `/usr/share/nginx/html/`.

Quando o container sobe, o Nginx fica responsável por servir a página na porta `80`.

O workflow de CI faz três coisas principais:

1. baixa o código do repositório;
2. constrói a imagem Docker;
3. sobe um container temporário e verifica se a aplicação responde via HTTP.

## Pré-requisitos

Para rodar o projeto localmente, você precisa ter:

- Docker instalado;
- Git instalado, se for clonar o repositório;
- acesso a um terminal.

## Como rodar localmente

### 1. Clonar o repositório

```bash
git clone <URL_DO_SEU_REPOSITORIO>
cd devops-docker-cicd
```

### 2. Construir a imagem

```bash
docker build -t meu-site:1.0 .
```

### 3. Executar o container

```bash
docker run --rm -p 8080:80 meu-site:1.0
```

### 4. Acessar no navegador

Abra:

```text
http://localhost:8080
```

## CI com GitHub Actions

O arquivo `.github/workflows/ci.yml` é executado automaticamente em:

- `push` na branch `main`;
- `pull_request` com destino na branch `main`.

Esse workflow ajuda a garantir que:

- o Dockerfile continua válido;
- a imagem ainda é construída com sucesso;
- o container responde corretamente na porta esperada.

## O que este projeto demonstra para recrutadores

Este projeto mostra que você entende conceitos importantes de DevOps e entrega de software, como:

- containerização de aplicações;
- construção e execução de imagens Docker;
- validação automática com GitHub Actions;
- organização básica de projeto;
- noção de pipeline de CI;
- preparo para evolução futura para CD.

## Próximas melhorias possíveis

- adicionar um `.dockerignore`;
- publicar a imagem em um registry como o GitHub Container Registry;
- criar uma etapa de CD;
- adicionar testes automatizados mais completos;
- separar o conteúdo do site em mais arquivos estáticos.

## Autor

Lucas Baccelli
