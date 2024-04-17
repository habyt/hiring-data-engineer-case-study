# Data Modeling Case Study

## Overview
For this exercise, we will focus on understanding and modeling sellable 
objects (apartment units) and a simplifed customer relationship.

A source of complexity is the different types of units that we rent and the 
relationships between those sellable units, members, and the contracts that
link units to members.

For this exercise, we will focus just on the sellable units. There are two parts
to this exericse.

1. You will create a write-up that includes ER Diagrams or Relational Schema 
   expressing how you would model the relationships and your rationale for why 
   you've made your choices. Your write-up should be in narrative format (not bullet points).
2. Write a simple Dockerized python script to pull data from one of our public
   APIs and format the data according to your proposed schema. Then, persist
   the formatted data. To be clear, we should be able to run download the repo, build the docker image, and run it

## Description
We rent units of two majors types: Co-living, Traditional

A Co-living Unit is a Rooom within an Apartment that is rented.
A Traditional Unit is an entire Apartment that is rented.

Both types of rentable Units have at least 1 Applicant. 
Both types of rentable Units may have additional Co-Applicants.

An Apartment may be:
- entirely Co-living
- entirely Traditional
- mix of Co-living and Traditional

Unit (Rent) Prices are for individual Units and given durations (e.g., $1,307 for 18 Months).
A Price may have zero or more Concessions (i.e., money off).

Units have zero or more Fees (e.g., Screen Fee).

## API
The NAMER (North America) API for listings returns the current available 
units. 

```
GET https://www.common.com/cmn-api/listings/common
```

Swagger Docs: https://www.common.com/cmn-api/docs#/integration/ListingsController_findAllCommonListings


Notes:
- id defines the unique sellable unit (either a Room for co-living or the Apartment for traditional)
- occupancyType defines if the unit is coliving (SHARED) or traditional (PRIVATE)
- propertyId is the Property ID
- address.roomNumber defines the Room number within an apartment (or the entire Apartment number if
  the apartment is traditional)
- ignore the Amenities arrays



## Schema Write-up

Create a write-up detailing your proposed (normalized) schema for the above relationships.
Please attach visuals in the form of either an ER diagram or a relational schema.
Your write-up should be in narrative format (not bullet points).

You do not need to assume that you are working in any particular database system.

We are looking for:
- clarity of thought and arguments
- scalability of the proposed model (e.g., what if we start renting to businesses? would that change anything?)


## Code Exercise

Use the above API to:
- pull data
- transform the data into object models that represent your proposed schema
- serialize the models and persist them as files (e.g., csv, json)
- code should run inside a Docker container (to be clear, we should be able to run download the repo, build the docker image, and run it)

We are looking for:
- clarity of code and rationale for choices
- coding practices
  - you are free to use any style (OOP, functional, procedural)
  - but please do comment your code and give rationale for your choices and
    thought processes


## Submission

Create a public Github repo and submit the repo's URL.
