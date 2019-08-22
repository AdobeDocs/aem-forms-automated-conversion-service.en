---
title: [DO NOT PUBLISH] Extend the default meta-model
seo-title: [DO NOT PUBLISH] Extend the default meta-model
description: null
seo-description: null
page-status-flag: never-activated
uuid: a1be9b83-4fc3-4757-9c79-c14b47112a3b
topic-tags: forms
discoiquuid: 9fce5d31-0a3e-4401-b9d7-bb63799121bf
privatebeta: true
---

# [DO NOT PUBLISH] Extend the default meta-model{#do-not-publish-extend-the-default-meta-model}

Automated Forms Conversion service identifies and extracts form objects from source forms. Semantic mapper helps the service to decide how the extracted objects are represented in an adaptive form. For example, a source form can have many different types of representations of a date. The semantic mapper helps map all the representations of date form objects of the source form with date component of the adaptive forms. Symentic-mapper also allows the service to pre-configure and apply validations, rules, data patterns, help text, and accessibility properties to adaptive form components during conversion. 

![](assets/meta-model.gif)

Meta-model is a JSON schema. Before you start with meta-model, ensure that you are well versed with JSON. You should have experience in creating, editing, and reading data saved in JSON format.

## Understanding the meta-model {#understanding-the-meta-model}

A meta-model refers to a JSON schema file that contains entities. Each entity can include multiple properties. The entities and its properties can vary based on the domain. You can augment a schema file with keywords and field configurations to map schema properties to adaptive form components.

The meta-model uses a combination of schema, keywords, and field configurations to map the source form fields with corresponding adaptive form components and apply rules or validations.

**Schema **is all the entities and their corresponding properties. For example, the code below has the ContactPoint field and corresponding properties of the field. You can add custom fields to the meta-model and extend the default meta-model.

**Keywords **are all the different synonyms you can use for a field label. Keywords are referenced with the `aff:keywords`property. For example, the below code uses phone, telephone, mobile phone, work phone, home phone, telephone number, telephone no, and phone number keywords for a phone number. All the source form components with aforementioned keywords are converted to adaptive form telephone component.

**Field Configurations (properties of adaptive form components)** map source form fields to corresponding adaptive form components. For example, the code below ( `sling:resourceType, guideNodeClass`) helps map source form fields with aforementioned keywords to adaptive form telephone component. You can also use field configurations to apply set of rules or validations to mapped adaptive form components. For example, the below code applies a pattern to the telephone field. The rules and validations are applied to adaptive form fields during conversion.

```
"ContactPoint": {
     "id": "ContactPoint",
        "properties": {
           "telephone": {
             "type": "string",
             "pattern": "/\\d{10}/",
             "aem:affKeyword": [
               "phone",
               "telephone",
               "mobile phone",
               "work phone",
               "home phone",
               "telephone number",
               "telephone no",
               "phone number"
             ],
             "description": "Telephone Number",
             "aem:afProperties": {
               "sling:resourceType": "fd/af/components/guidetelephone",
               "guideNodeClass": "guideTelephone"
          }
        }
      }
    }
```

### Common properties of adaptive form components (field configurations) {#common-properties-of-adaptive-form-components-field-configurations}

