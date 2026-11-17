# Reviews Assistant

**Reviews Assistant** is a training full-stack app from a webinar on integrating the OpenAI API with .NET. Users submit reviews, and an administrator uses AI to analyze sentiment, priority, category, and urgency, and to generate draft replies.

Stack: ASP.NET Core (.NET 10), Angular, PostgreSQL, Entity Framework Core, JWT, and the OpenAI Responses API.

## Prerequisites

- .NET SDK 10;
- Node.js and npm;
- PostgreSQL;
- OpenAI API key.

## Configuration

Open `api/ReviewsAssistant/ReviewsAssistant.WebAPI/appsettings.json` and replace the placeholders:

- `ConnectionStrings:Reviews` — PostgreSQL connection string;
- `Jwt:SigningKey` — a long random key for signing JWTs;
- `Admin:Email` and `Admin:Password` — administrator credentials;
- `Ai:OpenAi:ApiKey` — your OpenAI API key.

To enable AI analysis, set `Ai:Provider` to `OpenAi`. To run without OpenAI calls, set it to `Stub`.

> Do not publish real keys or passwords. For local development, keep them in `appsettings.Development.json` or User Secrets — `appsettings.Development.json` is ignored by Git.

Example AI section:

```json
"Ai": {
  "Provider": "OpenAi",
  "OpenAi": {
    "Model": "gpt-5-mini",
    "ApiKey": "YOUR_OPENAI_API_KEY"
  }
}
```

## Running the app

1. Create a PostgreSQL database and set the connection string.
2. Start the server in one terminal:

   ```bash
   cd api/ReviewsAssistant/ReviewsAssistant.WebAPI
   dotnet run
   ```

   On startup the app applies migrations automatically. The API is available at `http://localhost:5296`.

3. In another terminal, install dependencies and start the client:

   ```bash
   cd client
   npm install
   npm start
   ```

4. Open the URL printed by the Angular CLI. By default the client calls the API at `http://localhost:5296`.

## Features

- public form for submitting reviews;
- JWT sign-in to the admin panel;
- filtering and sorting reviews;
- AI analysis of sentiment, category, priority, and urgency;
- draft replies to customers.

A full description of the product, architecture, data model, and API is in [docs/project.md](docs/project.md).
