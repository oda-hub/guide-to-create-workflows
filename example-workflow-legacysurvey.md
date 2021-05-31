# Example of LegacySurvery workflow

Example:

```python
import astroquery.legacysurvey

# This is the sort of query will will introspect with SmartSky:
astroquery.legacysurvey.LegacySurvey.query_object("Mrk421")
```

We will determine that:

```turtle
oda:this-particular-workflow oda:isRequesing odaAstroquery:legacysurvey;
                             oda:isRequesingParameter oda:astroObject;
                             oda:isRequesingAstroObject odaAstroObjects:Mrk421 .
```

in addition, we will know that:

```turtle
odaAstroObjects:Mrk421 rdfs:label "Mrk421";
                       a odaAstroObjects:AGN .
```

this will, in the future, allow us to infer that

```turtle
oda:this-particular-workflow oda:isRelevantIn odaDomains:TimeDomainAstronomy .
```



