# 10 Atividades Práticas para Comandos Linux no Codespaces

## Atividade 1: Explorando o Sistema de Arquivos
**Objetivo:** Aprender a navegar e manipular arquivos e diretórios.

**Passos:**
1. Crie uma estrutura de diretórios para um projeto fictício:
   ```bash
   mkdir -p projeto/src/{components,pages,utils} projeto/docs projeto/tests
   ```
2. Navegue entre os diretórios usando `cd` e confirme sua localização com `pwd`
3. Liste a estrutura de diretórios completa usando:
   ```bash
   find projeto -type d | sort
   ```
4. Crie alguns arquivos vazios em diferentes diretórios:
   ```bash
   touch projeto/src/index.js
   touch projeto/src/components/Button.js
   touch projeto/src/utils/helpers.js
   touch projeto/docs/README.md
   ```
5. Use comandos para listar, copiar, mover e renomear arquivos:
   ```bash
   ls -la projeto/src/
   cp projeto/src/index.js projeto/src/main.js
   mv projeto/docs/README.md projeto/README.md
   ```

## Atividade 2: Trabalhando com Conteúdo de Arquivos
**Objetivo:** Aprender a criar, visualizar e manipular conteúdo de arquivos.

**Passos:**
1. Crie um arquivo com conteúdo usando o redirecionamento:
   ```bash
   echo "# Meu Projeto" > projeto/README.md
   echo -e "Esta é a documentação do projeto.\n\n## Estrutura de Diretórios" >> projeto/README.md
   ```
2. Visualize o conteúdo usando diferentes comandos:
   ```bash
   cat projeto/README.md
   head -n 1 projeto/README.md
   tail -n 2 projeto/README.md
   ```
3. Adicione conteúdo a um arquivo JavaScript:
   ```bash
   cat > projeto/src/utils/helpers.js << 'EOF'
   /**
    * Função auxiliar para formatar data
    */
   export function formatDate(date) {
     return new Date(date).toLocaleDateString();
   }

   /**
    * Função auxiliar para validar email
    */
   export function validateEmail(email) {
     const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
     return regex.test(email);
   }
   EOF
   ```
4. Busque por uma palavra específica nos arquivos:
   ```bash
   grep -r "function" projeto/
   ```

## Atividade 3: Gerenciando Processos
**Objetivo:** Aprender a iniciar, monitorar e controlar processos.

**Passos:**
1. Instale uma aplicação Node.js simples:
   ```bash
   mkdir app-teste
   cd app-teste
   npm init -y
   npm install express
   ```
2. Crie um servidor simples:
   ```bash
   cat > server.js << 'EOF'
   const express = require('express');
   const app = express();
   
   app.get('/', (req, res) => {
     res.send('Servidor de teste para monitoramento de processos');
   });
   
   app.listen(3000, () => {
     console.log('Servidor rodando na porta 3000');
   });
   EOF
   ```
3. Inicie o servidor em background:
   ```bash
   node server.js &
   ```
4. Verifique os processos em execução:
   ```bash
   ps aux | grep node
   ```
5. Encontre o PID (ID do processo) e termine o processo:
   ```bash
   kill $(pgrep -f "node server.js")
   ```
6. Confirme que o processo foi terminado:
   ```bash
   ps aux | grep node
   ```

## Atividade 4: Redirecionamento e Pipes
**Objetivo:** Aprender a redirecionar entrada/saída e conectar comandos.

**Passos:**
1. Crie um arquivo com uma lista de frutas:
   ```bash
   cat > frutas.txt << 'EOF'
   maçã
   banana
   laranja
   abacaxi
   morango
   uva
   pêssego
   melancia
   kiwi
   manga
   EOF
   ```
2. Ordene o arquivo e salve em um novo arquivo:
   ```bash
   sort frutas.txt > frutas_ordenadas.txt
   ```
3. Conte o número de linhas, palavras e caracteres:
   ```bash
   wc frutas.txt
   ```
4. Filtre as frutas que começam com 'm' e conte-as:
   ```bash
   grep "^m" frutas.txt | wc -l
   ```
5. Combine múltiplos comandos para criar um arquivo de estatísticas:
   ```bash
   echo "Estatísticas do arquivo frutas.txt:" > estatisticas.txt
   echo "Total de frutas: $(wc -l < frutas.txt)" >> estatisticas.txt
   echo "Frutas que começam com 'a': $(grep "^a" frutas.txt | wc -l)" >> estatisticas.txt
   echo "Frutas em ordem alfabética:" >> estatisticas.txt
   sort frutas.txt >> estatisticas.txt
   ```

## Atividade 5: Permissões de Arquivos
**Objetivo:** Aprender a gerenciar permissões de arquivos e diretórios.

**Passos:**
1. Crie um script shell simples:
   ```bash
   cat > script.sh << 'EOF'
   #!/bin/bash
   echo "Hoje é $(date)"
   echo "Usuário atual: $USER"
   echo "Diretório atual: $(pwd)"
   ls -la
   EOF
   ```
