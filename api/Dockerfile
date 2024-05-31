# Base Image: It starts with a Node.js 17 environment using a lightweight Alpine Linux image.
#FROM node:16-alpine                 


# Working Directory: It sets the working directory in the container to /app.
#WORKDIR /app

# It copies your application code (app.js), the Dockerfile, and the package.json and package-lock.json files into the /app directory in the container.
#COPY . .

# Install Dependencies: It runs npm install to install all the dependencies specified in package.json.
#RUN npm install 

# Expose Port: It indicates(oznacuje) that your application will use port 4000
#EXPOSE 4000

# Run Application: It specifies the command to start your application (node app.js) when the container starts.
#CMD [ "node","app.js" ]

#Building app
# docker build -t <your-image-name> .
# -------------------------------------
    #Caching data for more quicker load data
# Base Image: It starts with a Node.js 17 environment using a lightweight Alpine Linux image.
 FROM node:20-alpine                 

 RUN npm install -g nodemon

 WORKDIR /app

 COPY package.json .

 RUN npm install 

 COPY . .

 EXPOSE 4000

 CMD [ "npm","run","dev" ]

#Building app
# docker build -t <your-image-name> .
