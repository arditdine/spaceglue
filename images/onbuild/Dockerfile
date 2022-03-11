FROM abernix/spaceglue:node-8.9.3-builddeps
LABEL Ardit Dine

USER root
WORKDIR /home/node
ONBUILD WORKDIR /home/node
COPY scripts .
RUN chown -R node:node /home/node/

RUN ["npm", "install", "--global", "node-gyp", "node-pre-gyp"]
USER node

ONBUILD USER root
ONBUILD COPY ./ /home/node/app
ONBUILD RUN ["chown", "-R", "node:node", "/home/node/app"]

ONBUILD USER node
ONBUILD RUN lib/build_app.sh