The following properties are common to adaptive form components. You can add these properties to a meta-model to set value for an adaptive form component:

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody> 
  <tr> 
   <td width="25">Property Name</td> 
   <td>Description</td> 
   <td>Adaptive Form Component</td> 
  </tr> 
  <tr> 
   <td>title</td> 
   <td>The title property serves as label for the adaptive form components.</td> 
   <td>All adaptive form components</td> 
  </tr> 
  <tr> 
   <td>description<br /> </td> 
   <td>The description property sets long description for an adaptive form component.</td> 
   <td>All adaptive form components</td> 
  </tr> 
  <tr> 
   <td>default<br /> </td> 
   <td>The default property serves as initial value of an adaptive form component.</td> 
   <td>All adaptive form components</td> 
  </tr> 
  <tr> 
   <td>maxLength</td> 
   <td>The maxLength property is sets maxlength attribute of the text field component.</td> 
   <td>Text box</td> 
  </tr> 
  <tr> 
   <td>minimum<br /> </td> 
   <td>The minimum, maximum, exclusiveMinimum, and exclusiveMaximum properties are for Numeric box component only.</td> 
   <td><p>Numeric box, Numeric stepper, and Date picker components</p> </td> 
  </tr> 
  <tr> 
   <td>maximum<br /> </td> 
   <td>Specifies the upper bound for numeric values and dates. By default, the maximum value is included.</td> 
   <td>Numeric box, Numeric stepper, and Date picker components</td> 
  </tr> 
  <tr> 
   <td>exclusiveMinimum </td> 
   <td><p>If true, the numeric value or date specified in the component of the form must be greater than the numeric value or date specified for the minimum property.</p> <p>If false, the numeric value or date specified in the component of the form must be greater than or equal to the numeric value or date specified for the minimum property.</p> </td> 
   <td>Numeric box, Numeric stepper, and Date picker components</td> 
  </tr> 
  <tr> 
   <td>exclusiveMaximum</td> 
   <td><p>If true, the numeric value or date specified in the component of the form must be less than the numeric value or date specified for the maximum property.</p> <p>If false, the numeric value or date specified in the component of the form must be less than or equal to the numeric value or date specified for the maximum property.</p> </td> 
   <td>Numeric box, Numeric stepper, and Date picker components</td> 
  </tr> 
  <tr> 
   <td>minDate</td> 
   <td>The minDate property specifies starting date for the date picker component. It is used in conjunction with maxDate property to specify a range of dates for the date picker component.</td> 
   <td>Date picker component</td> 
  </tr> 
  <tr> 
   <td>maxDate</td> 
   <td>The maxDate property specifies last date for the date picker component. It is used in conjunction with minDate property to specify a range of dates for the date picker component.</td> 
   <td>Date picker component</td> 
  </tr> 
  <tr> 
   <td>minItems<br /> </td> 
   <td>The minItems and maxItems properties are used to restrict the number of items/fields that can be added or removed from a panel component. The minitems properties specifies a minimum number of items that panel can include. You can specify -1 for unlimited number of items.</td> 
   <td>Panel component</td> 
  </tr> 
  <tr> 
   <td>maxItems<br /> </td> 
   <td>The minItems and maxItems properties are used to restrict the number of items/fields that can be added or removed from a panel component. The maxitems properties specifies a maximum number of items that panel can include. You can specify -1 for unlimited number of items.</td> 
   <td>Panel component</td> 
  </tr> 
  <tr> 
   <td>readOnly<br /> </td> 
   <td>The readOnly property sets the readonly attribute of an adaptive form component.</td> 
   <td>All components</td> 
  </tr> 
  <tr> 
   <td>pattern<br /> </td> 
   <td>The pattern property sets the validation pattern (regular expression) for an adaptive form component.</td> 
   <td>All adaptive forms components which are mapped to an XSD schema</td> 
  </tr> 
 </tbody> 
</table>

<!--
Comment Type: draft

<h3>Properties specific to an adaptive form component</h3>
-->

## Entities in the default meta-model {#entities-in-the-default-meta-model}

Automated Forms Conversion service has a default meta-model. It is a JSON schema and resides on Adobe Cloud with other components of Automated Forms Conversion service. You can find a copy of the meta-model on your local AEM server at http://&lt;server&gt;:&lt;port&gt;/aem/forms.html/content/dam/formsanddocuments/metamodel/global.schema.json.

The schema of meta-model is derived from schema entities at https://schema.org/docs/schemas.html. It has person, address, FinancialProduct, and more entities as defined on https://schema.org. Every entity of the meta-model adheres to the following structure:

```
   "Entity": {
      "id": "Entity",
      "properties": {
        "name": {
          "type": "string"
        },

        "description": {
          "type": "string",
          "description": "Description of the item"
        }
      }
    }
```

## Modify existing properties {#modify-existing-properties}

You can define or modify properties for any entity in the meta-model. The properties specified in the meta-model are applied to the corresponding adaptive form components during conversion. For example, the date of birth entity in the default meta-model does not contain validations. You can add custom validations on the date of birth entity and these are applied to corresponding component of adaptive form:

**Date of Birth field in default meta model (without validations)**:

```
   "birthDate": {
              "type": "string",
              "format": "date",
              "aem:affKeyword": ["DOB"],
              "description": "Date of birth."
            },
```

**Date of birth field with validations**

