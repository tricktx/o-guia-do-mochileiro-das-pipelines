# docker-guide

### Referências: 
1. https://github.com/ramoncunha/docker-guide
2. https://www.docker.com/resources/what-container/
3. https://docs.docker.com/get-started/docker-overview/

# Cronograma de Estudos para Docker

### **Semana 1: Introdução ao Docker**
- [x] Feito 
- **Teoria (1h)**:
    - O que é Docker e sua importância em projetos modernos.
    - Conceitos básicos: imagens, containers, volumes, e redes.
    - Instalação do Docker e Docker Compose.
- **Prática (1h)**:
    - Instalar Docker no seu ambiente de desenvolvimento.
    - Criar seu primeiro container: `docker run hello-world`.
    - Listar containers em execução e finalizados: `docker ps`, `docker ps -a`.
    - Explorar o Docker Hub e baixar uma imagem, como o Nginx: `docker pull nginx`.

**Exercício:** Criar um container do Nginx, acessar pelo navegador e remover o container.

---

### **Semana 2: Trabalhando com Imagens e Containers**
- [ ] Feito
- **Teoria (1h)**:
    - Estrutura de uma imagem Docker.
    - Diferença entre imagens e containers.
    - Comandos principais: `build`, `run`, `stop`, `start`, `rm`.
- **Prática (1h)**:
    - Criar e executar containers a partir de imagens pré-existentes.
    - Subir um banco de dados (MySQL) como container:
        
        ```bash
        docker run --name mysql-container -e MYSQL_ROOT_PASSWORD=root -d mysql:latest
        ```
        
    - Conectar-se ao container usando um cliente.

**Exercício:** Criar e gerenciar containers MySQL, explorando o ciclo de vida do container.

---

### **Semana 3: Dockerfile - Criando Imagens Personalizadas**
- [ ] Feito
- **Teoria (1h)**:
    - O que é um Dockerfile e sua estrutura.
    - Instruções básicas: `FROM`, `RUN`, `COPY`, `CMD`.
    - Conceito de camadas no Docker.
- **Prática (1h)**:
    - Criar uma aplicação simples em Spring Boot.
    - Criar um Dockerfile para a aplicação:
        
        ```dockerfile
        FROM openjdk:17
        COPY target/app.jar app.jar
        ENTRYPOINT ["java", "-jar", "app.jar"]
        ```
        
    - Construir e executar a imagem:
        
        ```bash
        docker build -t spring-app .
        docker run -p 8080:8080 spring-app
        ```
        

**Exercício:** Criar uma imagem Docker personalizada para sua aplicação Spring Boot e testar o acesso.

---

### **Semana 4: Docker Compose**
- [ ] Feito
- **Teoria (1h)**:
    - O que é Docker Compose e suas vantagens.
    - Estrutura de um arquivo `docker-compose.yml`.
    - Comandos principais: `up`, `down`.
- **Prática (1h)**:
    - Criar um `docker-compose.yml` para rodar a aplicação Spring Boot com MySQL.
        
        ```yaml
        version: '3'
        services:
          app:
            build: .
            ports:
              - "8080:8080"
          db:
            image: mysql:latest
            environment:
              MYSQL_ROOT_PASSWORD: root
        ```
        

**Exercício:** Configurar e rodar a aplicação Spring Boot com MySQL usando Docker Compose.

---

### **Semana 5: Volumes e Persistência de Dados**
- [ ] Feito
- **Teoria (1h)**:
    - O que são volumes e por que usá-los.
    - Criando e montando volumes.
    - Persistência em bancos de dados.
- **Prática (1h)**:
    - Configurar um volume para o MySQL no `docker-compose.yml`:
        
        ```yaml
        volumes:
          - db_data:/var/lib/mysql
        volumes:
          db_data:
        ```
        

**Exercício:** Persistir dados no banco de dados MySQL mesmo após reiniciar o container.

---

### **Semana 6: Redes e Comunicação entre Containers**
- [ ] Feito
- **Teoria (1h)**:
    - Redes no Docker: bridge, host e overlay.
    - Comunicação entre containers usando redes.
- **Prática (1h)**:
    - Criar uma rede no Docker Compose e conectar os serviços.
    - Testar comunicação entre a aplicação Spring Boot e o banco de dados.

**Exercício:** Testar comunicação entre múltiplos containers.

---

### **Semana 7: Otimização e Debugging**
- [ ] Feito
- **Teoria (1h)**:
    - Reduzindo o tamanho de imagens.
    - Analisando logs e debugando containers.
    - Explorando o comando `docker inspect`.
- **Prática (1h)**:
    - Otimizar o Dockerfile da aplicação Spring Boot.
    - Usar logs e o comando `exec` para acessar um container em execução.

**Exercício:** Identificar e corrigir problemas em uma aplicação containerizada.

---

### **Semana 8: Testes, CI/CD e Próximos Passos**
- [ ] Feito
- **Teoria (1h)**:
    - Automatizando testes com containers.
    - Docker em pipelines CI/CD.
    - Explorando ferramentas adicionais: Kubernetes e Docker Swarm.
