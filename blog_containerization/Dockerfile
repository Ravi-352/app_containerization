FROM node:10-alpine

#RUN mkdir -p /app/node_modules && chown -R node:node /app

# Create app directory
WORKDIR /app

# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
# where available (npm@5+)
#RUN groupadd node && useradd node && chown -R node:node /app
COPY package*.json ./
#USER node
RUN npm install
# If you are building your code for production
# RUN npm ci --omit=dev

# Bundle app source
#COPY -chown=node:node . .
COPY . .

EXPOSE 8080

CMD [ "node", "app.js" ]

