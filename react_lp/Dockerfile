# pull official base image
FROM node:18.2.0-alpine

# set working directory
WORKDIR /app

# add `/app/node_modules/.bin` to $PATH
ENV PATH /app/node_modules/.bin:$PATH

ENV PYTHONUNBUFFERED=1
RUN apk add --update --no-cache python3 && ln -sf python3 /usr/bin/python
RUN python3 -m ensurepip
RUN pip3 install --no-cache --upgrade pip setuptools
RUN apk add --no-cache make
RUN apk add build-base




# install app dependencies
COPY package.json ./
RUN npm install --force

# add app
COPY . ./

EXPOSE 3000

# start app
CMD ["npm", "start"]