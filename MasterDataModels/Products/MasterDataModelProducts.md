# Master Data Model Products

## Table of contents
<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->
  - [Master Data Model Products](#master-data-model-products)
    - [Table of contents](#table-of-contents)
    - [1. Introduction](#1-introduction)
      - [1.1 Purpose of this document](#11-purpose-of-this-document)
      - [1.2 Particularities of different product environments](#12-particularities-of-different-product-environments)
        - [1.2.1 Construction materials](#121-construction-materials)
        - [1.2.2 Textiles](#122-textiles)
        - [1.2.3 Food](#123-food)
        - [1.2.4 Hazardous Substances](#124-hazardous-substances)
        - [1.2.5 Services](#125-services)
    - [2. Requirements for a Master Data Model](#2-requirements-for-a-master-data-model)
      - [2.1 General Requirements](#21-general-requirements)
      - [2.2 User Requirements](#22-user-requirements)
        - [2.2.1 Topic 'Types of Objects'](#221-topic-'types-of-objects')
          - [User stories properties of products](#user-stories-properties-of-products)
          - [Use case properties of products](#use-case-properties-of-products)
          - [Use case properties for dangerous materials](#use-case-properties-for-dangerous-materials)
          - [Use case properties for units](#use-case-properties-for-units)
          - [Use case properties for variants](#use-case-properties-for-variants)
        - [2.2.2 Topic 'Types of Relations'](#222-topic-'types-of-relations')
          - [Use case relations product to customer](#use-case-relations-product-to-customer)
          - [Use case relations product to supplier](#use-case-relations-product-to-supplier)
          - [Use case relations product to product](#use-case-relations-product-to-product)
          - [Use case define bill of materials out of the availiable products and services for production](#use-case-define-bill-of-materials-out-of-the-availiable-products-and-services-for-production)
          - [Use case define bill of materials out of the availiable products and services for trading](#use-case-define-bill-of-materials-out-of-the-availiable-products-and-services-for-trading)
    - [3. Findings](#3-findings)
      - [Common Fields](#common-fields)
      - [Rights Management](#rights-management)
        - [User stories Rights management](#user-stories-rights-management)
        - [Use case Rights management](#use-case-rights-management)
      - [Data integrity](#data-integrity)
        - [User stories Data integrity](#user-stories-data-integrity)
        - [Use case Data integrity](#use-case-data-integrity)
      - [Data quality](#data-quality)
        - [User stories Data quality](#user-stories-data-quality)
        - [Use case Data quality](#use-case-data-quality)
      - [Legal requirements](#legal-requirements)
        - ['Data protection'](#'data-protection')
          - [User stories Data protection](#user-stories-data-protection)
          - [Use case Data protection](#use-case-data-protection)
      - ['Data sovereignty'](#'data-sovereignty')
        - [User stories Data sovereignty](#user-stories-data-sovereignty)
        - [Use case Data sovereignty](#use-case-data-sovereignty)
      - [Standardization](#standardization)
        - [User stories standardization](#user-stories-standardization)
        - [Use case Standardization data formats](#use-case-standardization-data-formats)
    - [4. Results](#4-results)
      - [4.1 UML Diagram of the OIH Master Data Model for Addresses](#41-uml-diagram-of-the-oih-master-data-model-for-addresses)
      - [4.2 JSON Schema of the OIH Master Data Model for Addresses](#42-json-schema-of-the-oih-master-data-model-for-addresses)<!-- /TOC -->

## 1. Introduction
### 1.1 Purpose of this document
This document describes the evaluation of the master data model for product data. The aim is to establish a comprehensive data model that can meet the requirements of small and medium sized businesses in a variety of lines of sectors. The concept must consider that all data will be accessed simultaneously by multiple applications. The model must be applicable both in simplified, reduced settings but also in unique, one of a kind, product cases. The use of a centralized data Storage is optional.

Work package title:
Requirement Analysis, Concepts & Standardization
Conception of a Master Data Model for Product data
Responsible partner:
CES
...

Description of AP 2.6, TVB

### 1.2 Particularities of different product environments
Following are a few examples of product environments which will show the particularities and challenges that must be considered, when storing and managing data in different branches of business. The concept needs to reflect this as a requirement so it can be utilized cross-sectoral.    

#### 1.2.1 Construction materials
Work with construction materials requires that products can be managed in different units, and ideally, converted within.  
For example it is common to order wooden planks in standardized dimensions, but be invoiced in cubic meters. In that case, the product references a certain wood type (possibly of a certain quality), which is warehoused as planks, at the same time, though, the stock will be accounted for in cubic meters.   
Similar conversions are common with sheet metals or cast products. These items are usually sold according to their weight, but will be stocked by length, piece or their square measurement. Especially with manufacturing companies it is not uncommon to sell yard good products that can be cut and converted to piece goods, to then also manage the related stock in both units.  
In addition to the handling of units and storage there also other costs to keep in mind, for example the scrapping costs or the copper surchage. Both play an important role in metal processing. All of these costs must be considered in the process of price determination.

#### 1.2.2 Textiles
Textile products usually are stock managed in variants. This way a t-shirt can be maintained as one article in the system, but it is available in different sizes, materials and colors. Although not every combination needs to be possible. In addition, product characteristics might be different for each variant. Specifications (and dimensions) can  be different per article, but they might also be applied to a whole product group.
The system must be able to answer complicated queries teh following: 'what are the sizes we have available for a particular typ of footwear in the color red?' and 'which of these sizes are the men's and which are the lady's version?'. These kinds of queries are only possible if the different variants of an article can be grouped in any which way.

#### 1.2.3 Food
In regard to food items, packaging units and expiry dates play an important role. For example, what kinds of bundles are available? How many pieces will fit in one package? How many packages will fit on a pallet? The "packaged on" and "best before" date must always be available, so the "first in - first out" principle can be considered while picking the goods for delivery.
When determining the prices of types of food that are subject to special taxes, as with the alcohol or sparkling wine tax, these additional costs must be included in the process.

#### 1.2.4 Hazardous Substances
Dangerous goods and hazardous substances have certain requirements for storage and handling. According to standardized regulations (i.e. Risk and Safety Phrases as well as the Hazard and Precautionary Statements) hazardous substances have to be labelled as such. Further the items need to comply to the Globally Harmonized System of Classification, Labelling and Packaging of Chemicals and include the required labels and pictograms on the shipping documentation and mention the related codes (for example "Explosive", "Very Toxic", "Toxic", "Extremely Flammable", "Flammable" "Oxidizing", "Corrosive", "Harmful" or "Dangerous for the environment").

Per product it is required to be able to recall the degree of protection, the fire class and the class of water. Dangerous goods need to have the correct description, the UN-number, LQ, class, tunnel code, category, packing group and emergency information.     

#### 1.2.5 Services
Services can be charged by the hour or as a lump sum.

## 2. Requirements for a Master Data Model

### 2.1 General Requirements

The general requirements are similar to those described in the master data model for addresses, apart from the data protection requirements, which are usually higher when dealing with personal data than with product data.

The master data model for the OIH should be:
- compatible with business models in business-to-business and business-to-consumer
- generic but extendable for individual applications
- used by the integration services and by the data hub
- cover most of the integration scenarios
- de facto standard for the product data exchange scenarios for SME

### 2.2 User Requirements

For the evaluation of the requirements we used topics, use cases and user
stories

- A topic describes the main issue, e.g. data integrity. We use the topics for
clustering the different use cases and user stories by a specific issue.

- The use case describes a specific business scenario, e.g. syncing data
between two applications. It covers the long term description of the context we
would like to implement. Use Cases are permanent artifacts, which will remain as
long as the product will be developed and supported.
For the use cases we use a Cockburn-style template where user goals,
subgoals or intentions are expressed in every step of the basic flow or
the extensions. This practice makes the requirement specification clearer, and
maximizes the flexibility of the design and the implementations.

- The user story describes a specific scenario from a user perspective, it is an
informal description of a feature. They define what has to be built in the
software project later on, so we can fill our backlog.

The common template of a user story should be:
"As a *role*, I want *capability* so that *receive benefit*"

#### 2.2.1 Topic 'Types of Objects'
While talking about products, we are generally referring to goods, which are purchased, produced or sold. Those products can be both, physical objects or immaterial values. Products can relate to one another and have differing characteristics or features, which can be relevant while using them in business processes.

##### User stories properties of products

| User story: | As a user I need information to purchase / order the product.
| :--- | :--- |

| User story: | As a user I need information to offer / sell the product.
| :--- | :--- |

##### Use case properties of products

| Label        | USE CASE - properties of products |
| :---  | :---  |
| **Actor:** | User |
| **Summary:** | Describes adding specific product data to a product |
| **Trigger:** | A user wants to change Product informations |
| **Preconditions:** | The product is already stored |
| **Main Success Scenario:** | Added product data |
| **Failure Scenario:** | Adding product data was not successful |
| **Basic Workflow:** | 1. Chose the product<br/> 2. Add specific product data, e.g. unit, in the appropriate fields<br/> 3. Store the data  |

##### Use case properties for dangerous materials

| Label        | USE CASE - properties of hazmats |
| :---  | :---  |
| **Actor:** | User |
| **Summary:** | Describes adding specifications of hazmat to a product |
| **Trigger:** | A user wants to change/add product informations |
| **Preconditions:** | The product is already stored |
| **Main Success Scenario:** | Added product hazmat specifications |
| **Failure Scenario:** | Adding hazmat data was not successful |
| **Basic Workflow:** | 1. Choose the product<br/> 2. Add specific hazmat data to the product, e.g. EUH-Sentences, in the appropriate specification list<br/> 3. Store the data  |

##### Use case properties for units

| Label        | USE CASE - define units and conversions (from one unit to another) for a product |
| :---  | :---  |
| **Actor:** | User |
| **Summary:** | Describes adding new units to a product for e.g. stock-holding, production, order or selling of the product and define the conversions between the units|
| **Trigger:** | A user wants to change/add product informations |
| **Preconditions:** | The product is already stored |
| **Main Success Scenario:** | Added product units |
| **Failure Scenario:** | Adding a unit was not successful |
| **Basic Workflow:** | 1. Choose the product<br/> 2. Add specific unit and the conversions to the product<br/> 3. Store the data  |

##### Use case properties for variants

| Label        | USE CASE - define variants for a product |
| :---  | :---  |
| **Actor:** | User |
| **Summary:** | Describes adding new variants to a product for e.g. size, colour, shape, material etc. of the product|
| **Trigger:** | A user wants to change/add product informations |
| **Preconditions:** | The product is already stored |
| **Main Success Scenario:** | Added product variants |
| **Failure Scenario:** | Adding a variant was not successful |
| **Basic Workflow:** | 1. Choose the product<br/> 2. Add a variant to the product<br/> 3. Store the data  |

#### 2.2.2 Topic 'Types of Relations'

| User story: | As a user I want to assign one or more products to a customer to store the number and description that the customer uses for the product|
| :--- | :--- |

##### Use case relations product to customer

| Label        | USE CASE - product to customer Relations |
| :---  | :---  |
| **Actor:** | User |
| **Summary:** | Describes the relation between products and customer. |
| **Trigger:** | A user wants to assign product to customer. |
| **Preconditions:** | nd |
| **Main Success Scenario:** | Assignment took place |
| **Failure Scenario:** | Assignment not possible |
| **Basic Workflow:** | 1 Define product<br/> 2 Define customer<br/> 3 Assign product to customer relation |
| **Alternative Workflow:** |    |

| User story: | As a user I want to assign one or more products to a supplier to store the number and description that the supplier uses for the product as well as the delivery-time or the delivery-route|
| :--- | :--- |

##### Use case relations product to supplier

| Label        | USE CASE - product to supplier Relations |
| :---  | :---  |
| **Actor:** | User |
| **Summary:** | Describes the relation between products and supplier. |
| **Trigger:** | A user wants to assign product to supplier. |
| **Preconditions:** | nd |
| **Main Success Scenario:** | Assignment took place |
| **Failure Scenario:** | Assignment not possible |
| **Basic Workflow:** | 1 Define product<br/> 2 Define supplier<br/> 3 Assign product to supplier relation |
| **Alternative Workflow:** |    |

| User story: | As a user I want to assign one or more products to a product as alternatives or replacements|
| :--- | :--- |

##### Use case relations product to product

| Label        | USE CASE - product to product Relations |
| :---  | :---  |
| **Actor:** | User |
| **Summary:** | Describes the relation between products and product. |
| **Trigger:** | A user wants to assign product to product. |
| **Preconditions:** | nd |
| **Main Success Scenario:** | Assignment took place |
| **Failure Scenario:** | Assignment not possible |
| **Basic Workflow:** | 1 Define products<br/> 2 Assign product to product relation |
| **Alternative Workflow:** |    |

| User story: | As a user I want to define bill of materials out of the availiable products and services for production|
| :--- | :--- |

##### Use case define bill of materials out of the availiable products and services for production

| Label        | USE CASE - define bill of materials as product to product list |
| :---  | :---  |
| **Actor:** | User |
| **Summary:** | Describes the relation between one product and its constituents products. |
| **Trigger:** | A user wants to assign products as parts of a (master)product. |
| **Preconditions:** | nd |
| **Main Success Scenario:** | Assignment took place |
| **Failure Scenario:** | Assignment not possible |
| **Basic Workflow:** | 1 Define products<br/> 2 Assign the bill of material relations for the production |
| **Alternative Workflow:** |    |


| User story: | As a user I want to define bill of materials out of the availiable products and services for trading|
| :--- | :--- |

##### Use case define bill of materials out of the availiable products and services for trading

| Label        | USE CASE - define bill of materials as product to product list |
| :---  | :---  |
| **Actor:** | User |
| **Summary:** | Describes the relation between one product and its constituents products. |
| **Trigger:** | A user wants to assign products as parts of a (master)product. |
| **Preconditions:** | nd |
| **Main Success Scenario:** | Assignment took place |
| **Failure Scenario:** | Assignment not possible |
| **Basic Workflow:** | 1 Define products<br/> 2 Assign the bill of material relations for the trading |
| **Alternative Workflow:** |    |

## 3. Findings

### Common Fields
A typical product contains the following fields:
- articleNo
- matchcode
- description
- gtin
- costCalc
- costAvg
- costLast
- costList
- costInventory
- dtCostLast
- isSale
- isPurchase
- isWorkStep
- isProduction
- isStockTracing
- isCheckStock
- isService
- isPacking
- isConsumable
- isDivisible
- isShipping
- isCharges
- isSerialNo
- status
- drawingNo
- version
- dinStandard
- isRohsCompliant
- netWeight
- grossWeight
- density
- length
- width
- strength
- innerDiameter
- outerDiameter
- volume
- isReverseCharge
- isDiscount
- isReduction
- isIntrastat
- isPreferential
- customsTariff
- replacementTime

### Rights Management

#### User stories Rights management

| User story: | As Administrator I have to control which user can read, write, edit or delete products. |
| :--- | :--- |

| User story: | As Administrator I have to control which user can see prices, profits or supplier information on products. |
| :--- | :--- |

| User story: | As Administrator I have to control which external system can access the contacts in my database. |
| :--- | :--- |

| User story: | As Administrator I don't want to grant privileges to the users for every system in use. |
| :--- | :--- |

#### Use case Rights management

| Label        | USE CASE - Rights Management Groups |
| :---  | :---  |
| **Actor:** | Administrator |
| **Summary:** | Grant or withdraw users access rights |
| **Trigger:** | An Administrator wants to control the access rights of the users. |
| **Preconditions:** |  |
| **Main Success Scenario:** | Privileges are altered |
| **Failure Scenario:** | Privileges not altered |
| **Basic Workflow:** | 1. choose a user group<br/> 2. Alter the privileges<br/> 3. Save new privileges |
| **Alternative Workflow:** | 1a. Create new user group.<br/> 2. Define privileges.<br/> 3. Save the new group.<br/> 4. Put desired users in the new group.   |

| Label        | USE CASE - Rights Management for Contacts |
| :---  | :---  |
| **Actor:** | Administrator |
| **Summary:** | Grant or withdraw users access rights for individual contacts |
| **Trigger:** | An Administrator wants to control the access rights of the users. |
| **Preconditions:** | User groups are defined |
| **Main Success Scenario:** | Privileges are altered |
| **Failure Scenario:** | Privileges not altered |
| **Basic Workflow:** | 1. choose the contact data<br/> 2. Alter the user group<br/> 3. Save new privileges |
| **Alternative Workflow:** | 1a. Put or remove a user in a specific user group which can access or should nor more access an entry.<br/> 2. Save definition.   |

### Data integrity

#### User stories Data integrity
| User story: | As a user I want to have my data consistent across multiple systems. |
| :--- | :--- |

#### Use case Data integrity

| Label        | USE CASE Data integrity |
| :---  | :---  |
| **Actor:** | User |
| **Summary:** |  |
| **Trigger:** | User wants consistent data across all used systems. |
| **Preconditions:** |  |
| **Main Success Scenario:** |  |
| **Failure Scenario:** |  |
| **Basic Workflow:** |  |
| **Alternative Workflow:** |    |

### Data quality

#### User stories Data quality

| User story: | As a User I want to enrich entries in my database with additional informations from other sources, so that i have additional informations or further contact possibilities. |
| :--- | :--- |

| User story: | As a User I want to find double entries in my database to eliminate them to have the possibility to clean my database of double entries. |
| :--- | :--- |

| User story: | As a User I want an update of my data automatically synchronized between different systems, because I don't want to do it manually. |
| :--- | :--- |

| User story: | As a User I want to validate the existence of in one system with another system, so that i am sure, that all systems contains the same data. |
| :--- | :--- |

#### Use case Data quality

| Label        | USE CASE - Enrich data |
| :---  | :---  |
| **Actor:** | User |
| **Summary:** | Describes enrichment of the entries in my database with additional informations. |
| **Trigger:** | A user wants to add further information to existing data. |
| **Preconditions:** | Contacts are stored in the database. |
| **Main Success Scenario:** | Additional data is stored in the database  |
| **Failure Scenario:** | Enrichment not possible |
| **Basic Workflow:** | 1. choose contacts for enrichment <br/> 2. choose data with further informations<br/> 3. The system adds the new information to the data |
| **Alternative Workflow:** | 3a. Automatic adding of new information is not possible.<br/>4. User has to define the fields for the new informations.<br/> 5. The system adds the new information to the data.   |

| Label        | USE CASE - Find double entries |
| :---  | :---  |
| **Actor:** | User |
| **Summary:** | Describes inspection of the database for double entries |
| **Trigger:** | A user wants to inspect the database for double entries. |
| **Preconditions:** | Contacts are stored in the database. |
| **Main Success Scenario:** | See if there are double entries.  |
| **Failure Scenario:** | Inspection not possible |
| **Basic Workflow:** | 1. choose contacts for inspection. <br/> 2. See possible double entries. |
| **Alternative Workflow:** | 3. choose the double entries for merging<br/> 4. Merge the desired entries.   |

| Label        | USE CASE - Validate Contact Data across different Systems |
| :---  | :---  |
| **Actor:** | User |
| **Summary:** | Describes inspection of the database for possible double entries. |
| **Trigger:** | A user wants to validate the entries across different systems |
| **Preconditions:** | Running connection between the different systems |
| **Main Success Scenario:** | See if there is a difference between the entries in the databases of the different systems.  |
| **Failure Scenario:** | Inspection not possible |
| **Basic Workflow:** | 1. choose the different systems for validation <br/> 2. Start validation.<br/> 3. See the difference |
| **Alternative Workflow:** | 4. Synchronize the different systems.   |

### Legal requirements

#### 'Data protection'

##### User stories Data protection

| User story: | As a User I have to delete single contact persons from all the systems in which they are stored if a person demands this. (§35 BDSG) |
| :--- | :--- |

| User story: | As a User I have to correct individual fields from contact entries from all the systems in which they are stored of a person demands this. (§35 BDSG) |
| :--- | :--- |

| User story: | As a User I have to block individual contacts for further approaches from all the systems in which they are stored if they demands this. (§35 BDSG) |
| :--- | :--- |

| User story: | As a User I must be able to control the blocking of data for every system. (§35 BDSG) |
| :--- | :--- |

| User story: | As a User I must not delete addresses if legal requirements, statutes or contractual requirements stand in the way of this. In this case they have to be blocked. |
| :--- | :--- |

##### Use case Data protection

| Label        | USE CASE - Delete single contacts from all the systems.  |
| :---  | :---  |
| **Actor:** | User |
| **Summary:** | Describes the removing of contact data from all the systems  |
| **Trigger:** | A User has to remove contacts from the databases |
| **Preconditions:** | Contact Data is stored in the database. |
| **Main Success Scenario:** | Contact data is removed. |
| **Failure Scenario:** | Contact data not removable |
| **Basic Workflow:** | 1. Identify the contact person.<br/> 2. Flag contact person for removal.<br/> 3. Start removing process 4. See a list from all the systems where the contact person has been removed.  |
| **Alternative Workflow:** | 4a. See a list of the cases where it is not possible to remove the contact person from a specific system. 5. Decide further process for this cases (e.g. block).   |

| Label        | USE CASE - Block single contacts from all the systems.  |
| :---  | :---  |
| **Actor:** | User |
| **Summary:** | Describes the blocking of contact data from all the systems  |
| **Trigger:** | A User has to block contacts from the databases |
| **Preconditions:** | Contact Data is stored in the database. |
| **Main Success Scenario:** | Contact data is blocked |
| **Failure Scenario:** | Contact data not blockable |
| **Basic Workflow:** | 1. Identify the contact person.<br/> 2. Flag contact person for blocking.<br/> 3. Start blocking process 4. See a list from all the systems where the contact person has been blocked.  |
| **Alternative Workflow:** | 4a. See a list of the cases where it is not possible to block the contact person from a specific system. 5. Decide further process for this cases (e.g. remove).   |

### 'Data sovereignty'

#### User stories Data sovereignty

| User story: | As a User I want to import contact data from an Excel file into my database |
| :--- | :--- |

| User story: | As a User I want to import contact data from Outlook into my database. |
| :--- | :--- |

#### Use case Data sovereignty

| Label        | USE CASE - Import of products |
| :---  | :---  |
| **Actor:** | User |
| **Summary:** | Import of data.   |
| **Trigger:** | A user wants to import contact data |
| **Preconditions:** | Contact Data stored in a file  |
| **Main Success Scenario:** | Data is imported |
| **Failure Scenario:** | Import not possible |
| **Basic Workflow:** | 1. choose the desired contact data<br/> 2. Export or Import the data |
| **Alternative Workflow:** | 2a. Data for the import is an unsupported format. 3. Convert the data in a supported format. 4. Import the data.    |

| Label        | USE CASE - Export of products |
| :---  | :---  |
| **Actor:** | User |
| **Summary:** | Export of data.   |
| **Trigger:** | A user wants to export contact data |
| **Preconditions:** | Contact Data stored in the contact database |
| **Main Success Scenario:** | Data is exported |
| **Failure Scenario:** | Export not possible |
| **Basic Workflow:** | 1. choose the desired contact data<br/> 	2. choose the desired format for the export 3. Export the data |
| **Alternative Workflow:** | 3a. Export is not possible 3. Copy & Paste ever entry in the database by manually.    |

| User story: | As a User I want to transfer my contact data in the event of a new order from our ERP-Software to our CRM-Software. |
| :--- | :--- |

| User story: | As a User I want to transfer the product numbers and descriptions to a catalog system for my marketing campaigns. |
| :--- | :--- |

| Label        | USE CASE - Migration of products |
| :---  | :---  |
| **Actor:** | User |
| **Summary:** | Convert data into specific format.   |
| **Trigger:** | A user wants to import or export contact data from or to a specific data format. |
| **Preconditions:** | Contact Data stored in a contact database |
| **Main Success Scenario:** | Data is imported or exported |
| **Failure Scenario:** | Export or import not possible |
| **Basic Workflow:** | 1. choose the desired contact data<br/> 2. choose the desired data format 3. Export or Import the data |
| **Alternative Workflow:** | 2a. Desired format is not supported 3a. Export data in an alternative supported format.     |

| Label        | USE CASE - Automatic transfer of products |
| :---  | :---  |
| **Actor:** | User |
| **Summary:** | Automatic transfer of products from one system to another.   |
| **Trigger:** | A user wants to have product data automatically transfered from one system to another. |
| **Preconditions:** | Contact Data stored in a product database |
| **Main Success Scenario:** | Data is transferred |
| **Failure Scenario:** | Transfer not possible |
| **Basic Workflow:** | 1. choose the source system of the product data<br/> 2. choose the desired target system<br/> 3. Data is transfered to the target system  |
| **Alternative Workflow:** | 2a. Target System not reachable 3a. Throw failure message.     |

### Standardization

#### User stories standardization

| User story: | As a User I want the product numbers in a standardized format, so that my edi system can recognize the products. |
| :--- | :--- |

| User story: | As a User I want the stored statistical data (e.g. product size, revenue etc.) in a standardized format, so that I can use them for the marketing. |
| :--- | :--- |

#### Use case Standardization data formats

| Label        | USE CASE - Standardization of data |
| :---  | :---  |
| **Actor:** | User |
| **Summary:** | Describes standardization of data |
| **Trigger:** | A user wants to add standardize existing data in a specific format. |
| **Preconditions:** | Contacts are stored in the database. |
| **Main Success Scenario:** | Data is standardized  |
| **Failure Scenario:** | Standardization not possible |
| **Basic Workflow:** | 1. choose fields for standardization <br/> 2. choose format for standardization<br/> 3. The system standardize the informations. |
| **Alternative Workflow:** | 2a. The desired field is not suitable for standardization<br/> 2b. The format is not suitable for this field <br/> 2c. There is no standard format for this field.   |

## 4. Results

### 4.1 UML Diagram of the OIH Master Data Model for Addresses

![UML Draft OIH Master Data Model Products](Assets/OIHDataModelProducts.svg)

### 4.2 JSON Schema of the OIH Master Data Model for Addresses

The OIH specifies JSON as the format that data is processed with.
Accordingly, JSON Schema is the given format to describe MDMs.

From the UML we derive the JSON-Schema.

[/src/main/schema/products/product.json](../../src/main/schema/products/product.json)
