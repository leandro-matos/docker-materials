
# Containers - Day02

### Important:
Tipo Bind: Já possuo o diretório e quero montar dentro do container;
Tipo Volume: Mais recomendado, Compartilhamento de dados entre múltiplos containers

### Questions:
1) Quando criamos um volume do tipo bind, quais os parâmetros para indicar onde o volume será montado no container?
Resp: dst ou destionation

2) Quando criamos um volume do tipo volume, quais os parâmetros para indicar o nome do volume que será montado no container?
Resp: src ou source

3) É possível montar um volume como somente leitura em um container?
Resp: Sim

4) Qual o parâmetro para montar um volume em um container como somente leitura?
Resp: ro

5) Quando o container é removido, o volume também será removido?
Resp Não

6) Qual o comando para montar um volume do tipo volume em um container?
Resp: #docker container run -d --mount type=volume,src=origem, destination=/var/opt/dest nginx

7) Qual o comando utilizado para criar um volume?
Resp: #docker volume create giropops

8) Qual o comando para remover um volume?
Resp #docker volume rm giropops

9) Qual o comando utilizado para listar todos os volumes?
Resp: #docker volume ls

10) Qual o comando utilizado para remover todos os volumes que não estão sendo utilizado por nenhum container?
Resp: #docker volume prune

11) Qual o comando para montar um volume do tipo bind em um container?
Resp: #docker container run -ti --mount type=bind,src=/root/container,dst=/volume ubuntu

12) Qual o diretório no host onde ficam os volumes criados?
Resp: /var/lib/docker/volumes

13) Qual o comando utilizado para ver detalhes sobre um determinado volume?
Resp: #docker volume inspect giropops

## Comandos Úteis para entendimento sobre o Docker:
# docker container run -ti --mount type=bind,src=/volume,dst=/volume ubuntu
# docker container run -ti --mount type=bind,src=/root/primeiro_container,dst=/volume ubuntu
# docker container run -ti --mount type=bind,src=/root/primeiro_container,dst=/volume,ro ubuntu
# docker volume create giropops
# docker volume rm giropops
# docker volume inspect giropops
# docker volume prune
# docker container run -d --mount type=volume,source=giropops,destination=/var/opa  nginx
# docker container create -v /data --name dbdados centos
# docker run -d -p 5432:5432 --name pgsql1 --volumes-from dbdados -e POSTGRESQL_USER=docker -e POSTGRESQL_PASS=docker -e POSTGRESQL_DB=docker kamui/postgresql
# docker run -d -p 5433:5432 --name pgsql2 --volumes-from dbdados -e  POSTGRESQL_USER=docker -e POSTGRESQL_PASS=docker -e POSTGRESQL_DB=docker kamui/postgresql
# docker run -ti --volumes-from dbdados -v $(pwd):/backup debian tar -cvf /backup/backup.tar /data

Forma Antiga:
#### docker container create -v /data --name dbdados centos
#### docker run -d -p 5432:5432 --name pgsql1 --volumes-from dbdados -e POSTGRESQL_USER=docker -e POSTGRESQL_PASS=docker -e POSTGRESQL_DB=docker kamui/postgresql

Forma Nova:
#### docker volume create dbdados
#### docker run -d -p 5433:5432 --mount type=volume,src=dbdados,dst=/data -e POSTGRESQL_USER=docker -e POSTGRESQL_PASS=docker -e POSTGRESQL_DB=docker kamui/postgresql
#### docker volume inspect dbdados

Backup dos Dados:
#### docker container run -ti --mount type=volume,src=dbdados,dst=/data --mount type=bind,src=G:\docker\projetos\backup,dst=/backup debian tar -cvf /backup/bkpbanco.tar /data
#### tar -xvf .\bkpbanco.tar