- **Prática (1h)**:
    - Criar testes unitários que utilizam containers (Testcontainers).
    - Configurar um pipeline CI/CD simples com Docker.

**Exercício:** Implementar testes com Testcontainers em uma aplicação Spring Boot.

---

### **Dicas Gerais**

1. **Documentação:** Consulte a documentação oficial do Docker sempre que necessário.
2. **Prática Regular:** Mesmo fora do horário de estudo, pratique comandos básicos no terminal.
3. **Comunidade:** Participe de fóruns e grupos para aprender com outros desenvolvedores.

Pronto para começar? 🚀 Caso queira ajustes ou mais detalhes, é só pedir!

---

## Semana 1: Introdução ao Docker

### **Objetivo**

Compreender os conceitos básicos do Docker e realizar a instalação e execução de seus primeiros containers.

---

### **Teoria: O que é Docker?**

Docker é uma plataforma que permite criar, gerenciar e executar aplicações em containers. Containers são como máquinas virtuais leves que compartilham o kernel do sistema operacional, tornando-os rápidos e eficientes.

**Principais conceitos:**

- **Imagens:** Modelos "prontos" que servem como base para criar containers.
- **Containers:** Instâncias em execução de uma imagem.
- **Volumes:** Local de armazenamento para dados persistentes.
- **Redes:** Mecanismo para comunicação entre containers.

**Por que usar Docker?**

- Isolamento de aplicações.
- Portabilidade entre diferentes ambientes.
- Fácil integração em pipelines de CI/CD.

---

### **Instalação do Docker no MacOS M1**

A versão padrão do Docker suporta os processadores M1. Siga os passos abaixo:

1. **Baixe o Docker Desktop:**
    
    - Acesse [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop).
    - Baixe a versão para **Mac com chip Apple (Silicon)**.
2. **Instale o Docker Desktop:**
    
    - Abra o arquivo `.dmg` baixado e arraste o ícone do Docker para a pasta **Aplicativos**.
    - Inicie o Docker e siga as instruções na tela.
3. **Verifique a instalação:** Abra o terminal e execute:
    
    ```bash
    docker --version
    ```
    
    Resultado esperado (ou similar):
    
    ```
    Docker version 24.0.5, build 123456
    ```
    

---

### **Primeiros Passos no Docker**

Agora que o Docker está instalado, vamos explorar os comandos básicos.

1. **Testar o Docker:** Execute o comando:
    
    ```bash
    docker run hello-world
    ```
    
    Esse comando:
    
    - Baixa a imagem `hello-world` do Docker Hub (se não estiver localmente).
    - Cria e executa um container a partir dela.
    - Exibe uma mensagem de sucesso.
2. **Listar containers:**
    
    - Para ver containers ativos:
        
        ```bash
        docker ps
        ```
        
    - Para ver todos os containers (ativos ou não):
        
        ```bash
        docker ps -a
        ```
        
3. **Baixar uma imagem do Docker Hub:**
    
    - Baixe uma imagem do Nginx:
        
        ```bash
        docker pull nginx
        ```
        
