# prefer debian based images over alpine because with alpine you are effectively choosing an unofficial Node.js runtime
# read more: https://snyk.io/blog/choosing-the-best-node-js-docker-image/
FROM node:19

WORKDIR /mesh

# always have a lockfile (instead of multiple "yarn add"s) when building in a dockerfile,
COPY package.json yarn.lock ./
RUN yarn --frozen-lockfile

# after installing, copy the mesh config to leverage docker layer cache for faster builds
COPY .meshrc.yaml ./

# use the EXEC form when running commands, this way the exit codes and signals are properly propagated
CMD [ "yarn", "mesh", "dev" ]
