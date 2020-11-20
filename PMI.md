# PMI API Documentation
---
ASHP's PMI API delivers drug information content in htm format using the globally accepted semantic clinical drug form (SCDF) RXNorm concept as indentifiers. 

The API uses Google's [Firebase](https://firebase.google.com/) platform to deliver json data as well as files to you via RESTful http requests. We also leverage Google's Firebase platform to deliver lightning fast speed and flexible SDKs that cater to a variety of programming languages in functional reactive programming patterns.

You can read more about Firebase developer documentations [here](https://firebase.google.com/docs).

Please contact us for API keys to access this data.

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
  
Sample response JSON for **PMI/10760**  
You can obtain the above data via https://ahfs-pmi.firebaseio.com/PMI/10760.json?auth={apiKey}&print=pretty
```
{
  "UN" : "601122",
  "description" : [ "triamcinolone Oral Paste" ],
  "title" : "Triamcinolone",
  "updatedAt" : 1604973524220
}
```

## Monograph Files
---
The PMI monograph files are in .htm format. They are located in Cloud Firebase's Storage platform. Fore security reasons Firebase Storage is not accessible via REST. You can read about Firebase Cloud Storage documentation [here](https://firebase.google.com/docs/storage).

### Firebase Cloud Storage Buckets
* gs://ashp-pmi This is the bucket where all the monographs are stored. For example, if you have SCDF identifier: 601122, you can use the database API to find the ASHP UN identifer "601122" To get to the monograph file, you need to prepend the UN with the character 'a' to the bucket URL: `gs://ashp-pmi/a601122.htm`

You can use any of the Firebase SDKs to access the file. You can checkout a sample version of the monograph [here](https://github.com/ASHP-Software/Documentations/blob/main/a60122.htm).
