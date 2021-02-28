
# Containers - Day01

### Important:
Container não é virtualização;
Container é o isolamento lógico (processos, usuários, network, mount points);
Container dedica recursos da máquina (limitação) e isolar para o determinado Container;
Namespaces(recursos lógicos) e cgroups(recursos físicos);
Docker é uma das soluções de container;
Entrypoint: Principal processo do container;
01 CMD por dockerfile;

### Questions:
01) As camadas dos container são todas Read and Write? (Leitura e escrita) Não
02) Qual módulo do kernel Linux é o responsável pelo isolamento de processos? Namespaces
03) As imagens são compartilhadas entre os containers em execução? Não
04) Qual módulo do kernel Linux é o responsável pelo isolamento de recursos como CPU e memória? (Cgroups);
05) Qual módulo do kernel Linux é o responsável por criar rotas, redirects e boa parte da tarefa de roteamento de pacotes para o Docker? (NetFilter);
06) Qual é a versão paga do Docker? Docker EE (Enterprise Edition)
07) Qual o comando utilizado para verificar qual a versão do Docker instalado? Docker Version
08) Qual a URL para realizar a instalação do Docker através do comando curl? https://get.docker.com
09) Qual o comando que eu posso executar para visualizar todos os containers? #docker container ls -a
10) Qual o comando que eu posso executar para pausar determinado container? #docker container pausa [container id]
11) Como eu posso sair do container sem mata-lo? CTRL + p + q
12) Qual comando eu utilizo para que seja executado determinado comando dentro do container? #docker exec -ti [container id] [comando]
13) Qual comando é utilizado para ver detalhes sobre um container? #docker container inspect [container id]
14) Qual o comando utilizado para executar um container em modo daemon, sem interação e/ou terminal? #docker container run -ti nginx
15) Qual comando eu utilizo para capturar os logs de determinado container? #docker container logs -f [container id]
16) Qual comando eu utilizo para me conectar ao container? #docker container attach [container id]
17) Na saída de qual comando eu consigo pegar o IP de determinado container? #docker container inspect [container id]
18) Qual comando eu utilizo para ver o consumo de CPU e memória de determinado container? #docker container stats [container id]
19) Qual é o comando utilizado para limitar o consumo de memória de um container em 256M? #docker container run --memory 256 nginx
20) Qual o comando utilizado para realizar atualizações no container em execução? #docker container update
21) Qual o parâmetro para limitar a quantidade de CPU de um container? --cpus
22) Qual o comando para listar as imagens que estão no host? #docker image ls ou #docker images
23) Qual o nome do arquivo onde adiciono informações sobre a imagem que irei buildar? #DockerFile
24) Qual o comando utilizado para buildar (construir) uma imagem? #docker image build


## Comandos Úteis para entendimento sobre o Docker:
01) curl -fsSL https://get.docker.com/ | bash
02) docker version
03) docker container ls
04) docker container run hello-world
05) docker image ls
06) docker ps
07) docker container ls
08) docker container ls -a
09) docker container run -ti centos:7
10) docker container run -ti ubuntu
11) docker container -d nginx
12) docker container attach [CONTAINER ID]
13) docker container exec -ti [CONTAINER ID] [COMANDO]
14) docker container start [CONTAINER ID]
15) docker container stop [CONTAINER ID]
16) docker container restart [CONTAINER ID]
17) docker container pause [CONTAINER ID]
18) docker container unpause [CONTAINER ID]
19) docker container inspect [CONTAINER ID]
20) docker container logs -f [CONTAINER ID]
21) docker container rm [CONTAINER ID]
22) docker container rm -f [CONTAINER ID]
23) docker container exec -ti [CONTAINER ID] [COMANDO]
24) docker container run -d nginx
25) docker container stats [CONTAINER ID]
26) docker container top [CONTAINER ID]
27) docker container run -d -m 128M --cpus 0.5 nginx
28) docker container update --memory 64M --cpus 0.4 nginx
29) docker container inspect [CONTAINER ID]
30) docker container stats [CONTAINER ID]
31) docker container top [CONTAINER ID]

## Comando executados dentro do container:
01) apt-get update
02) apt-get install stress
03) stress --cpu 1 --vm-bytes 128M --vm1

## Criar DockerFile
01) docker image build -t [nome da imagem]:1.0
02) docker image ls
03) docker container run -d [nome da imagem]:1.0
04) docker container logs -f [CONTAINER ID]
