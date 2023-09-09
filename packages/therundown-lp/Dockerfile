FROM node:16

# Input arguments (passed by docker build command)
ARG USER_ID=0
ARG GROUP_ID=0
ARG WORKSPACE_DIR=/lw

# Create app directory
WORKDIR ${WORKSPACE_DIR}

# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
# where available (npm@5+)
COPY package*.json ./
COPY yarn.lock ./

RUN yarn install

# Bundle app source
COPY . .

# IMPORTANT: set the build's workspace dir to be owned by the container's user
RUN chown -R ${USER_ID}:${GROUP_ID} ${WORKSPACE_DIR}
RUN chmod 700 ${WORKSPACE_DIR}
USER ${USER_ID}

EXPOSE ${EXPOSE_PORT}
CMD yarn start