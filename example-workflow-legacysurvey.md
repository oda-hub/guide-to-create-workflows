# Example of LegacySurvery workflow

For example, let's assume we use this code somewhere in the workflow:

```python
import astroquery.legacysurvey

# This is the sort of query will will introspect with SmartSky:
astroquery.legacysurvey.LegacySurvey.query_object("Mrk421")
```

(Note that `query_object` method is implemeted by most of the popupar astroquery modules; others have also `query_region`, etc.)

When workflow is executed, renku SmartSky plugin will determine that:

```turtle
oda:this-particular-workflow oda:isRequesting odaAstroquery:legacysurvey;
                             oda:isRequestingParameter oda:astroObject;
                             oda:isRequestingAstroObject oda:Mrk421 .
```

This is miminal metadata which has to be collected. No complex reasoning is done, KG is not read. This information is ingested in the KG after the workflow is executed.

At a later stage, we will process thesed data, enriching them with extra information from simbad Simbad that:

```turtle
odaAstroObjects:Mrk421 rdfs:label "Mrk421";
                       a odaAstroObjects:AGN .
                       
odaAstroObjects:AGN  oda:isRelevantIn odaDomains:TimeDomainAstronomy .                        
```

this will allow us to infer that

```turtle
oda:this-particular-workflow oda:isRequesting odaAstroObjects:AGN;
                             oda:isRelevantIn odaDomains:TimeDomainAstronomy .
```


Note: We will provide OWL2 document to specify the necessary elements.
