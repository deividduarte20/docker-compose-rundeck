# Provê container com rundeck

## Para executar o container
docker-compose up -d

## Para adicionar nodes, crie o diretório com o comando abaixo alterando nome_projeto para o seu projeto
mkdir -p /var/rundeck/projects/nome_projeto/etc

Entre no diretório criado acima
cd /var/rundeck/projects/nome_projeto/etc

## Crie o arquivo resources.xml
touch resources.xml

## Insira o conteúdo abaixo no arquivo resources.xml e substitua o ip
<project>
<node name="my-node" hostname="10.0.0.25" osArch="amd64" osFamily="unix" osName="Linux" osVersion="3.11.10-03111015-generic" username="rundeck"/>
</project>


## Atribua o usuário rundeck como dono
chown rundeck:rundeck /var/rundeck/projects/nome_projeto/etc/resources.xml

## Reinicie o serviço
service rundeckd restart



