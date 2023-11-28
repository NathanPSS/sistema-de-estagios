# TCC

## Primeira Inicialização do BackEnd
docker compose up para inicializar os containers

## Login PGADMIN
email = admin@gmail.com
senha = postgree

## Criando Conexao
No PGADMIN
Add server group

Nome = hujb Host/Adders = postgres-compose (nome do container ou endereço IP) username = postgree password = 123 

### Criando Banco 
Botao direito em databases -> create -> template = template_postigis (opcional)

## Inicie a Aplicação BackEnd
No App Propeties esta setado para o JPA executar o SQL da aplicação automatico, ao iniciar o backend o app gera as tabelas automatico

## Configurando os Aplicativos

NOTA Configuração feita no Android Studio usando Linux Ubunto como SO

Instalar Flutter SDK (Method 1)

Instalar plugins Dart e Flutter no Android Studio

Abrir o projeto dos Aplicativos com o Android Studio 

### Configurando SDK

Com o projeto aberto File -> Settings -> Languages & Frameworks -> Flutter -> Adicionar o caminho SDK do flutter (flutter sdk-path para mostrar o caminho caso a IDE nao automaticamente reconheça)

## Configurando pacotes 

no terminal do projeto comando flutter pub get para adicionar outras libs

## Configurando APPs

ifconfig no terminal e descobrir o IP da maquina.

com o IP mudar a configuração do .env para API_BASE_URL=http://(ip da maquina):8080

Esse passo deve ser repetido para todas as 3 aplicações (App Est,App Precep, e o QrcodeTotens)

## Adicionando Entidades para Teste

Setor executar o SQL INSERT INTO setor VALUES (1,'Pediatria')

Apos Colocar um setor coloque um Preceptor

Para colocar um preceptor faça uma requisição POST para http://localhost:8080/preceptor/create 

Com o seguinte JSON no body de exemplo 

{
	"nome": "Juriscleia Fonseca",
	"matricula": "92243",
	"password": "123456",
	"idSetor": 1
}

### Nota Rotas de criação das Entidades no momento nao requerem autenticaçao por isso serao ultilizadas somente em modo de desenvolvimento

Estagiario 

Para colocar um estagiario faça uma requisição POST para http://localhost:8080/estagiario/create 
Exemplo
{
	"nome": "Juriscleia Fonseca Silva",
	"matricula": "3333",
	"password": "123456",
}

Para colocar um admin faça uma requisição POST para http://localhost:8080/admin/create 
Exemplo
{
	"nome": "Irineu",
	"matricula": "7777",
	"password": "123456",
}

### Usando o APP

Os aplicativos do estagiario e preceptor sao logados com a matricula como username e password e a password

A aplicação que disponibiliza o QRCode automaticamente carrega os setores disponiveis no backend

### Visualização de CheckIns Abertos

A visualização dos checkIns abertos e determinada pela existencia de um JSON no Redis

para visualizalos para acessar http://localhost:8001 para entrar no redisinsignt

coloque as configs obrigatorias Host = redis-compose (ou IP do container) port = 6379 name = redis (ou qualquer outro)















