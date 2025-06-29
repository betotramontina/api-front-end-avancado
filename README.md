
Conectar wsl ubuntu
open integrated terminal
$ python3 -m venv venv_api
$ source venv_api/bin/activate
Passo 1: Abrir um novo terminal no VS Code conectado ao WSL

Se você tiver um terminal em execução no VS Code que não seja o WSL, feche-o.

Abra um novo terminal no VS Code: Terminal > New Terminal ou Ctrl+Shift+ (backtick).

Verifique: No cabeçalho do terminal, ele deve indicar algo como bash (WSL) ou zsh (WSL). No rodapé do VS Code, o indicador verde deve mostrar WSL: Ubuntu. Isso confirma que você está no ambiente certo.

Passo 2: Atualizar os pacotes do Ubuntu no WSL

No terminal do VS Code (que está no WSL):

Bash

sudo apt update
sudo apt upgrade -y

Passo 3: Instalar o curl (se ainda não tiver)

Bash

sudo apt install curl -y

Passo 4: Instalar o NVM (Node Version Manager) no WSL

Este é o passo crucial. Substitua v0.39.7 pela versão mais recente do NVM se houver uma mais nova (verifique no GitHub nvm-sh/nvm).

Bash

curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh

Passo 5: Recarregar o ambiente do shell no WSL

Após a instalação do NVM, o script tenta modificar seu arquivo de configuração de shell (.bashrc ou .zshrc). Para que essas mudanças sejam aplicadas ao seu terminal atual, você precisa recarregá-lo.

Você pode fechar o terminal atual no VS Code e abrir um novo, ou executar o comando:

Bash

source ~/.bashrc

Passo 6: Verificar a instalação do NVM

No novo terminal do VS Code (ou após o source):

Bash

command -v nvm
Você deve ver nvm como saída.

Passo 7: Instalar o Node.js usando NVM no WSL

Agora que o NVM está funcionando, instale a versão do Node.js que seu projeto front-end exige. A versão LTS é geralmente a mais segura e recomendada para a maioria dos projetos.

Bash

nvm install --lts

Passo 8: Definir a versão do Node.js a ser usada (se você instalou várias ou quer garantir)

Bash

nvm use --lts # Para usar a versão LTS

pip install -U flask-openapi3[swagger,redoc,rapidoc,rapipdf,scalar,elements]







É fortemente indicado o uso de ambientes virtuais do tipo virtualenv.

(env)$ pip install -r requirements.txt
Este comando instala as dependências/bibliotecas, descritas no arquivo requirements.txt.

Para executar a API basta executar:

(env)$ flask run --host 0.0.0.0 --port 5000
Em modo de desenvolvimento é recomendado executar utilizando o parâmetro reload, que reiniciará o servidor automaticamente após uma mudança no código fonte.

(env)$ flask run --host 0.0.0.0 --port 5000 --reload
Abra o http://localhost:5000/#/ no navegador para verificar o status da API em execução.
