# SPA Configuration - React SSI

Example of using server-side includes to inject runtime configuration to a React single-page app.

## Notes

 - Bootstrapped using [Create React App]
 - **Requires** `html-minifier-terser` of at least 5.1.0 (see this [Pull Request]) or explicit
    configuration to leave SSI comments in HTML (can be done via `webpack-html-plugin` but not in
    CRA)
 - Set up for deployment to [Cloud Foundry]

## Usage

This demo includes two sets of configuration:

 - development (in `src/configuration.js`); and
 - production (in `public/config.html`).

The SSI directive in `public/index.html` is replaced by the content of `public/config.html` at
runtime, if SSI is enabled on the server (the included `Staticfile` does this for the Nginx used
in the [Staticfile buildpack]).

To run locally with the development configuration:

```bash
npm start
```

To deploy to CF with the production configuration, using the [CF CLI]:

```bash
npm run build && cf push
```

  [CF CLI]: https://docs.cloudfoundry.org/cf-cli/install-go-cli.html
  [Cloud Foundry]: https://cloudfoundry.org/
  [Create React App]: https://github.com/facebook/create-react-app/
  [Pull Request]: https://github.com/DanielRuf/html-minifier-terser/pull/39
  [Staticfile buildpack]: https://docs.cloudfoundry.org/buildpacks/staticfile/index.html
