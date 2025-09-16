# Speech-to-FHIR Demo

This repository contains a simple demo application that showcases how to convert speech input into FHIR resources using the Squire SDK.

## Getting Started

### 1. Clone the repository and install dependencies

```sh
git clone https://github.com/squirehealth/speech-to-fhir-demo.git
cd speech-to-fhir-demo

echo "@squirehealth:registry=https://pkg.squire.eu/npm/
//pkg.squire.eu/npm/:_authToken=<YOUR_PACKAGE_REPOSITORY_TOKEN>" > .npmrc
npm install
npm run dev

# Now open your browser and navigate to:
# http://127.0.0.1:8080/
```

To run this, make sure you have installed [Node.js](https://nodejs.org/).

To get a `YOUR_PACKAGE_REPOSITORY_TOKEN`, please contact [Squire](https://squire.eu/).

### 2. Requesting an API key

1. Log in to the [Squire Portal](https://acc.squire.eu/) (create an account if you don't have one yet).
2. Navigate to the "API Keys" section in your account settings.
3. Click on "Create New API Key" and follow the prompts to generate your key.

> [!IMPORTANT]
> Your API key is a secret, and should not be exposed in client-side code.

### 3. Requesting an access token

An access token is required to authenticate your requests to the Squire API. You can obtain an access token by making a POST request to the token endpoint with your API key and user details.

```sh
curl -X POST "https://api-acc.squire.eu/api/v1/token/" \
  -H "X-Api-Key: <YOUR_API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{"user_id": "example1234", "first_name": "doctor", "last_name": "123", "organisation": "practice_name"}'
```

Once you have the access token, add it to `index.html` to authenticate your requests via the Squire SDK.

> [!NOTE]
> In a real life application, you would request the access token per end user on your backend server. For simplicity reasons, we are hardcoding it in this demo.

## Custom FHIRQuestionnaires

Any custom FHIRQuestionnaire can be used. To do so, first add them to Squire via the API. This will generate a `templateId` that you can use to reference the questionnaire in the SDK.

To render them locally in this demo, add them to the `assets` folder and request them in the `index.html` file.

## About

This demo application is a minimal example to illustrate how the Squire SDK can be integrated into any web application. The SDK offers support for all frontend setups (React, Angular, Vue, plain JavaScript, etc.) as well as backend environments (Java, .NET, Python, etc.). No bundler is used here for simplicity purposes, but it works with any of your liking (Vite, Webpack, ...). TypeScript support is also included out of the box.

For more information, visit [the Squire website](https://squire.eu/).

![Squire Logo](./assets/logo.svg)