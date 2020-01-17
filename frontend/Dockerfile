 # Use existing docker image (base image) :alpine is baseic version not all node
FROM node:alpine as builder

#Creating folder for application
WORKDIR /app
#Copy package.json file from current directory to container main folder
COPY ./package.json ./
# Download and install a dependency
RUN npm install
# RUN npm i -f
#Copy all files from current directory to container main folder
COPY ./ ./

#Tell the image what to do when it starts as container

# CMD [ "npm", "run", "build" ]
RUN npm run build

# /app/build <----- all I need
# start new process run phase
FROM nginx

# take all was created in builder and paste in nginx specific folder
COPY --from=builder /app/build /usr/share/nginx/html