### Cria o projeto frontend com react-ts
yarn create vite frontend --template react-ts

### projetos\dsmeta\frontend

### Instala as dependências
yarn

### Executa o projeto
yarn dev

### Criar o projeto com Spring Initializr
https://start.spring.io

### Configurações do projeto com Spring Initializr
Project: 		Maven Project      Language: Java      Spring Boot: 2.7.1
Project Metadata
Group: 			com.devsuperior
Artifact: 		dsmeta
Name: 			dsmeta
Descritpion: 	Projeto da Semana Spring React Devsuperior
Package name: 	com.devsuperior.dsmeta

### Dependências
Spring Web (web)
Spring Data JPA (SQL)
H2 Database (SQL)
Spring Security (Security)

### Criar o arquivo dsmeta.zip
Java: 17
Generate: [CTRL] + [ENTER]

### Extrair o conteúdo de dsmeta.zip, renomear a pasta criada para backend e copiar essa pasta para o diretório projetos\dsmeta

### projetos\dsmeta\backend

### Abrir o programa Spring Tool Suite (STS) e importar o projeto Maven > Existing Maven Projects

### Copiar o código abaixo e colar em projeto\dsmeta\backend\pom.xml no final do arquivo dentro das tags <build> e <plugins>

<plugin>
	<groupId>org.apache.maven.plugins</groupId>
	<artifactId>maven-resources-plugin</artifactId>
	<version>3.1.0</version><!--$NO-MVN-MAN-VER$ -->
</plugin>

### Formatação STS: [CTRL] + [SHIFT] + [F]

### Para atualizar o projeto com o plugin, abrir o programa STS, clicar com o BD em dsmeta[boot] > Maven > Update Project e marcar Force Update of Snapshots/Releases

### Criar o reposito dsmeta no Github. Abrir Git cmd e na pasta dsmeta configurar o Git

git init
git add .
git commit -m "Project created"
git branch -M main
git remote add origin git@github.com:cgetchepare/dsmeta.git
git push -u origin main

### Limpar os arquivos e fazer o update do projeto

git add .
git commit -m "Project clean"
git push

### Abrir o site https://figma.com, conforme o projeto e selecionar a imagem vector e exportar como vector.svg no canto superior direito da tela
### Renomear o arquivo para notification-icon.svg e copiar para projetos/dsmeta/frontend/src/img/notification-icon.svg

### Criar o arquivo index.tsx em projetos/dsmeta/frontend/src/components/NotificationButton/index.tsx

### No Vscode formatar código: [SHIFT] + [ALT] + [F]

### Código (projetos/dsmeta/frontend/src/App.tsx)

import NotificationButton from "./components/NotificationButton"

function App() {
  return (
    <>
      <h1>Olá Mundo!</h1>
      <NotificationButton />
    </>
  )
}

export default App


### Código (projetos/dsmeta/frontend/src/components/NotificationButton/index.tsx)

function NotificationButton() {
    return (
        <>
            <p>Meu componente</p>
            <p>Que legal!</p>
        </>
    )
}

export default NotificationButton


### No React quando se quer exportar mais de um componente, é necessário no return utilizar a tag fragment <> </> 

### No VsCode para selecionar e alterar uma palavra e todas as suas ocorrências dentro do arquivo [CTRL] + [D]  

### Instalar dependência para calendário Datepicker
yarn add react-datepicker@4.8.0 @types/react-datepicker@4.4.2

### React Hook useState para manter estado das datas
const date = new Date(new Date().setDate(new Date().getDate() - 365))]

### No STS, reiniciar o projeto
Boot Dashboard > local > dsmeta [BD] Re(start)

### O projeto Spring Boot conecta com a porta 8080
http://localhost:8080

### Importar tipos de variáveis, annotations ou dependências de bibliotecas no STS
[CTRL] + [SHIFT} +[O]

### Criar os métodos Getters e Setters
[BD] Source > Generate Getters and Setters

### Mapeamento Objeto Relacional JPA

### Annotations são usadas para fazer um pré-processamento do código a ser compilado e gerar o executável 
@Entity

### Acessar o banco de dados H2 através do navegador e criar a tabela 
http://localhost:8080/h2-console

Login

Saved Settings:	Generic H2 (Embedded)
Setting Name: 	Generic H2 (Embedded)
Driver Class: 	org.h2.Driver
JDBC URL: 		jdbc:h2:mem:testdb
User Name: 		sa
Password:

Connect

### Clicar em cima do nome da tabela (TB_SALES) gera automaticamente o comando  
SELECT * FROM TB_SALES. 

RUN

### No projeto em src/main/resources [BD] New > File > import.sql

### Abrir o arquivo import.sql no editor do STS e fazer um seed
import.sql [BD] Open With > Text Editor

### Copiar os registros para o arquivo e ao reinicar o projeto, os registros já estarão presentes no banco de dados

### Repository é o componente do sistema responsável pelo acesso e operações com banco de dados

### Criar a interface repositories. Em com.devsuperior.dsmeta [BD] New > Interface  
Source folder:	dsmeta/src/main/java
Package:		com.devsuperior.dsmeta.repositories
Name:			SaleRepository

### Service é o componente do sistema responsável por implementar operações de negócios (CRUD, buscas, regras de negócios)

### Em com.devsuperior.com.dsmeta [BD] New > Class
Source folder:	dsmeta/src/main/java
Package:		com.devsuperior.dsmeta.services
Name:			SaleService

### Controller é o componente do sistema responsável por implementar a API (requisição), disponibilizando os ENDPOINTS que o frontend vai precisar para acessar o backend

### Em com.devsuperior.com.dsmeta [BD] New > Class
Source folder:	dsmeta/src/main/java
Package:		com.devsuperior.dsmeta.controllers
Name:			SaleController

### palavra [CTRL] + [SPACE]

### Fluxo de Variação em 3 Camadas  Controller -> Service -> Repository

### @Autowired é uma anotação para injetar uma instância de algum componente do sistema

### Requisições

GET 	http://localhost:8080/sales
GET 	http://localhost:8080/sales?minDate=2022-01-01&maxDate=2022-03-31

### Dependências Maven - Twilio (envio de SMS)

### Copiar para o arquivo pow.xml do projeto o código em <dependencies></dependencies>
<dependencies>
...
	<dependency>
		<groupId>com.twilio.sdk</groupId>
		<artifactId>twilio</artifactId>
		<version>8.31.1</version>
	</dependency>
</dependencies>

### Copiar para o arquivo application.properties o código (variáveis de ambiente)

twilio.sid=${TWILIO_SID}
twilio.key=${TWILIO_KEY}
twilio.phone.from=${TWILIO_PHONE_FROM}
twilio.phone.to=${TWILIO_PHONE_TO}

spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.username=sa
spring.datasource.password=

spring.h2.console.enabled=true
spring.h2.console.path=/h2-console

spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true

### A anotação @Value busca no arquivo application.properties a variável de ambiente especificada. Por exemplo:
@Value("${twilio.sid}")
private String twilioSid;

dsmeta [BD] Run As > Run Configurations

http://localhost:8080/sales/notification

### Anotações e parâmetros
@GetMapping("/{id}/notification")

anotação -	@GetMapping
parâmetro -	{id}

### Alteração ENDPOINT com parâmetro id
http://localhost:8080/sales/53/notification



