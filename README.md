# Provê container com rundeck

## Para executar o container
```bash
docker-compose up -d
```

## Listar os containers em execução
```bash
Docker ps
```

## Entrando no container
```bash
docker exec -it <ID DO CONTAINER> bash
```

## Para adicionar nodes, crie o diretório com o comando abaixo alterando nome_projeto para o seu projeto
```bash
mkdir -p /var/rundeck/projects/nome_projeto/etc
```

Entre no diretório criado acima
```bash
cd /var/rundeck/projects/nome_projeto/etc
```

## Crie o arquivo resources.xml
```bash
touch resources.xml
```
## Insira o conteúdo abaixo no arquivo resources.xml e substitua o ip
```xml
<project>
<node name="my-node" hostname="10.0.0.25" osArch="amd64" osFamily="unix" osName="Linux" osVersion="3.11.10-03111015-generic" username="rundeck"/>
</project>
```

## Atribua o usuário rundeck como dono
```bash
chown rundeck:rundeck /var/rundeck/projects/nome_projeto/etc/resources.xml
```

## Reinicie o serviço
```
service rundeckd restart
```


