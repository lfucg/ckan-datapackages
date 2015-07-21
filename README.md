### Use [dpm](http://okfnlabs.org/blog/2014/09/11/data-api-for-data-packages-with-dpm-and-ckan.html) to (re)create a CKAN resource and push the data to it

Will create the package - deleting first if it exists - and insert the data defined in lexington-code-enforcement-complaints/datapackage.json

If the lexington-code-enforcement-complaints package exists in CKAN and a resource exists, its data will be completely recreated based on values of `lexington-code-enforcement-complaints.csv` but the resource id stays the same. This is handy so that we don't have to change the CKAN resource ids that our [ETL process](https://github.com/lfucg/lexington-pentaho-etl) upserts to.

**Caveat:** Recreating the datasets will change the \_id column that CKAN assigns. If Citygram has already consumed the event feed then the ['StatusLex' link](https://github.com/citygram/citygram-services/blob/7c34bc265a9e685739f55d32a62751e92f30a053/lib/spy_glass/registry/lexington-code-enforcement-complaints.rb#L19) that use the _id column will point to the wrong listing.

```
npm install datapackage -g
cd lexington-code-enforcement-complaints
dpm ckan civicdata --owner_org=lexington-ky
```

Same for building permits:

```
cd lexington-building-permits
dpm ckan civicdata --owner_org=lexington-ky
```

### In order to upsert the data rather than first deleting and recreating the resource

I edited the [datapackage-ckan/index.js](https://gist.github.com/eeeschwartz/12f1b32a549b516f6614) dependency of datapackage.

(`npm install datapackage -g` on OSX puts the file here: `/usr/local/lib/node_modules/datapackage/node_modules/datapackage-ckan/index.js`)
