# PMI API Documentation
---
ASHP's PMI API delivers drug information content in htm format using the globally accepted semantic clinical drug form (SCDF) RXNorm concept as indentifiers. 

The API uses Google's [Firebase](https://firebase.google.com/) platform to deliver json data as well as files to you via Firebase SDKs. We also leverage Google's Firebase platform to deliver lightning fast speed and flexible SDKs that cater to a variety of programming languages in functional reactive programming patterns.

If you do not already have an API key, contact [us](softwaresupport@ashp.org) to get the process started.

You can read more about Firebase developer documentations [here](https://firebase.google.com/docs). 

**We ask that you only fetch data from this API to sync with your local database. Please do not directly integrate in your user facing applications.**

## Routes
---
You can build your https request using our Firebase Domain then append it with a route. e.g. https://ahfs-pmi.firebaseio.com/PMI

*Keep in mind that if you are making a REST API call, you need to append .json to the end of the route. You can find some sample API calls at the end of this document.*

* **/PMI** - This route holds all the latest version of SCDF RXNorm mapping to ASHP's PMI data. The index of drugs is keyed by SCDF identifier.

## Objects
---
### PMI
The PMI object represents a mapping of SCDF to AHFS unique identifiers as well as the title and description of the PMI monograph file.
  * **UN**: String - This is ASHP's PMI unique identifier. You can use this identifier to fetch the monograph file from Firebase Storage.
  * **description**: String - This is the description of the PMI monograph for the SCDF concept. e.g. For SCDF key: 10760, the description is: "triamcinolone Oral Paste"
  * **title**: String - This is the title of the PMI monograph for the SCDF concept.
  * **updatedAt**: Int - This is the server time stamp when this record was last updated/written to Firebase. This integer represents the Linux Epoch time in milliseconds.
  
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
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html>
<head>
<title>Triamcinolone (68:04)</title>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<meta name="Author" content="American Society of Health-System Pharmacists (ASHP)" />
<meta name="Copyright" content="(c) 2020, ASHP" />
<meta name="Keywords" content="68:04, Triamcinolone, Aristocort<sup>®</sup>, Kenacort<sup>®</sup>, " />
</head>
<!-- **********************************************************************
     All material distributed as part of the AHFS Patient Medication
     Information (PMI) database is copyrighted. Reproduction, storage on a 
     retrieval system, or transmission of this material or any part thereof 
     in any form or by any means without the express written permission of the
     American Society of Health-System Pharmacists is prohibited.
     
     Please contact ASHP eHealth Solutions Division at +1 (301) 664-8647
     for more detailed information.
     
     (c) Copyright, 2020, American Society of Health-System 
     Pharmacists, Inc. All Rights Reserved.
     ********************************************************************** -->
<body>
<table><tr><td><p><font size="+3"><b>Triamcinolone</b></font>
<br/>(trye am sin' oh lone)
<br/>
<br/><hr size="4" width="100%" noshade="noshade" /></p></td></tr>
<tr><td><p><b>Brand Name(s):</b> Aristocort<sup>®</sup><sup><a href="#discontinued">¶</a></sup>, Kenacort<sup>®</sup><sup><a href="#discontinued">¶</a></sup>; also available generically</p></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td><a name="why"></a><p><font size="+1"><b>WHY is this medicine prescribed?</b></font></p></td></tr>
<tr><td><dl><dd>
<p>Triamcinolone, a corticosteroid, is similar to a natural hormone produced by your adrenal glands. It often is used to replace this chemical when your body does not make enough of it. It relieves inflammation (swelling, heat, redness, and pain) and is used to treat certain forms of arthritis; skin, blood, kidney, eye, thyroid, and intestinal disorders (e.g., colitis); severe allergies; and asthma. Triamcinolone is also used to treat certain types of cancer.</p>
<p>This medication is sometimes prescribed for other uses; ask your doctor or pharmacist for more information.</p></dd></dl></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td><a name="how"></a><p><font size="+1"><b>HOW should this medicine be used?</b></font></p></td></tr>
<tr><td><dl><dd>
<p>Triamcinolone comes as a tablet and syrup to be taken by mouth. Your doctor will prescribe a dosing schedule that is best for you. Follow the directions on your prescription label carefully, and ask your doctor or pharmacist to explain any part you do not understand.</p>
<p>Do not stop taking triamcinolone without talking to your doctor. Stopping the drug abruptly can cause loss of appetite, upset stomach, vomiting, drowsiness, confusion, headache, fever, joint and muscle pain, peeling skin, and weight loss. If you take large doses for a long time, your doctor probably will decrease your dose gradually to allow your body to adjust before stopping the drug completely. Watch for these side effects if you are gradually decreasing your dose and after you stop taking the tablets or oral liquid, even if you switch to an inhalation. If these problems occur, call your doctor immediately. You may need to increase your dose of tablets or liquid temporarily or start taking them again.</p>
<p>Take triamcinolone exactly as directed. Do not take more or less of it or take it more often than prescribed by your doctor.</p></dd></dl></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td><a name="precautions"></a><p><font size="+1"><b>What SPECIAL PRECAUTIONS should I follow?</b></font></p></td></tr>
<tr><td><dl><dd>
<p>Before taking triamcinolone,</p>
<ul><li><a name="hypersensitivity"></a>tell your doctor and pharmacist if you are allergic to triamcinolone, aspirin, tartrazine (a yellow dye in some processed foods and drugs), or any other drugs.</li></ul>
<ul><li><a name="drug-interact"></a>tell your doctor and pharmacist what prescription and nonprescription medications you are taking, especially anticoagulants ('blood thinners') such as warfarin (Coumadin), arthritis medications, aspirin, cyclosporine (Neoral, Sandimmune), digoxin (Lanoxin), diuretics ('water pills'), estrogen (Premarin), ketoconazole (Nizoral), oral contraceptives, phenobarbital, phenytoin (Dilantin), rifampin (Rifadin), theophylline (Theo-Dur), and vitamins.</li></ul>
<ul><li><a name="precaut-contraindication"></a>if you have a fungal infection (other than on your skin), do not take triamcinolone without talking to your doctor.</li></ul>
<ul><li><a name="precaut-contraindication"></a>tell your doctor if you have or have ever had liver, kidney, intestinal, or heart disease; diabetes; an underactive thyroid gland; high blood pressure; mental illness; myasthenia gravis; osteoporosis; herpes eye infection; seizures; tuberculosis (TB); or ulcers.</li></ul>
<ul><li><a name="preg-fert-lact"></a>tell your doctor if you are pregnant, plan to become pregnant, or are breast-feeding. If you become pregnant while taking triamcinolone, call your doctor.</li></ul>
<ul><li><a name="surgery-precaut"></a>if you are having surgery, including dental surgery, tell the doctor or dentist that you are taking triamcinolone.</li></ul>
<ul><li><a name="alcohol-precaut"></a>if you have a history of ulcers or take large doses of aspirin or other arthritis medication, limit your consumption of alcoholic beverages while taking this drug. Triamcinolone makes your stomach and intestines more susceptible to the irritating effects of alcohol, aspirin, and certain arthritis medications. This effect increases your risk of ulcers.</li></ul></dd></dl></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td><a name="special-dietary"></a><p><font size="+1"><b>What SPECIAL DIETARY instructions should I follow?</b></font></p></td></tr>
<tr><td><dl><dd>
<p>Your doctor may instruct you to follow a low-sodium, low-salt, potassium-rich, or high-protein diet. Follow these directions.</p>
<p>Triamcinolone may cause an upset stomach. Take triamcinolone with food or milk.</p></dd></dl></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td><a name="if-i-forget"></a><p><font size="+1"><b>What should I do IF I FORGET to take a dose?</b></font></p></td></tr>
<tr><td><dl><dd>
<p>When you start to take triamcinolone, ask your doctor what to do if you forget a dose. Write down these instructions so that you can refer to them later.</p>
<p>If you take triamcinolone once a day, take the missed dose as soon as you remember it. However, if it is almost time for the next dose, skip the missed dose and continue your regular dosing schedule. Do not take a double dose to make up for a missed one.</p></dd></dl></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td><a name="side-effects"></a><p><font size="+1"><b>What SIDE EFFECTS can this medicine cause?</b></font></p></td></tr>
<tr><td><dl><dd><a name="com-adv-eff"></a>
<p>Triamcinolone may cause side effects. Tell your doctor if any of these symptoms are severe or do not go away:
</p>
<ul>
<li>upset stomach</li>
<li>stomach irritation</li>
<li>vomiting</li>
<li>headache</li>
<li>dizziness</li>
<li>insomnia</li>
<li>restlessness</li>
<li>depression</li>
<li>anxiety</li>
<li>acne</li>
<li>increased hair growth</li>
<li>easy bruising</li>
<li>irregular or absent menstrual periods</li></ul><p></p><a name="severe-adv-eff"></a>
<p>If you experience any of the following symptoms, call your doctor immediately:
</p>
<ul>
<li>skin rash</li>
<li>swollen face, lower legs, or ankles</li>
<li>vision problems</li>
<li>cold or infection that lasts a long time</li>
<li>muscle weakness</li>
<li>black or tarry stool</li></ul><p></p>
<p>If you experience a serious side effect, you or your doctor may send a report to the Food and Drug Administration's (FDA) MedWatch Adverse Event Reporting program online (<a href="http://www.fda.gov/Safety/MedWatch">http://www.fda.gov/Safety/MedWatch</a>) or by phone (1-800-332-1088).</p></dd></dl></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td><a name="storage-conditions"></a><p><font size="+1"><b>What should I know about STORAGE and DISPOSAL of this medication?</b></font></p></td></tr>
<tr><td><dl><dd>
<p>Keep this medication in the container it came in, tightly closed, and out of reach of children. Store it at room temperature and away from excess heat and moisture (not in the bathroom).</p>
<p>Unneeded medications should be disposed of in special ways to ensure that pets, children, and other people cannot consume them.  However, you should not flush this medication down the toilet. Instead, the best way to dispose of your medication is through a medicine take-back program. Talk to your pharmacist or contact your local garbage/recycling department to learn about take-back programs in your community.  See the FDA's Safe Disposal of Medicines website (<a href="http://goo.gl/c4Rm4p">http://goo.gl/c4Rm4p</a>) for more information if you do not have access to a take-back program.</p>
<p>It is important to keep all medication out of sight and reach of children as many containers (such as weekly pill minders and those for eye drops, creams, patches, and inhalers) are not child-resistant and young children can open them easily. To protect young children from poisoning, always lock safety caps and immediately place the medication in a safe location – one that is up and away and out of their sight and reach. <a href="http://www.upandaway.org">http://www.upandaway.org</a></p></dd></dl></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td><a name="overdose"></a><p><font size="+1"><b>What should I do in case of OVERDOSE?</b></font></p></td></tr>
<tr><td><dl><dd>
<p>In case of overdose, call the poison control helpline at 1-800-222-1222. Information is also available online at <a href="https://www.poisonhelp.org/help">https://www.poisonhelp.org/help</a>. If the victim has collapsed, had a seizure, has trouble breathing, or can't be awakened, immediately call emergency services at 911.</p></dd></dl></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td><a name="other-information"></a><p><font size="+1"><b>What OTHER INFORMATION should I know?</b></font></p></td></tr>
<tr><td><dl><dd>
<p>Keep all appointments with your doctor and the laboratory. Your doctor will order certain lab tests to check your response to triamcinolone. Checkups are especially important for children because triamcinolone can slow bone growth.</p>
<p>Carry an identification card that indicates that you may need to take supplementary doses (write down the full dose you took before gradually decreasing it) of triamcinolone during periods of stress (injuries, infections, and severe asthma attacks). Ask your pharmacist or doctor how to obtain this card. List your name, medical problems, drugs and dosages, and doctor's name and telephone number on the card.</p>
<p>This drug makes you more susceptible to illnesses. If you are exposed to chicken pox, measles, or tuberculosis (TB) while taking triamcinolone, call your doctor. Do not have a vaccination, other immunization, or any skin test while you are taking triamcinolone unless your doctor tells you that you may.</p>
<p>Report any injuries or signs of infection (fever, sore throat, pain during urination, and muscle aches) that occur during treatment.</p>
<p>Your doctor may instruct you to weigh yourself every day. Report any unusual weight gain.</p>
<p>If your sputum (the matter you cough up during an asthma attack) thickens or changes color from clear white to yellow, green, or gray, call your doctor; these changes may be signs of an infection.</p>
<p>If you have diabetes, triamcinolone may increase your blood sugar level. If you monitor your blood sugar (glucose) at home, test your blood or urine more frequently than usual. Call your doctor if your blood sugar is high or if sugar is present in your urine; your dose of diabetes medication and your diet may need to be changed.</p>
<p>Do not let anyone else take your medication. Ask your pharmacist any questions you have about refilling your prescription.</p>
<p>It is important for you to keep a written list of all of the prescription and nonprescription (over-the-counter) medicines you are taking, as well as any products such as vitamins, minerals, or other dietary supplements. You should bring this list with you each time you visit a doctor or if you are admitted to a hospital. It is also important information to carry with you in case of emergencies.</p></dd></dl></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td></td></tr>
<tr><td><a name="discontinued" /><font size="-1"><sup>¶</sup> These branded products are no longer on the market and only generic alternatives are available.</font></td></tr>
<tr><td><hr size="1" width="100%" noshade="noshade" /></td></tr>
<tr><td><p><font size="-1">This report on medications is for your information only, and is not considered individual patient advice. Because of the changing nature of drug information, please consult your physician or pharmacist about specific clinical use.</font></p>
<p><font size="-1">The American Society of Health-System Pharmacists, Inc. represents that the information provided hereunder was formulated with a reasonable standard of care, and in conformity with professional standards in the field. The American Society of Health-System Pharmacists, Inc. makes no representations or warranties, express or implied, including, but not limited to, any implied warranty of merchantability and/or fitness for a particular purpose, with respect to such information and specifically disclaims all such warranties. Users are advised that decisions regarding drug therapy are complex medical decisions requiring the independent, informed decision of an appropriate health care professional, and the information is provided for informational purposes only. The entire monograph for a drug should be reviewed for a thorough understanding of the drug's actions, uses and side effects. The American Society of Health-System Pharmacists, Inc. does not endorse or recommend the use of any drug. The information is not a substitute for medical care.</font></p></td></tr>
<tr><td><p><font size="-1">
AHFS<sup>&reg;</sup> Patient Medication Information&trade;. &#169; Copyright, 2020. Selected Revisions November 15, 2015, <a href="http://www.ashp.org">American Society of Health-System Pharmacists<sup>&reg;</sup></a> 4500 East-West Highway, Suite 900, Bethesda, Maryland 20814 USA. All Rights Reserved. Duplication for commercial use must be authorized by ASHP.</font></p></td></tr>
</table>
</body>
</html>
```

