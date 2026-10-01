Lab 1: Full-Stack Integration Analysis
1. CORS Explained

CORS, or Cross-Origin Resource Sharing, is a browser security rule that controls whether one website is allowed to request resources from another origin. In a typical MERN application, the React client and Express server may run separately, such as React on localhost:5173 and Express on localhost:3000. Even though both are running on my own computer, the browser sees them as different origins because their ports are different. If the Express server has not been configured to allow requests from the React application's origin, the browser can block the request and produce a CORS error.

One solution during development is to configure the Express server with the cors middleware and specifically allow requests from the React development server. Another option is using a React development proxy. The proxy allows the React application to send requests through its own development server, which then forwards those requests to Express. I think the proxy approach can make local development cleaner because the frontend can make requests using a relative API path instead of dealing with two different origins directly.

2. Environment Management

Hardcoding an API URL directly into React code is a problem because the URL may change between development, testing, and production. For example, I might use a local Express server while building an application but eventually deploy the API to a completely different domain. Having the URL scattered throughout components would mean changing the code every time the environment changes.

Environment variables provide a cleaner way to manage these values. On the React side, a variable such as REACT_APP_API_URL can store the API's base URL, depending on the React build setup being used. On the Express side, the dotenv package loads values from a .env file into process.env, allowing the server to access things such as database connection strings, ports, and JWT secrets without putting them directly into the source code. The .env file should also be kept out of GitHub when it contains sensitive information.

3. Data Fetching Trade-offs

The native fetch API is useful because it is already built into modern browsers and does not require another dependency. However, for a larger application with many API requests, I see an advantage in using Axios because it provides a more convenient interface for handling requests and responses. Axios automatically handles JSON response data and makes it easier to configure things such as a shared base URL, headers, and interceptors.

For a MERN application with authentication, multiple routes, and repeated API requests, that centralized configuration can reduce duplicated code. Instead of setting up the same request behavior in every component, Axios can provide a consistent way for the React client to communicate with the Express API.