2. Verifique as permissões atuais:
   ```bash
   ls -l script.sh
   ```
3. Adicione permissão de execução:
   ```bash
   chmod +x script.sh
   ```
4. Execute o script:
   ```bash
   ./script.sh
   ```
5. Experimente diferentes configurações de permissão:
   ```bash
   chmod 755 script.sh  # Permissão total para dono, leitura/execução para outros
   chmod 700 script.sh  # Apenas o dono pode ler/escrever/executar
   ```
6. Crie um diretório com permissões específicas:
   ```bash
   mkdir dados_restrito
   chmod 700 dados_restrito
   ```

## Atividade 6: Compressão e Arquivamento
**Objetivo:** Aprender a comprimir e descomprimir arquivos.

**Passos:**
1. Crie mais alguns arquivos para teste:
   ```bash
   mkdir dados
   for i in {1..5}; do 
     echo "Este é o arquivo de dados $i" > dados/arquivo$i.txt
   done
   ```
2. Crie um arquivo tar:
   ```bash
   tar -cvf dados.tar dados/
   ```
3. Crie um arquivo tar comprimido com gzip:
   ```bash
   tar -czvf dados.tar.gz dados/
   ```
4. Compare os tamanhos:
   ```bash
   ls -lh dados.tar dados.tar.gz
   ```
5. Extraia o arquivo comprimido em um novo diretório:
   ```bash
   mkdir restaurado
   tar -xzvf dados.tar.gz -C restaurado/
   ```
6. Compare os diretórios original e restaurado:
   ```bash
   diff -r dados/ restaurado/dados/
   ```

## Atividade 7: Sistema de Busca Avançada
**Objetivo:** Aprender a encontrar arquivos e conteúdo no sistema.

**Passos:**
1. Crie arquivos com diferentes extensões:
   ```bash
   mkdir -p projeto-busca/{src,docs,config}
   touch projeto-busca/src/{app.js,style.css,index.html}
   touch projeto-busca/docs/{manual.pdf,guia.md}
   touch projeto-busca/config/{dev.json,prod.json}
   ```
2. Adicione conteúdo a alguns arquivos:
   ```bash
   echo '{"ambiente": "desenvolvimento", "debug": true}' > projeto-busca/config/dev.json
   echo '{"ambiente": "produção", "debug": false}' > projeto-busca/config/prod.json
   echo "# Guia do Usuário" > projeto-busca/docs/guia.md
   ```
3. Busque todos os arquivos JavaScript:
   ```bash
   find projeto-busca -name "*.js"
   ```
4. Busque arquivos modificados nas últimas 24 horas:
   ```bash
   find projeto-busca -type f -mtime -1
   ```
5. Busque arquivos com conteúdo específico:
   ```bash
   grep -r "ambiente" projeto-busca/
   ```
6. Encontre todos os diretórios vazios:
   ```bash
   find projeto-busca -type d -empty
   ```

## Atividade 8: Monitoramento de Recursos
**Objetivo:** Aprender a monitorar recursos do sistema.

**Passos:**
1. Verifique o uso de disco:
   ```bash
   df -h
   ```
2. Verifique o tamanho de diretórios específicos:
   ```bash
   du -sh projeto-busca/
   du -sh --max-depth=1 ./
   ```
3. Monitore o uso de memória:
   ```bash
   free -h
   ```
4. Visualize os processos em execução:
   ```bash
   ps aux
   ```
5. Use o top para monitoramento em tempo real:
   ```bash
   top
   ```
   (Pressione 'q' para sair)
6. Crie um script para gerar um relatório de recursos:
   ```bash
   cat > monitor.sh << 'EOF'
   #!/bin/bash
   echo "==== RELATÓRIO DE RECURSOS $(date) ===="
   echo -e "\n== USO DE DISCO =="
   df -h
   echo -e "\n== USO DE MEMÓRIA =="
   free -h
   echo -e "\n== PROCESSOS MAIS ATIVOS =="
   ps aux --sort=-%cpu | head -n 5
   EOF
   
   chmod +x monitor.sh
   ./monitor.sh > relatorio_recursos.txt
   ```

## Atividade 9: Configuração de Ambiente de Desenvolvimento
**Objetivo:** Configurar um ambiente de desenvolvimento web básico.

**Passos:**
1. Crie um novo projeto web:
   ```bash
   mkdir web-project
   cd web-project
   ```
2. Inicialize um repositório Git:
   ```bash
   git init
   ```
3. Crie uma estrutura básica de projeto:
   ```bash
   mkdir -p src/{css,js,img} public
   touch src/index.html src/css/style.css src/js/main.js
   ```
