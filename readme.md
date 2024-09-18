- export heroku app name
```bash
export APPNAME=<YOUR_HEROKU_APP_NAME>
```

- go to project directory
```bash
cd <HEROKU_PROJECT_ROOT_FOLDER>
```

- Enable Heroku Labs Dyno Metadata to set HEROKU_APP_NAME env variable automatically
```bash
heroku labs:enable runtime-dyno-metadata -a $APPNAME
```

- Pass your required environment variables
```bash
heroku config:add MW_API_URL_FOR_CONFIG_CHECK="https://rhqbf.mw.lc"
```
```bash
heroku config:add MW_API_KEY=kxtgxquehpxpwvrctbvmllaqwovspakftggg
```
```bash
heroku config:add MW_TARGET=https://rhqbf.mw.lc:443
```

- Add this buildpack and set your Datadog API key
```bash
heroku buildpacks:add --index 1 https://github.com/kartikMiddleware/buildpack.git
```

- Deploy to Heroku forcing a rebuild
```bash
git commit --allow-empty -m "Rebuild slug"
```
```bash
git push heroku main
```
