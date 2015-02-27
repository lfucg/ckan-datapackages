### Use dpm to (re)create a CKAN resource and push the data to it

Will recreate the dataset and insert the data defined in code-enforcement/datapackage.json

```
npm install datapackage -g
cd lexington-code-enforcement-complaints
dpm ckan civicdata
```

Same for building permits:

```
cd lexington-building-permits
dpm ckan civicdata
```

### In order to upsert the data rather than first deleting and recreating the resource

I edited the [datapackage-ckan/index.js](https://gist.github.com/eeeschwartz/12f1b32a549b516f6614) dependency of datapackage.