4. Adicione conteúdo ao HTML:
   ```bash
   cat > src/index.html << 'EOF'
   <!DOCTYPE html>
   <html lang="pt-br">
   <head>
     <meta charset="UTF-8">
     <meta name="viewport" content="width=device-width, initial-scale=1.0">
     <title>Projeto Web</title>
     <link rel="stylesheet" href="css/style.css">
   </head>
   <body>
     <h1>Meu Projeto Web</h1>
     <p>Este é um projeto para praticar comandos Linux.</p>
     <script src="js/main.js"></script>
   </body>
   </html>
   EOF
   ```
5. Inicialize npm e instale algumas dependências:
   ```bash
   npm init -y
   npm install --save-dev http-server
   ```
6. Adicione um script para iniciar o servidor:
   ```bash
   # Adicionando script ao package.json
   sed -i 's/"scripts": {/"scripts": {\n    "start": "http-server src -p 8080",/' package.json
   ```
7. Configure o .gitignore:
   ```bash
   echo -e "node_modules/\n.DS_Store\n*.log" > .gitignore
   ```
8. Adicione arquivos ao Git e faça o primeiro commit:
   ```bash
   git add .
   git status
   git commit -m "Configuração inicial do projeto web"
   ```

## Atividade 10: Automação com Shell Script
**Objetivo:** Criar um script para automatizar tarefas de desenvolvimento.

**Passos:**
1. Crie um script para automatizar a inicialização de um projeto:
   ```bash
   cat > criar_projeto.sh << 'EOF'
   #!/bin/bash
   
   # Script para inicializar um novo projeto
   
   if [ -z "$1" ]; then
     echo "Por favor, forneça um nome para o projeto"
     echo "Uso: ./criar_projeto.sh nome-do-projeto [tipo]"
     echo "Tipos disponíveis: node, web (padrão: web)"
     exit 1
   fi
   
   NOME_PROJETO=$1
   TIPO_PROJETO=${2:-web}
   
   echo "Criando projeto '$NOME_PROJETO' do tipo '$TIPO_PROJETO'..."
   
   # Criar diretório do projeto
   mkdir -p $NOME_PROJETO
   cd $NOME_PROJETO
   
   # Inicializar Git
   git init
   echo -e "node_modules/\n.DS_Store\n*.log\ndist/\n.env" > .gitignore
   
   # Configuração baseada no tipo
   case $TIPO_PROJETO in
     node)
       # Configuração para projeto Node.js
       npm init -y
       mkdir -p src/{controllers,models,routes,services,utils}
       touch src/index.js
       
       # Adicionar dependências comuns
       npm install express dotenv
       npm install --save-dev nodemon
       
       # Configurar scripts
       sed -i 's/"scripts": {/"scripts": {\n    "start": "node src\/index.js",\n    "dev": "nodemon src\/index.js",/' package.json
       
       # Criar arquivo de exemplo
       cat > src/index.js << 'NODEJS'
   const express = require('express');
   const app = express();
   
   app.use(express.json());
   
   app.get('/', (req, res) => {
     res.json({ message: 'API funcionando!' });
   });
   
   const PORT = process.env.PORT || 3000;
   app.listen(PORT, () => console.log(`Servidor rodando na porta ${PORT}`));
   NODEJS
       ;;
     
     web)
       # Configuração para projeto Web
       mkdir -p src/{css,js,img} public
       
       # Criar arquivos básicos
       cat > src/index.html << 'HTML'
   <!DOCTYPE html>
   <html lang="pt-br">
   <head>
     <meta charset="UTF-8">
     <meta name="viewport" content="width=device-width, initial-scale=1.0">
     <title>Meu Projeto Web</title>
     <link rel="stylesheet" href="css/style.css">
   </head>
   <body>
     <h1>Meu Projeto Web</h1>
     <p>Conteúdo inicial do projeto.</p>
     <script src="js/main.js"></script>
   </body>
   </html>
   HTML
       
       touch src/css/style.css src/js/main.js
       
       # Configurar npm
       npm init -y
       npm install --save-dev http-server
       
       # Configurar scripts
       sed -i 's/"scripts": {/"scripts": {\n    "start": "http-server src -p 8080",/' package.json
       ;;
     
     *)
       echo "Tipo de projeto não reconhecido: $TIPO_PROJETO"
       echo "Tipos disponíveis: node, web"
       exit 1
       ;;
   esac
   
   # Primeiro commit
   git add .
   git commit -m "Configuração inicial do projeto $NOME_PROJETO"
   
   echo -e "\nProjeto '$NOME_PROJETO' criado com sucesso!"
   echo "Para iniciar o projeto:"
   echo "  cd $NOME_PROJETO"
   echo "  npm start"
   EOF
   ```
2. Torne o script executável:
   ```bash
   chmod +x criar_projeto.sh
   ```
3. Execute o script para criar um novo projeto:
   ```bash
   ./criar_projeto.sh meu-site web
   ```
4. Navegue até o projeto criado e verifique sua estrutura:
   ```bash
   cd meu-site
   ls -la
   git log
   ```
5. Inicie o servidor para testar:
   ```bash
   npm start
   ```
   (O Codespaces deve detectar a porta e permitir visualizar o site)