# Change Log
## 2025-03-04
### Added: Many Optimade data sources into the "OPTIMADE Data Providers" resource theme

## 2025-04-07
### Changed @id forms reflect the kind of resource that they represent e.g "@id": "psdiDcat:resource-theme/7bcc430a-fdc9-413e-bf32-bf163236430b"; "@id": "psdiDcat:data/e0e14403-1575-43db-a677-89aa515968e4"; "@id": "psdiDcat:service/6bc7c64d-ee3d-430b-be09-f26040886c3c"; "@id": "psdiDcat:tool/5b584eb3-3b07-48c5-bb89-3e5382eeea2d"; "@id": "psdiDcat:guidance/8070e4aa-9dd5-4f39-9e3b-e121317ef361"
### describe access policies with "dcterms:accessRights" linking to a http://purl.org/coar/access_rights/ vocabulary value (instead of ODRL description) for now
### everything is now in top-level @graph

## 2025-04-09
### changed structure of metadata files so that they're not all in folders, but in top-level now (gives cleaner namespace structure) e.g. psdi-dcat.jsonld is not in the resource-catalogue folder anymore
