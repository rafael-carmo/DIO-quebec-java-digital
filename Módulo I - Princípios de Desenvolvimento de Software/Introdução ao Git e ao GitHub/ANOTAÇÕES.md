## Gerando chave SSH
Como configurar chaves no gitHub:
1 - Configurações
2 - SSH and GPG Keys
3 - SSH Keys -> New SSH Key
4 - depois de gerar a chave pelo git, colar chave no campo Key.

Gerando chaves SSH no git:
1 - Entrar no git bash
2 - ssh-keygen -t ed25519 -C email@email.com 
ed25519: tipo de criptografia da chave
email: de preferencia o email que usa no github
OBS: verificar pasta onde as chaves vão ser geradas
3 - Navegar até a pasta onde estão as chaves e executar o comando para abrir o arquivo
com a chave pública:
cat id_ed25519.pub (verificar qual arquivo tem a extensão .pub, esse é o arquivo com a chave
publica)
4 - copiar dados da chave pública e colar no github. Colocar um title para identificar a máquina
que possui aquela chave.
5 - Incializar o ssh agent, que é o responsavel por gerenciar as chaves (tem que ser executado
dentro da pasta onde ficam as chaves):
-> eval $(ssh-agent -s)
- esse comando starta o processo para rodar em plano de fundo
6 -Passar chave privada para o ssh agent:
-> ssh-add nome_da_chave_privada


OBS: Este processo pode ser feito para várias máquinas (confiaveis), evitando de ter que colocar usuário
e senha, toda vez que for fazer um commit
OBS: Depois de ter feito a geração de um SSH numa máquina, vc não conseguirá mais clonar um repositorio
do github pelo metodo HTTPS, terá que usar a opção de SSH

## Gerando Token de acesso pessoal
Como configurar token no gitHub:
1 - Configurações
2 - Developer Settings
3 - PErsonal access tokens
4 - Generate new token
5 - Escrever uma nota para este token -> Marcar opção Repo
6 - Botão Genrate Token
7 - Após gerar o token, guardá-lo em algum lugar, pois não será mais possivel visuáliza-lo.
terá que fazer o processo todo de novo para geração de um novo token
OBS: ao clonar um repositorio, utilizar a opção https, será pedido o token.

## Comandos Git
-> git init
-inicializa um repositorio git, numa pasta oculta .git
- para listar os arquivos ocultos (ls -a)

-> git config --global user.email "email@email.com"
-> git config --global user.name "name"
- Configurando usuario e email, pode ser de forma global para maquina ou apenas para o repositorio

-> git add *
- Adiciona os arquivos na stage area, que entrarão no proximo commit

-> git commit -m "no do commit"
- Coloca os arquivos da stage area no repositorio local

-> git restore --staged <file>
- Retira o arquivo da staged e coloca no estado anterior
