# URL shortener project

Test project Task-Frontend-1: 531

This is the frontend part of a URL shortener project designed to convert a long URL into a short URL that looks like 'shrtnr.vercel.app/s/' with an editable slug in the UI. It's a Vue 3 / Nuxt project hosted on Vercel, and it features an adaptive layout for both desktop and mobile devices.
End hosting link: https://shrtnr.vercel.app/

## Usage 

On the homepage, a user can enter a long URL and optionally add a customizable slug. If no custom slug is provided, a random slug is generated instead. A custom slug can consist of 3 to 8 URL-friendly symbols (`A-Za-z0-9_-`). A random slug, which is generated if no custom slug was provided, consists of 8 URL-friendly symbols.

This frontend project does not have a backend yet, so no actual backend request is sent to generate a short URL. Instead, the user is redirected to a results page with a short, frontend-generated URL that doesn't actually redirect to the original long link at this time since there is no backend.

Nevertheless, an asynchronous function that should handle the backend request in the future is provided. However, it is not currently bound to any button on the UI.

As the next step, a fully functional backend can be added to this project.

## Setup

Make sure to install the dependencies:

```bash
# npm
npm install
```

## Development Server

Start the development server on `http://localhost:3000`:

```bash
# npm
npm run dev
```

## Production

Build the application for production:

```bash
# npm
npm run build
```

Locally preview production build:

```bash
# npm
npm run preview
```
