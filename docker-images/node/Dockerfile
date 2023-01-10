# Especificando a imagem que sera buscada no register (node versao 10)
FROM node:10

# Especificando o diretorio da imagem no qual todos os comandos serao executados
WORKDIR /usr/src/app

# Copia os arquivos do pacote e instala as dependencias
COPY package*.json ./
RUN npm install express
RUN npm install

# Copia todos arquivos da aplicacao para a imagem
COPY . .

# Definindo o comando default a ser executado quando o container foi iniciado
CMD [ "npm", "start" ]
