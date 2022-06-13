## How to set up project on a local environment
This is just the frontend (client) of the whole app. The backend (API) that this client consumes is in this repo: [https://github.com/veekthoven/mailerlite-test](https://github.com/veekthoven/mailerlite-test).

Follow this step to serve this app.

- Run `npm install` to install dependencies
- Run `cp .env.example .env`
- Open `.env` file and set the URL of the API. This should be `http://localhost:82/api` if it wasn't changed.
- Run `npm run dev` to serve the app.
- Visit [http://localhost:3000](http://localhost:3000) to view the app.

## NOTE
The API that this client consumes is in a seperate repo, you can access it here: [https://github.com/veekthoven/mailerlite-test](https://github.com/veekthoven/mailerlite-test)
