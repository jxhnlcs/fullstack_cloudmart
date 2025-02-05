FROM node:18
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 5000
CMD ["npm", "start"]

# docker build -t cloudmart-backend .
# docker run -d -p 5000:5000 --env-file .env cloudmart-backend
