

* Entrypoint: principal processo do container, como se fosse o init;
* CMD: O CMD precisa passar os parametros para o processo;

### Comandos Úteis para entendimento sobre o Docker:
01) docker image build -t apache_modify:1.0 .
02) docker container run -d -p 8080:80 apache_modify:1.0
03) docker image build -t go_app:1.0 . 
04) docker run -p 8080:8081 -it my-go-app