```
"birthDate": {
              "type": "string",
              "format": "date",
              "pattern": "date{DD MMMM, YYYY}",
              "aem:affKeyword": [
                "DOB",
                "Date of Birth"
              ],
              "description": "Date of birth in DD MMMM, YYYY",
              "aem:afProperties": {
                "displayPictureClause": "date{DD MMMM, YYYY}",
                "displayPatternType": "date{DD MMMM, YYYY}",
                "validationPatternType": "date{DD MMMM, YYYY}",
                "validatePictureClause": "date{DD MMMM, YYYY}",
                "validatePictureClauseMessage": "Date must be in DD MMMM, YYYY format."
              }
```

For instructions about using a custom meta-model during conversion, see [customize meta-model](#customizemetamodel).

## Add new properties {#add-new-properties}

The default-meta model does not have every possible entity. You can add your own entities to the meta-model, when required. For example, you can add the below code to person entity to add information about the car a person owns:

```
 {
  "carowned" : {
     "aem:affKeyword" : ["car", "four wheeler", ],
     "title" : "Which brand car do you drive?",
     "type" : "number",
     "enum" : [0, 1, 2, 3],
     "enumNames" : ["Audi", "Roll-Royce", "Lincoln", "Jaguar-Land Rover"]
   }
}
```

When the source form is converted to adaptive form. All form fields in source form of type number with caption car or four wheeler is converted to a radio button component of adaptive form. Moreover, the title and item properties of the button component are set as specified in the meta-model entity. For instructions about using a custom meta-model, see [customize meta-model](#customizemetamodel).

## Map a form field to an adaptive form component {#map-a-form-field-to-an-adaptive-form-component}

You can map a form field component to an out-of-the-box adaptive form component or a custom adaptive form component. The following table lists form field configuration properties and corresponding adaptive form components: 

<table border="1" cellpadding="3" cellspacing="0" width="100%"> 
 <tbody> 
  <tr> 
   <th><strong>Meta-model field configurations</strong></th> 
   <th><strong>Adaptive Form component</strong></th> 
  </tr> 
  <tr> 
   <td><p>String properties with enum and enumNames constraint.</p> <p>Syntax,</p> <p> <span class="code">{</span></p> <p><span class="code">"type" : "string",</span></p> <p><span class="code">"enum" : ["M", "F"]</span></p> <p><span class="code">"enumNames" : ["Male", "Female"]</span></p> <p><span class="code">}</span></p> <p> </p> </td> 
   <td><p>Mapped to the drop-down component:</p> 
    <ul> 
     <li>Values listed in enumNames are displayed in the drop box.</li> 
     <li>Values listed in the enum are used for calculation.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>String property with format constraint. For example, email, and date.</p> <p>Syntax,</p> <p><span class="code">{</span></p> <p><span class="code">"type" : "string",</span></p> <p><span class="code">"format" : "email"</span></p> <p><span class="code">}</span></p> <p> </p> </td> 
   <td> 
    <ul> 
     <li>When the type is string and format is email, corresponding form field is mapped to the email component of adaptive form<br /> </li> 
     <li>When the type is string and format is hostname, corresponding form field is mapped to the textbox component</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>{</p> <p>"type" : "string",</p> <p>}</p> </td> 
   <td><br /> <br /> Mapped to the text-field component<br /> <br /> <br /> </td> 
  </tr> 
  <tr> 
   <td>"type": "number"</td> 
   <td>Mapped to the numeric field with sub type set to float<br /> </td> 
  </tr> 
  <tr> 
   <td>"type": "integer",</td> 
   <td>Mapped to the numeric field with sub type set to integer<br /> </td> 
  </tr> 
  <tr> 
   <td>"type": "boolean"</td> 
   <td>Mapped to the switch component<br /> </td> 
  </tr> 
  <tr> 
   <td> "type": "object"</td> 
   <td>Mapped to the panel component<br /> </td> 
  </tr> 
  <tr> 
   <td>"type": "array"</td> 
   <td>Mapped to repeatable panel with min and max equal to minItems and maxItems respectively. Only Homogenous arrays are supported. So the items constraint must be an object and not an array.<br /> </td> 
  </tr> 
 </tbody> 
</table>

You can also map a form field to a custom adaptive form component. You require sling:resourceType and guideNodeClass properties to map a form field to a custom adaptive form component. For example, the below code maps a form field to telephone component of adaptive forms:

```
 "aem:afProperties": {
                "sling:resourceType": "fd/af/components/guidetelephone",
                "guideNodeClass": "guideTelephone"
              }
```

## Add restrictions and limit values for adaptive form components {#add-restrictions-and-limit-values-for-adaptive-form-components}

You can add the below properties to add restrictions to meta-model entities. These properties limit the values acceptable to an adaptive form component:

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody> 
  <tr> 
   <td width="21%"><p><strong> Schema property</strong></p> </td> 
   <td valign="top" width="14%"><p><strong>Data Type</strong></p> </td> 
   <td width="41%"><p><strong>Description</strong></p> </td> 
   <td width="22%"><p><strong>Component</strong></p> </td> 
  </tr> 
  <tr> 
   <td width="21%"><p><span class="code">maximum</span></p> </td> 
   <td valign="top" width="14%"><p>String</p> </td> 
   <td width="41%"><p>Specifies the upper bound for numeric values and dates. By default, the maximum value is included.</p> </td> 
   <td width="22%"> 
    <ul> 
     <li>Numeric box</li> 
     <li>Numeric Stepper<br /> </li> 
     <li>Date Picker</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td width="21%"><p><span class="code">minimum</span></p> </td> 
   <td valign="top" width="14%"><p>String</p> </td> 
   <td width="41%"><p>Specifies the lower bound for numeric values and dates. By default, the minimum value is included.</p> </td> 
   <td width="22%"> 
    <ul> 
     <li>Numeric box</li> 
     <li>Numeric Stepper</li> 
     <li>Date Picker</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td width="21%"><p><span class="code">exclusiveMaximum</span></p> </td> 
   <td valign="top" width="14%"><p>Boolean</p> </td> 
   <td width="41%"><p>If true, the numeric value or date specified in the component of the form must be less than the numeric value or date specified for the maximum property.</p> <p>If false, the numeric value or date specified in the component of the form must be less than or equal to the numeric value or date specified for the maximum property.</p> </td> 
   <td width="22%"> 
    <ul> 
     <li>Numeric box</li> 
     <li>Numeric Stepper</li> 
     <li>Date Picker</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td width="21%"><p><span class="code">exclusiveMinimum</span></p> </td> 
   <td valign="top" width="14%"><p>Boolean</p> </td> 
   <td width="41%"><p>If true, the numeric value or date specified in the component of the form must be greater than the numeric value or date specified for the minimum property.</p> <p>If false, the numeric value or date specified in the component of the form must be greater than or equal to the numeric value or date specified for the minimum property.</p> </td> 
   <td width="22%"> 
    <ul> 
     <li>Numeric box</li> 
     <li>Numeric Stepper</li> 
     <li>Date Picker</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td width="21%"><p><span class="code">minLength</span></p> </td> 
   <td valign="top" width="14%"><p>String</p> </td> 
   <td width="41%"><p>Specifies the minimum number of characters allowed in a component. The minimum length must be equal to or greater than zero.</p> </td> 
   <td width="22%"> 
    <ul> 
     <li>Text box</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><span class="code">maxLength</span></td> 
   <td>String</td> 
   <td>Specifies the maximum number of characters allowed in a component. The maximum length must be equal to or greater than zero.</td> 
   <td> 
    <ul> 
     <li>Text box</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td width="21%"><p><span class="code">pattern</span></p> </td> 
   <td valign="top" width="14%"><p>String</p> </td> 
   <td width="41%"><p>Specifies the sequence of the characters. A component accepts the characters if the characters conform to specified pattern.</p> <p>The pattern property maps to the validation pattern of the corresponding adaptive form component.</p> </td> 
   <td width="22%"> 
    <ul> 
     <li>All adaptive forms components which are mapped to an XSD schema </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>maxItems</td> 
   <td>String</td> 
   <td>Specifies the maximum number of item in an array. The maximum items must be equal to or greater than zero.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>minItems</td> 
   <td>String</td> 
   <td>Specifies the minimum number of item in an array. The minimum items must be equal to or greater than zero.</td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

## Common scenarios to customize a meta-model {#common-scenarios-to-customize-a-meta-model}

The default-metamodel of the Automated Forms Conversion service contains entities for all the common form fields. But your organization can have a set of custom rules and validations. You can extend the default meta-model to create a custom meta-model. The custom meta-model contains entities specific your organization, extended version of some existing entities, and rest of entities of default meta-model. Some common scenarios to customize a metamodel are:

* Add validations to an entity  
* Add search keyword for a form field  
* Add or change description or title of a form field
* Add an event to an entity
* Change type of a field
* Change format of a field
* Import properties of another entity
* Specify pattern for a field

<!--
Comment Type: draft

<p>We have used BSV field, a custom field specific to an organization, and telephone field, a field common across organizations to describe common scenarios. After you add a new entity or extend an existing entity, see <a href="#customizemetamodel">customize meta-model</a> for details instructions to use the custom-meta model during conversion.</p>
-->

<!--
Comment Type: draft

<h3>Add validations to an entity</h3>
-->

<!--
Comment Type: draft

<p>There are multiple methods to add field validation to an adaptive form. You can set a required field, validation patterns, and validation expressions. </p>
-->

#### Required {#required}

To make a component mandatory, you can specify the required property:

```
"employee": {
            "type": "object",
            "properties": {
                "userName": {
                    "type": "string"
                },
                "dateOfBirth": {
                    "type": "string",
                    "format": "date"
                },
                "email": {
                    "type": "string",
                    "format": "email"
                },
                "language": {
                    "type": "string"
                },
            },
            "required": [
                "userName",
                "dateOfBirth",
                "language"
            ]
        }
```

## Customize meta-model {##customizemetamodel}

Your organization can have patterns and validations in addition to the ones listed in the default meta-model. You can extend the default meta-model to add pattern, validations, and entities specific to your organization. Automated Forms Conversion service applies the custom meta-model to the form fields during conversion. You can keep updating the meta-model as new patterns, validations, and entities specific to your organization are discovered. Customizing and using the customized meta-model requires you to:

* Download the meta-model
* Edit the meta-model
* Upload the meta-model
* Run the service with custom meta-model

### Download the meta-model {#download-the-meta-model}

1. Log in to your AEM Forms instance. 
1. Navigate to the ****[!UICONTROL Forms]**** > ****[!UICONTROL Forms & Documents]** **>** **[!UICONTROL Meta Model]**** folder.
1. Select the **[!UICONTROL global.schema.json]** file and tap **[!UICONTROL Download]**. A download dialog box appears. Select the **[!UICONTROL Download asset(s) as binary files]** option. Tap **[!UICONTROL Download]**. An archive is downloaded.

   <!--
   Comment Type: draft

   <li><p>Extract the archive and open the global.schema.json file for editing. </p> </li>
   -->

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

### Edit the meta-model {#edit-the-meta-model}

1. Extract the [downloaded archive](extend-the-default-meta-model.md) and open the global.schema.json file for editing. 
1. Edit the metadata to add pattern, validations, and entities specific to your organization. For example, you can replace the birthDate section in meta-model with the below section to add extra validations and keywords to date of birth:

   ```
   "birthDate": {
                 "type": "string",
                 "format": "date",
                 "pattern": "date{DD MMMM, YYYY}",
                 "aem:affKeyword": [
                   "DOB",
                   "Date of Birth"
                 ],
                 "description": "Date of birth in DD MMMM, YYYY",
                 "aem:afProperties": {
                   "displayPictureClause": "date{DD MMMM, YYYY}",
                   "displayPatternType": "date{DD MMMM, YYYY}",
                   "validationPatternType": "date{DD MMMM, YYYY}",
                   "validatePictureClause": "date{DD MMMM, YYYY}",
                   "validatePictureClauseMessage": "Date must be in DD MMMM, YYYY format."
                 }
   ```

1. Save and close the file.

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

### Upload the custom meta-model {#upload-the-custom-meta-model}

1. Log in to your AEM Forms instance. 
1. Navigate to the **[!UICONTROL Forms]**> **[!UICONTROL Forms & Documents]** folder. Tap **[!UICONTROL Create]**> **[!UICONTROL Folder]**. For example, custom-metadata.
1. Open the newly created folder. Tap **[!UICONTROL Create]**> **[!UICONTROL File Upload]**. Select the custom meta-model file and tap **[!UICONTROL Upload]**.

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

### Run the service with custom meta-model {#run-the-service-with-custom-meta-model}

1. Log in to your AEM Forms instance. Navigate to **[!UICONTROL Tools]**> **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion configuration]**.
1. Select [an already created configuration](configure-the-automated-forms-conversion-service.md#configure-the-cloud-service) and tap **[!UICONTROL Properties]**. 
1. Browse and select the custom global.schema.json file in the **[!UICONTROL Custom Meta-Model]** field. 
1. Tap **[!UICONTROL Start Conversion]**.