4. **Criar e executar um container do Nginx:**
    
    - Inicie um container Nginx:
        
        ```bash
        docker run --name nginx-container -d -p 8080:80 nginx
        ```
        
    - O Nginx estará disponível em [http://localhost:8080](http://localhost:8080/).
5. **Parar e remover containers:**
    
    - Pare o container:
        
        ```bash
        docker stop nginx-container
        ```
        
    - Remova o container:
        
        ```bash
        docker rm nginx-container
        ```
        

---

### **Exercícios Práticos**

1. **Teste o Hello World:** Execute `docker run hello-world` e identifique o fluxo de execução.
2. **Explore o Docker Hub:**
    - Visite o [Docker Hub](https://hub.docker.com/) e procure imagens populares como `nginx` ou `mysql`.
    - Baixe uma imagem de sua escolha usando `docker pull`.
3. **Crie e acesse um container do Nginx:**
    - Use `docker run` para criar o container.
    - Acesse o container via navegador em [http://localhost:8080](http://localhost:8080/).
4. **Gerencie containers:**
    - Liste os containers com `docker ps`.
    - Pare e remova o container do Nginx.

---

### **Comandos Úteis**

|Comando|Descrição|
|---|---|
|`docker --version`|Verificar a versão do Docker.|
|`docker pull <imagem>`|Baixar uma imagem do Docker Hub.|
|`docker run <imagem>`|Criar e executar um container.|
|`docker ps`|Listar containers ativos.|
|`docker ps -a`|Listar todos os containers (ativos ou não).|
|`docker stop <nome>`|Parar um container em execução.|
|`docker rm <nome>`|Remover um container.|
|`docker images`|Listar imagens locais.|
|`docker rmi <imagem>`|Remover uma imagem do repositório local.|

---

### **Checklist da Semana 1**

- [x]  Instalei o Docker no meu Mac.
- [x]  Executei o comando `docker run hello-world`.
- [x]  Listei containers e imagens no meu sistema.
- [x]  Subi um container do Nginx e acessei pelo navegador.
- [x]  Explorei e entendi como parar e remover containers.

---

## Semana 2: Trabalhando com Imagens e Containers

---

### **Teoria (1h)**

1. **Estrutura de uma imagem Docker**
    
    - Imagens são compostas por camadas, cada uma representando uma instrução no Dockerfile.
    - As camadas são reutilizadas para otimizar armazenamento e construção de imagens.
2. **Diferença entre Imagens e Containers**
    
    - **Imagem:** Blueprint para criar containers.
    - **Container:** Instância em execução de uma imagem, isolada e independente.
3. **Comandos principais:**
    
    - `build`: Para construir uma imagem a partir de um Dockerfile.
    - `run`: Para criar e iniciar containers com base em uma imagem.
    - `stop`, `start`: Gerenciar containers em execução.
    - `rm`: Remover containers.
    - `rmi`: Remover imagens do sistema local.

---

### **Prática (1h)**

#### **Passo 1: Criar e executar containers**

- Execute o container Nginx mapeando a porta:
    
    ```bash
    docker run -d --name nginx-container -p 8080:80 nginx:latest
    ```
    
    - `-p 8080:80`: Mapeia a porta 8080 do host para a porta 80 do container.
        - Acesse o Nginx no navegador em `http://localhost:8080`.

---

#### **Passo 2: Subir um Banco de Dados MySQL**

```bash
docker run --name mysql-container -e MYSQL_ROOT_PASSWORD=root -d mysql:latest
```

- `-e MYSQL_ROOT_PASSWORD=root`: Define a senha do usuário `root` no MySQL.
    - O usuário `root` tem privilégios administrativos para criar bancos, tabelas e usuários.
- A senha será solicitada ao conectar ao MySQL (usando `mysql -uroot -p`).
- Esse comando cria um banco de dados funcional e seguro com a senha especificada.

---

#### **Passo 3: Conectar ao MySQL no container**

```bash
docker exec -it mysql-container mysql -uroot -p
```

- `docker exec`: Executa comandos em um container ativo.
- `-it`: Permite interação com o terminal dentro do container.
- `mysql -uroot -p`: Abre o cliente MySQL e autentica com o usuário `root`.
    - Ao pressionar Enter, a senha configurada (`root`) será solicitada.

Dentro do cliente MySQL:

```sql
CREATE DATABASE exemplo;
SHOW DATABASES;
```

Esses comandos criam e listam bancos de dados.

---

#### **Passo 4: Subir um Banco de Dados com Persistência**

```bash
docker run --name mysql-persistent -e MYSQL_ROOT_PASSWORD=root -v mysql_data:/var/lib/mysql -d mysql:latest
```

##### **Explicação detalhada:**

- **`-v mysql_data:/var/lib/mysql`:**
    - Cria um **volume nomeado** chamado `mysql_data`.
    - Monta o volume no caminho `/var/lib/mysql` do container.
    - Essa configuração **garante que os dados do banco sejam persistidos**, mesmo que o container seja removido.
- Após parar e remover o container, o volume `mysql_data` mantém os dados.

Teste de persistência:

1. Suba o container e crie um banco:
    
    ```bash
    docker exec -it mysql-persistent mysql -uroot -p
    ```
    
    ```sql
    CREATE DATABASE persistencia;
    ```
    
2. Pare e remova o container:
    
    ```bash
    docker stop mysql-persistent
    docker rm mysql-persistent
    ```
    
3. Suba um novo container com o mesmo volume:
    
    ```bash
    docker run --name mysql-new -e MYSQL_ROOT_PASSWORD=root -v mysql_data:/var/lib/mysql -d mysql:latest
    ```
    
4. Conecte-se e veja o banco persistente:
    
    ```sql
    SHOW DATABASES;
    ```
    

---

### **Exercício Prático**

1. **Gerenciar o ciclo de vida de containers**
    
    - Subir, parar, reiniciar e remover containers.
    - Usar os comandos `docker ps`, `docker stop`, `docker start`, e `docker rm`.
2. **Persistência de Dados**
    
    - Criar um container MySQL com volume persistente (`-v`).
    - Testar a persistência ao recriar o container e verificar se os dados permanecem.

---

### **Resumo dos Comandos Aprendidos**

|Comando|Descrição|
|---|---|
|`docker run`|Criar e executar um container.|
|`-e`|Define variáveis de ambiente dentro do container.|
|`-v`|Cria volumes para persistir dados.|
|`docker exec`|Executa comandos em um container em execução.|
|`docker stop` / `docker start`|Para e inicia containers existentes.|
|`docker rm`|Remove containers parados.|

---

**Pronto para colocar em prática?** Caso surjam dúvidas, é só chamar! 🔥

--- 

## Semana 3: Em breve