# BASE IMAGE 
FROM node:15

# SETTING WORK DIRECTORY 
WORKDIR /app

# COPY EVERYTHING FROM PAGEKACE JSON 
COPY package.json .

# INSTALL ALL PACKAGES 
RUN npm install

# GRAB EVERY SINGLE FILE AND FOLDER TO CURRENT DIR 
COPY . ./

# USING ENVIRONMENT VARIABLE IN DOCKER CONTAINER - SETTING DEFAULT PORT
ENV PORT 4000
EXPOSE $PORT

# The EXPOSE instruction informs Docker that the container listens on the specified network ports at runtime. 
EXPOSE 3000

# RUNNING THE CONTAINER 
# CMD ["node", "index.js"]
CMD ["npm", "run", "dev"]
