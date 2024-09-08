# Etapa 1: Build da aplicação React com Vite
FROM node:18-alpine AS build

# Definir o diretório de trabalho
WORKDIR /app

# Copiar os arquivos de configuração e dependências
COPY package.json yarn.lock ./

# Instalar dependências usando Yarn
RUN yarn install

# Copiar o restante do código da aplicação
COPY . .

# Build da aplicação para produção
RUN yarn build

# Etapa 2: Configuração do NGINX para servir os arquivos
FROM nginx:alpine AS final

# Copiar a build da aplicação para o diretório de assets do NGINX
COPY --from=build /app/build /usr/share/nginx/html

# Copiar um arquivo de configuração NGINX personalizado, se necessário
# COPY nginx.conf /etc/nginx/conf.d/default.conf

# Expor a porta padrão do NGINX
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]