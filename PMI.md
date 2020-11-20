# PMI API Documentation
---
ASHP's PMI API delivers drug information content in htm format using the globally accepted semantic clinical drug form (SCDF) RXNorm concept as indentifiers. 

The API uses Google's [Firebase](https://firebase.google.com/) platform to deliver json data as well as files to you via RESTful http requests. We also leverage Google's Firebase platform to deliver lightning fast speed and flexible SDKs that cater to a variety of programming languages in functional reactive programming patterns.

You can read more about Firebase developer documentations [here](https://firebase.google.com/docs).

## Routes
---
You can build your https request using our Firebase Domain then append it with a route. e.g. https://ahfs-pmi.firebaseio.com/PMI

*Keep in mind that if you are making a REST API call, you need to append .json to the end of the route. You can find some sample API calls at the end of this document.*

* **/PMI** - This route holds all the latest version of SCDF RXNorm mapping to ASHP's PMI data. The index of drugs are keyed by SCDF identifier.

## Objects
---
### PMI
A drug shortage bulletin that holds all relevant information.
  * **UN**: String - This is ASHP's PMI unique identifier. You can use this identifier to fetch the monograph file from Firebase Storage.
  * **description**: String - This is the description of the PMI monograph for the SCDF concept. e.g. For SCDF key: 10760, the description is: "triamcinolone Oral Paste"
  * **title**: String - This is the title of the PMI monograph for the SCDF concept.
  * **updatedAt**: Int This is the server time stamp when this record was last updated/written to Firebase. This integer represents the Linux Epoch time in milliseconds.
  
Sample JSON for PMI/10760:
`{
  "UN" : "601122",
  "description" : [ "triamcinolone Oral Paste" ],
  "title" : "Triamcinolone",
  "updatedAt" : 1604973524220
}`



```
## Sample API calls
---
**To get all active shortages:**

/drugShortages.json?print=pretty&orderBy="/latest/shortageStatus"&equalTo="Active"&auth={apiKey}

**To get shortages since a date (Linux Epoch format in milliseconds):**

/drugShortages.json?auth={apiKey}&print=pretty&orderBy="latest/updatedAt"&startAt=1556668800000

[Full API usage documentation](https://firebase.google.com/docs/reference/rest/database)
