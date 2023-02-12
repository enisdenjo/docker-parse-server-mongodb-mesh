# Recommended setup for https://github.com/Urigo/graphql-mesh/issues/5118

I left a few tips and tricks in comments throught the source code. Consider checking them out!

## Getting started

```sh
docker compose up
```

Wait for the logs to calm down and navigate to [http://localhost:4000/graphql](http://localhost:4000/graphql).

## Note

There is a Parse Server issue running it afresh for the first time, it fails with:

```sh
/parse-server/lib/ParseServer.js:261
          throw err;
          ^

Error: Expected null to be a GraphQL nullable type.
    at devAssert (/parse-server/node_modules/graphql/jsutils/devAssert.js:12:11)
    at new GraphQLNonNull (/parse-server/node_modules/graphql/type/definition.js:395:32)
    at Object.load (/parse-server/lib/GraphQL/loaders/usersQueries.js:97:11)
    at Object.load (/parse-server/lib/GraphQL/loaders/defaultGraphQLQueries.js:24:16)
    at ParseGraphQLSchema.load (/parse-server/lib/GraphQL/ParseGraphQLSchema.js:133:27)
    at process.processTicksAndRejections (node:internal/process/task_queues:95:5)
    at async ParseGraphQLServer._getServer (/parse-server/lib/GraphQL/ParseGraphQLServer.js:80:26)
    at async /parse-server/lib/GraphQL/ParseGraphQLServer.js:109:22

Node.js v18.13.0
exited with code 7
```

However, once the services auto-restart after failure - everything works. I am not very familiar with Parse Server so I will not debug further.
