### Use dpm to (re)create a CKAN resource and push the data to it

Will insert the path defined in code-enforcement/datapackage.json

```
npm install datapackage -g
cd code-enforcement
dpm ckan civicdata
```

### In order to upsert the data rather than first deleting and recreating the resource

I edited the [datapackage-ckan/index.js](https://gist.github.com/eeeschwartz/12f1b32a549b516f6614) dependency of datapackage.
