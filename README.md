# Kubernete

## Atividade
- Crie um namespace chamado labwordpress, tudo o que for feito deverá estar dentro deste namespace;

- Faça o apply do arquivo de service do MySQL mude a porta padrão do banco MySQL para 3308;

- Crie o arquivo secret que deverá conter o password do banco MySQL, lembre-se de criar uma senha com fortes padrões de segurança;

- Faça o apply do arquivo de PersistentVolumeClaim do MySQL para um capacity de 3GB;

- Faça o apply do arquivo de deployment do MySQL, crie também um volume mount no deployment do MySQL chamado “mysql-persistent-storagelab", apontando para /var/lib/mysql. Lembre-se de criar o volume em si com o mesmo nome do volume mount;

- Faça o apply do arquivo de service do Wordpress altere para a TCP Port 80;

- Faça o apply do arquivo de PersistentVolumeClaim do Wordpress, para um capacity de 3GB;

- No arquivo de deployment do Wordpress, crie um volume mount no deployment do Wordpress chamado “wordpresspersistent-storage-lab", apontando para /var/www/html. Lembre-se de criar o volume em si com o mesmo nome do volume mount;

- No arquivo de deployment do wordpress, insira o secret contendo o password do MySQL, criado no começo do exercício.

- Faça o apply do arquivo de deployment do wordpress;

- Verifque se os pods, os services e os pvcs foram criados da forma correta dentro namespace criado no início deste exercício;

- Verifique qual foi a URI gerada através do ingress do kubernetes;

- Copie essa URI do Ingress e cole no browser para abrir a tela inicial do wordpress

- Criar documentação

## Documentação:

### Criar namespace:

kubectl create namespace labwordpress

- Verificar se o nemaspace foi criado:

kubectl get namespaces

### Definir o contexto como labwordpress:

- Verificar as configurações do Cluster e User:

kubectl config view

- Configura no Docker for windows:

kubectl config set-context labwordpress --namespace=labwordpress --user=docker-desktop --cluster=docker-desktop

- Configura no minikube:

kubectl config set-context labwordpress --namespace=labwordpress --user=minikube --cluster=minikube

- ativar o contexto labwordpress:

kubectl config use-context labwordpress

kubectl config current-context


## Implementar os arquivos do Secret, MySql e WordPress:

- Entre na pasta onde os arquivos estão e digete o comando:

kubectl apply -k ./

- Consulta para ver se foram criados:

kubectl get all

- consultar a url para ver no navegador:

kubectl -n ingress get svc wordpress --namespace=labwordpress /// windows

minikube service wordpress --url --namespace=labwordpress /// linux


- Apaga os container criados

kubectl delete -k ./ --namespace=labwordpress
