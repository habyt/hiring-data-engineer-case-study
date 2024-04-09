# Data Modeling Case Study

## Overview
For this exercise, we will focus on understanding and modeling sellable 
objects (apartment units) and a simplifed customer relationship.

A source of complexity is the different types of units that we rent and the 
relationships between those sellable units, members, and the contracts that
link units to members.

There are two parts to this exericse.

1. You will create a write-up that includes ER Diagrams or Relational Schema 
   expressing how you would model the relationships and your rationale for why 
   you've made your choices.
2. Write a simple Dockerized python script to pull data from one of our public
   APIs and format the data according to your proposed schema. Then, persist
   the formatted data.

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

A Contract represents:
- the actual lease interval (e.g., 2024-01-01 to 2024-06-01)
- Contracts form a linear tree with the root being the first Contract

A Member represents:
- the applicant/resident that rents a Unit and is connected to the unit via a Contract


## API
The NAMER (North America) API for listings returns the current available 
units. 

```
GET https://www.common.com/cmn-api/listings/common
```

Swagger Docs: https://www.common.com/cmn-api/docs#/integration/ListingsController_findAllCommonListings


Notes:
- occupancyType defines if the unit is coliving (SHARED) or traditional (PRIVATE)



## Schema Write-up

Create a write-up detailing your proposed (normalized) schema for the above relationships.
Please attach visuals in the form of either an ER diagram or a relational schema.

You do not need to assume that you are working in any particular database system.

We are looking for:
- clarity of thought and argument
- scalability of the proposed model (e.g., what if we start renting to businesses?)

## Code Exercise

Use the above API to:
- pull data
- transform the data into object models that represent your proposed schema
- serialize the models and persist them as files (e.g., csv, json)

We are looking for:
- clarity of code and rationale for choices
- coding practices
  - you are free to use any style (OOP, functional, procedural)
  - but please do comment your code and give rationale for your choices and
    thought processes


## Submission

Create a public Github repo and submit the repo's URL.