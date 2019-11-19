# TFTP-Container
Servidor de provisionamento utilizando docker e tftp

mkdir /var/lib/tftpboot
chmod 777  /var/lib/tftpboot

Encaminhar os arquivos “SEP’ mais o mac do aparelho’.cnf.xml e dialplan.xml ” para o diretório criado acima.

Exemplo:
SEPE8EDF3AAA0CF.cnf.xml

E8EDF3AAA0CF = mac do aparelho.

Procedimento de instalação e configuração do docker: wiki_id=282

Download do arquivo:
wget http://crm.totalip.com.br/files/totalip-tftp.tar

docker load --input totalip-tftp.tar

docker run -dit --name tftp --restart=always --privileged  -v /var/lib/tftpboot:/var/lib/tftpboot -p 69:69/udp totalip/tftp:1.0

--name tftp - Nome do arquivo.
-v /var/lib/tftpboot:/var/lib/tftpboot - Diretório onde irá ficar o arquivo do provisionamento.
kaue/tftp - Imagem do docker.
-p 69:69/udp - Liberar porta para acesso ao container
--restart=always - caso o container morra, inicie automaticamente.