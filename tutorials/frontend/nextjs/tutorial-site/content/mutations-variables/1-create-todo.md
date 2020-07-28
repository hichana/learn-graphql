---
title: "Create todos - mutation"
metaTitle: "Mutation to create todos | Next.js GraphQL Serverless Tutorial"
metaDescription: "GraphQL Mutation to create new personal todos. Try the mutation in GraphiQL, passing the Authorization token to get authenticated results."
---

In this part of the tutorial, you will learn how to create new todos by using GraphQL Mutations.

Let's define a graphql mutation to perform insert into todos.

```graphql
mutation ($todo: String!, $isPublic: Boolean!) {
  insert_todos(objects: {title: $todo, is_public: $isPublic, user_id: "<auth0-user-id>"}) {
    affected_rows
    returning {
      id
      title
      created_at
      is_completed
    }
  }
}
```


You will also need to pass in the values for the variables, including <auth0-user-id> which can be found in the `users` table of your Hasura instance (https://<your-hasura-app-url>/console/data/schema/public/tables/users/browse)

Try this mutation in GraphiQL against the application database to see what the response looks like.

Let's now integrate this graphql mutation into our app.

