Lab 2: API Flexibility Analysis
1. The Over-fetching Problem

One thing I noticed when comparing REST and GraphQL is that REST endpoints generally decide what data comes back before the frontend makes the request. Over-fetching happens when an endpoint returns more information than the frontend actually needs. For example, a React page might only need a user's name and profile picture, but a REST endpoint could return the user's entire profile, preferences, and other information. Under-fetching is the opposite problem: one endpoint does not provide enough information, so the frontend has to make additional requests to get everything it needs.

GraphQL approaches this differently because the client describes the data it wants in its query. Instead of accepting whatever fields a REST endpoint happens to return, the frontend can request specific fields from related data. This can reduce unnecessary data transfer and, in some situations, reduce the number of requests needed to build a page.

2. Endpoint and Schema Philosophy

A traditional REST API usually organizes its backend around multiple resources and endpoints. For example, an application could have separate routes such as /users, /projects, and /tasks. Different HTTP methods can then be used to create, retrieve, update, or delete those resources.

GraphQL usually works through a single endpoint, with the schema describing the available data and operations. The strongly typed schema is especially useful on the frontend because developers can know what fields and data types are available before making a request. This can make working with a large API more predictable and can also help development tools identify incorrect queries or fields.

To me, this is one of the biggest differences in the developer experience: REST gives the frontend a set of predefined routes, while GraphQL gives the frontend more control over constructing the data it needs.

3. Caching and Complexity

Caching is generally more straightforward with REST because individual resources have recognizable URLs. A response from something like /api/tasks/123 can be cached based on that URL, while standard HTTP caching mechanisms can work naturally with REST requests.

GraphQL makes caching more complicated because many different queries can be sent to the same endpoint. Two queries could request different combinations of fields while using the same GraphQL URL. This means applications often need additional caching strategies or client-side tools to determine when two responses can be reused.

However, that flexibility could be worthwhile for an application with a complicated interface that displays related information from many resources at once. For example, a dashboard might need selected fields from a user's profile, projects, tasks, and activity. Instead of making several REST requests and potentially receiving unnecessary fields, GraphQL could allow the frontend to request the exact combination of data required for that dashboard.

Overall, I see REST as a straightforward choice for predictable resource-based APIs, while GraphQL becomes more attractive when the frontend has complex or frequently changing data requirements.