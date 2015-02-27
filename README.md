### Use [dpm](http://okfnlabs.org/blog/2014/09/11/data-api-for-data-packages-with-dpm-and-ckan.html) to (re)create a CKAN resource and push the data to it

Will create the package - deleting first if it exists - and insert the data defined in lexington-code-enforcement-complaints/datapackage.json

If the lexington-code-enforcement-complaints package exists in CKAN and a resource exists, its data will be completely recreated based on values of `lexington-code-enforcement-complaints.csv` but the resource id stays the same. This is handy so that we don't have to change the CKAN resource ids that our [ETL process](https://github.com/lfucg/lexington-pentaho-etl) upserts to.

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
