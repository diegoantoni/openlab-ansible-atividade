# ATIVIDADE ANSIBLE - VAGRANT E ANSIBILE 
- Subindo wordpress de forma automatizada utilizando vagrant para provisionar a maquina
  virtual e ansible para provisionar os recursos dentro da vm

# EXECUTANDO O PROJETO
- Clone o repositorio no seu computador 
- Abra um terminal e navegue ate a raiz do projeto onde tenha o arquivo Vagrantfile
- execute o seguinte comando:
  ~$ vagrant up 
  
# AJUSTANDO O /ETC/HOSTS PARA ACESSO AO WORPRESS
- Adicione uma entra no /etc/hosts da sua maquina local
 ~$ sudo vim /etc/hosts
 - adicione dentro do arquivo:
    192.168.56.50 wordpress wordpress.atividade.example
 - Salve e saia do arquivo
  
 # TESTANDO O PROJETO
 - Abra um navegador e digite o seguinte link:
 - http://wordpress.atividade.example
 - Deve aparecer a pagina do wordpress solicitando usuario e senha
