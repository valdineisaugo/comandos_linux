# Comandos Linux Básicos para GitHub Codespaces

## Navegação e Gerenciamento de Arquivos

| Comando | Descrição | Exemplo |
|---------|-----------|---------|
| `pwd` | Mostra o diretório atual (Print Working Directory) | `pwd` |
| `ls` | Lista arquivos e diretórios | `ls` |
| `ls -la` | Lista detalhada incluindo arquivos ocultos | `ls -la` |
| `cd` | Muda de diretório (Change Directory) | `cd /pasta/subpasta` |
| `cd ..` | Volta um diretório | `cd ..` |
| `cd ~` | Vai para o diretório home | `cd ~` |
| `mkdir` | Cria um diretório | `mkdir nova-pasta` |
| `rmdir` | Remove um diretório vazio | `rmdir pasta-vazia` |
| `rm` | Remove arquivos | `rm arquivo.txt` |
| `rm -rf` | Remove diretórios e seu conteúdo (use com cuidado) | `rm -rf pasta` |
| `cp` | Copia arquivos | `cp origem.txt destino.txt` |
| `cp -r` | Copia diretórios recursivamente | `cp -r pasta1 pasta2` |
| `mv` | Move ou renomeia arquivos/diretórios | `mv arquivo.txt nova-pasta/` |
| `touch` | Cria um arquivo vazio | `touch novo-arquivo.txt` |
| `cat` | Mostra o conteúdo de um arquivo | `cat arquivo.txt` |
| `less` | Visualiza arquivos com paginação | `less arquivo-grande.txt` |
| `head` | Mostra as primeiras linhas de um arquivo | `head -n 10 arquivo.txt` |
| `tail` | Mostra as últimas linhas de um arquivo | `tail -n 10 arquivo.txt` |
| `find` | Busca arquivos e diretórios | `find . -name "*.js"` |
| `grep` | Busca texto em arquivos | `grep "texto" arquivo.txt` |

## Permissões

| Comando | Descrição | Exemplo |
|---------|-----------|---------|
| `chmod` | Muda permissões de arquivos/diretórios | `chmod 755 script.sh` |
| `chmod +x` | Torna um arquivo executável | `chmod +x script.sh` |
| `chown` | Muda o proprietário de arquivos/diretórios | `chown usuario arquivo.txt` |

## Informações do Sistema

| Comando | Descrição | Exemplo |
|---------|-----------|---------|
| `uname -a` | Mostra informações do sistema | `uname -a` |
| `df -h` | Mostra espaço em disco (human-readable) | `df -h` |
| `du -sh` | Mostra tamanho de pastas (human-readable) | `du -sh /pasta` |
| `free -h` | Mostra uso de memória | `free -h` |
| `top` | Mostra processos em execução (interativo) | `top` |
| `ps aux` | Lista todos os processos em execução | `ps aux` |
| `ps aux | grep nome` | Busca processo específico | `ps aux | grep node` |
| `kill` | Encerra um processo pelo PID | `kill 1234` |
| `killall` | Encerra processos pelo nome | `killall node` |

## Rede

| Comando | Descrição | Exemplo |
|---------|-----------|---------|
| `ping` | Testa conectividade com um host | `ping github.com` |
| `wget` | Baixa arquivos da web | `wget https://url/arquivo.zip` |
| `curl` | Transfere dados via URL | `curl https://api.github.com` |
| `ifconfig` ou `ip addr` | Mostra interfaces de rede | `ip addr` |
| `netstat -tuln` | Lista portas abertas | `netstat -tuln` |
| `ssh` | Conexão segura a servidores remotos | `ssh usuario@servidor` |

## Compressão e Arquivamento

| Comando | Descrição | Exemplo |
|---------|-----------|---------|
| `tar -czvf` | Cria arquivo tar.gz | `tar -czvf arquivo.tar.gz pasta/` |
| `tar -xzvf` | Extrai arquivo tar.gz | `tar -xzvf arquivo.tar.gz` |
| `zip` | Cria arquivo zip | `zip -r arquivo.zip pasta/` |
| `unzip` | Extrai arquivo zip | `unzip arquivo.zip` |

## Editores de Texto

| Comando | Descrição | Exemplo |
|---------|-----------|---------|
| `nano` | Editor de texto simples | `nano arquivo.txt` |
| `vim` | Editor de texto avançado | `vim arquivo.txt` |
| `code` | Abre arquivo no VS Code (disponível no Codespaces) | `code arquivo.txt` |

## Git (integrado no Codespaces)

| Comando | Descrição | Exemplo |
|---------|-----------|---------|
| `git status` | Mostra o estado atual do repositório | `git status` |
| `git add` | Adiciona arquivos para commit | `git add arquivo.txt` |
| `git commit` | Cria um commit com os arquivos adicionados | `git commit -m "Mensagem"` |
| `git pull` | Atualiza o repositório local | `git pull origin main` |
| `git push` | Envia commits para o repositório remoto | `git push origin main` |
| `git branch` | Lista branches | `git branch` |
| `git checkout` | Muda para outra branch | `git checkout nova-branch` |
| `git checkout -b` | Cria e muda para uma nova branch | `git checkout -b nova-branch` |

## Comandos para DevOps

| Comando | Descrição | Exemplo |
|---------|-----------|---------|
| `docker ps` | Lista contêineres Docker em execução | `docker ps` |
| `docker images` | Lista imagens Docker | `docker images` |
| `docker run` | Executa um contêiner Docker | `docker run -it ubuntu bash` |
| `npm install` | Instala pacotes Node.js | `npm install express` |
| `npm start` | Inicia aplicação Node.js | `npm start` |
| `python -m venv` | Cria ambiente virtual Python | `python -m venv env` |
| `source env/bin/activate` | Ativa ambiente virtual Python | `source env/bin/activate` |

## Dicas para Codespaces

1. No Codespaces, você já está logado no Git e não precisa configurar credenciais

2. Use `code .` para abrir o diretório atual no editor VS Code integrado

3. O terminal no Codespaces suporta múltiplas abas (guias) - clique no ícone + para abrir mais terminais

4. Você pode instalar extensões adicionais do VS Code diretamente no Codespaces

5. Para economizar horas de uso, lembre-se de parar seu Codespace quando não estiver usando