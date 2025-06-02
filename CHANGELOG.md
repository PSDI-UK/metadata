# Change Log

## 2025-06-02
* updated psdi-dcat-shacl.ttl and psdi-dcat-shacl.jsonld so that most of the shapes in it are now closed shapes. There have been some minor updates to the iris of @ids in psdi-dcat.jsonld as a result (so that different @types have different iris).

## 2025-05-27
* added psdi-dcat-shacl.ttl and psdi-dcat-shacl.jsonld for validation of psdi-dcat.jsonld
* updated psdi-dcat as a result of this:
  * added more to the context (this is not comprehensive yet, so as not to disrupt dependent code)
  * removed foaf:openid from elements with @type foaf:Agent, foaf:Organization, foaf:Person (@id contained the same value and should be used instead)
  * removed top-level @id from prov:qualifiedAttribution (@id of prov:qualifiedAttribution/prov:agent contained the same value and made more sense)
  * added @type on "prov:qualifiedAttribution"/"prov:agent" elements of "@type":"foaf:Agent"
  * added "vcard:Kind" elements now have attributes "@id" and "vcard:Name"
  * updated vard:hasEmail values so that they start with "mailto:"
  * psdiDcatExt:displayPriority is now potentially a double not integer (the context defines it with "@type": "xsd:double")
  * psdiDcatExt:deliveryFormat, "dcat:compressFormat", "dcat:packageFormat" and "dcat:mediaType" are now no longer literal string, but iri elements with @type dcterms:MediaType (its previous value is captured by the rdfs:label)
  * psdiDcatExt:byteSize is now captured as a literal with @type xsd:nonNegativeInteger (defined in the context)
* added new type of container (SIF format, used by Apptainer) to "Container Image Registry" resource theme(psdiDcat:resource-theme/837eb69a-a3b4-4ed7-a495-d1908dae0e91):
  * these have "psdiDcatExt:deliveryFormat/rdfs:label" values of "application/vnd.oci.image.manifest.v1+json" 
  * new resource tools added are:
    * Metadise Container (Docker format) (psdiDcat:tool/099911e7-a350-44b7-8add-2cba64beb8d8)
    * Metadise Container (SIF format) (psdiDcat:tool/a95c572b-634d-4682-9533-5d4787164997)
    * DL_MONTE Container Image (SIF format) (psdiDcat:tool/1839c691-c787-4d32-9fc3-e9c220902e93)
    * DSync (Data Transfer and Synchronisation) Container (SIF format) (psdiDcat:tool/f85c7c18-28b4-4efb-8edd-33d472683905)
  * renamed existing tool resources within this resource theme to distinguish them from these containers:
    * psdiDcat:tool/94032602-00a9-4640-a730-b6cd7bf3547d renamed from "DL_MONTE Container Image" to "DL_MONTE Container Image (Docker format)"
    * psdiDcat:tool/a363e1c8-e1e0-47a3-a8d7-17f36c731ac2 renamed from "DSync (Data Transfer and Synchronisation) Container" to "DSync (Data Transfer and Synchronisation) Container (Docker format)"

## 2025-04-09
* changed structure of metadata files so that they're not all in folders, but in top-level now (gives cleaner namespace structure) e.g. psdi-dcat.jsonld is not in the resource-catalogue folder anymore

## 2025-04-07
* changed @id forms reflect the kind of resource that they represent e.g "@id": "psdiDcat:resource-theme/7bcc430a-fdc9-413e-bf32-bf163236430b"; "@id": "psdiDcat:data/e0e14403-1575-43db-a677-89aa515968e4"; "@id": "psdiDcat:service/6bc7c64d-ee3d-430b-be09-f26040886c3c"; "@id": "psdiDcat:tool/5b584eb3-3b07-48c5-bb89-3e5382eeea2d"; "@id": "psdiDcat:guidance/8070e4aa-9dd5-4f39-9e3b-e121317ef361"
  * describe access policies with "dcterms:accessRights" linking to a http://purl.org/coar/access_rights/ vocabulary value (instead of ODRL description) for now
  * everything is now in top-level @graph

## 2025-03-04
* added: Many Optimade data sources into the "OPTIMADE Data Providers" resource theme