# OMS Quick Start Guide

Bem-vindo! Segue estes passos simples para executar o Order Management System (OMS).

## Pré-requisitos

Só precisas de uma coisa instalada.

### Docker Desktop

Faz o download e instala a partir de:
[https://www.docker.com/products/docker-desktop/](https://www.docker.com/products/docker-desktop/)

* Windows: descarregar o instalador para Windows
* Mac: descarregar o instalador para Mac (Intel ou Apple Silicon)
* Linux: seguir o guia de instalação para Linux

Após a instalação, confirma que o Docker Desktop está a correr (deverás ver o ícone da baleia na barra de tarefas).

---

## Executar o Projeto

### Passo 1: Extrair o ZIP

Extrai o ficheiro `oms-devops-project.zip` para uma pasta à tua escolha.

### Passo 2: Abrir o Terminal

Abre o PowerShell (Windows) ou o Terminal (Mac/Linux) e navega até à pasta do projeto:

```bash
cd caminho/para/oms-devops-project
```

### Passo 3: Iniciar Tudo

Escolhe quantas instâncias de frontend queres executar.

Opção A: Modo Standard (Frontend Único)

```bash
docker-compose up -d
```

Opção B: Modo Produção (3 Frontends com Load Balancing)

```bash
docker-compose up -d --scale frontend=3
```

A primeira execução pode demorar entre 2 a 5 minutos, enquanto o Docker descarrega e constrói as imagens.

### Passo 4: Aguardar pelos Serviços

Aguarda cerca de 1 a 2 minutos para que todos os serviços iniciem.
Podes verificar o estado com:

```bash
docker ps
```

Todos os contentores deverão aparecer com o estado "Up".

### Passo 5: Aceder à Aplicação

Abre o browser e acede a:

| Serviço             |URL                                                 |
| ------------------------------------------------------------------------- |
| App Principal       | [http://localhost](http://localhost)                   |
| Documentação da API | [http://localhost/api-docs](http://localhost/api-docs) |
| Consulta IA         | [http://localhost/ai](http://localhost/ai)             |

---

## Credenciais de Login

### Conta de Administrador

| Campo    | Valor           |
| -------- | --------------- |
| Email    | `admin@oms.com` |
| Password | `admin123`      |

### Ou Registar uma Nova Conta

Clica em "Register" na página de login para criares uma nova conta de cliente.

---

## Testar Funcionalidades

### Gestão de Produtos (Administrador)

* Inicia sessão como administrador
* Vai a Products → Add Product
* Cria novos produtos com nome, preço e stock

### Compras (Cliente)

* Regista-te ou inicia sessão como cliente
* Navega pelos produtos
* Adiciona ao carrinho e finaliza a compra

### Consulta com IA

* Vai à secção AI Query
* Faz perguntas como:

  * "Mostra todas as encomendas"
  * "Quais são os 5 produtos mais vendidos?"
  * "Lista os utilizadores registados este mês"

---

## Parar a Aplicação

Para parar todos os serviços:

```bash
docker-compose down
```

Para parar e apagar todos os dados (reinício completo):

```bash
docker-compose down -v
```

---

## Resolução de Problemas

### Cannot connect to Docker daemon

* Confirma que o Docker Desktop está a correr
* Tenta reiniciar o Docker Desktop

### Port already in use

* Fecha outras aplicações que estejam a usar as portas 3000, 5000 ou 8000
* Ou altera as portas no ficheiro `.env`

### Login de administrador não funciona

Reinicia o serviço de backend:

```bash
docker restart oms-backend
```

### Precisas de começar do zero?

```bash
docker-compose down -v
docker-compose up -d
```

---

## Suporte

Se encontrares algum problema, entra em contacto com a equipa de desenvolvimento.
