# wiremock-deploy-heroku
Deploy wiremock to heroku.

Assumes you already have a heroku account, already have the heroku cli installed, and are logged into the heroku cli.

## Instructions

- Clone this repo
```
git clone https://github.com/muthu07/wire-mock
cd wire-mock
```

- Create a heroku application
```
heroku create <app-name>
```

- Add the [Energized Work](http://www.energizedwork.com) downloadable jar buildpack. This will pull the wiremock jar defined as the ARTIFACT_URL property in the manifest.sh
```
heroku config:set 'NO_PRE_DEPLOY=true'
heroku buildpacks:set https://github.com/energizedwork/heroku-buildpack-runnable-jar
heroku buildpacks:add -i 1 https://github.com/heroku/heroku-buildpack-jvm-common.git --app wire-mock

```

- Start the application
```
git push heroku master
```


With a json body returned
```
curl http://<app-name>.herokuapp.com/getReportList
```
