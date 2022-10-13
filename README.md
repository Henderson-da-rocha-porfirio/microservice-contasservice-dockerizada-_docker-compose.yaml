# Microserviço Contas Dockerizada com definições no Dockerfile e utilizando o docker-compose.yml

## Docker Compose
> - 1. É uma ferramenta que foi desenvolvida para ajudar a definir e compartilhar múltiplos containers(instâncias)
> - 2. É possível criar um arquivo .yaml para definir as regras para o serviço criado com um simples comando.
> - 3. Com o .yaml criado, o Docker Compose pode atualizar ou derrubar tudo com um simples comando.
> - 4. A grande vantagem de usá-lo é que é possível definir as filas(stacks) da aplicação do mesmo jeito que é feito com os recursos dentro do app.
> - 5. Pode definir tudo deles dentro de um simples arquivo .yaml e guardá-lo na raiz do relatório do projeto.
> - 6. Ele faz com todos os serviços subam ou caiam com apenas um comando.

### Verificando se há um docker compose instalado:
````
docker-compose version ou docker-compose --version
````

### Obs: Não há ligação entre o Dockerfile e o docker-compose.yml. Eles são independentes.

### Com um único comando, é possível subir os containers relacionados ao projeto, e que obviamente, foram definidos dentro do .yml.
### Iniciando o Container: Lembrando que tem que ser rodado o comando dentro do diretório que está o arquivo .yml(podendo ser: docker-compose.yml, docker-compose.yaml, compose.yml ou compose.yaml).
````
docker-compose up
````
### Verificar quais os que estão em modo "up":
````
docker ps
````
### Parando o Container(tem que abrir um novo terminal ou cmd, e rodar o comando dentro do diretório onde está o docker-compose.yml em questão):
````
docker-compose stop ou crtl + x ou + c
```

### Acessando ao H2
### - Lembrar:
#### a. Criar um arquivo sql: data.sql
#### b. Configurar o application.properties
#### c. Adicionar no pom a dependência(pode ser pelo starters ou manualmente):
````
<dependency>
			<groupId>com.h2database</groupId>
			<artifactId>h2</artifactId>
			<scope>runtime</scope>
</dependency>
````

#### 1. Verificar no console o endpoint criado:
````
h2-console
````
#### 2. No navegador colocar o endpoint criado com a porta local cofigurado nas properties. Se não tiver sido configurada, ficará na 8080:
````
http://localhost:8080/h2-console/
````
#### 3. Quando abrir no console, colocar em JDBC URL, se der algum erro, o que saiu no console, por exemplo:
````
 H2 console available at '/h2-console'. Database available at 'jdbc:h2:mem:testdb'
````
#### 4. Testando no Postman:
````
http://localhost:8080/myAccount
````
##### - se der um erro 415: Content type 'text/plain;charset=UTF-8' not supported], colocar no Headers:
````
1. KEY: Content-Type
2. VALUE: application/json
````
#### 5. A beleza dos Microservices: Não há nada acoplado da regra de negócio com os microserviços cartões ou empréstimos.

#### Correndo o docker image com a porta num terminal ou cmd:
````
docker run -p 8080:8080 hendersonporfirio/microservice-account

````
