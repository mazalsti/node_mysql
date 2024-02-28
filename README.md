Arquivos do módulo inicial de Node + Typescript, da estrutura MVC aplicada.

### Pré-requisitos globais:
`npm i -g nodemon typescript ts-node`

### Instalação
`npm install`

### Para rodar o projeto
`npm run start-dev`

### ------------------------------------------------------------------------
criar uma projeto node: npm init -y
instalar typescript: tsc --init
instalar node_modules: npm install --save-dev @types/node
install nodemon: npm install nodemon 
instalar ts-node:  npm install ts-node
instalar types do express: npm install @types/express 
instalar template mustache: npm install mustache-express
instalar types mustache: npm install --save-dev @types/mustache-express
conf no tsconfig "moduleResolution" = node
conf no arq tscongif "outDir": "./Dist", 
conf no arq tscongif "rootDir": "./src",
conf no arq tagerte: ES6 
### ------------------------------------------------------------------------
configurando variavel de ambiente
comando para instalar: npm install dotenv
importa: import dotenv from 'dotenv';
chama a variavel: dotenv.config();
passa no server: server.listen(process.env.PORT);

### -------------------------------------------------------------------------
//configurando o mustache no engine
server.set('view engine', 'mustache');
// vincular os arquivos da views 
server.set('views', path.join(__dirname, 'views'));
server.engine('mustache', mustache());
server.use(express.static(path.join(__dirname,'../public')))
// server.use(express.static('public'))
server.use(express.urlencoded({extended: true}));

### ---------------------------------------------------------------------------
O que funcionou para mim foi seguir as etapas recomendadas na sequência exata:
Em casos raros, o cache npm pode ficar corrompido. Para mim, o que funcionou foi:
1 - npm cache clean --force
1.1 - Delete node_module folder
2 - Delete package-lock.json
2.1 - npm uninstall
3 - npm install
4 - npm install typescript
5 - npm link typescript
6 - npm run start
--- Verifique se você instalou expresso módulo. Caso contrário, use este comando:
6.1 - npm install --save express
6.2 - npm install express 
7 - For any further missing dependencies do npm install [dep] followed by npm link [dep]
E se o seu node_modulesdiretório estiver em outro lugar, defina NODE_PATHa variável de ambiente:
8 - set NODE_PATH=your\directory\to\node_modules;%NODE_PATH%