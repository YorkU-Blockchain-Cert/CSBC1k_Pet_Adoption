# Pet Adoption

# Introduction

---

## Background

According to Humane Canada, 14% of shelter animals are euthanized on an annual basis. The number of euthanized animals could be reduced dramatically if more people adopted pets instead of buying them. The aim of this project is to create an online platform for people to view, discover, and adopt animals at a shelter. This will give the general public a more convenient option to adopt pets.

# Requirements Summary

---

## Use Cases

### UC-1

John manages an animal shelter in Barrie, Ontario. On average, Ben’s shelter receives 2 new cats and 1 new dog per month. While the full history of these pets is not known, they are accompanied with some paper records. Upon receiving these pets and their records John logs into the shelter's portal and creates a profile for each of the new animals. He also associates his shelter with each of the animals.

Alice is interested in adopting a cat. While browsing and reviewing the profiles of the cats at John’s shelter, Alice falls in love with one of the cats. Alice fills out the online adoption form. The application for adoption is reviewed and approved by John. Then he assigns ownership of the cat to Alice. Alice receives an email informing her that a date is set for her to come and take her new pet home. She is also directed to check her new pet’s records on the shelter's portal.

### UC-2

A few months after Alice's adoption, she becomes a little concerned about her cat's health condition, Kitty. So she decides to take Kitty to a nearby pet clinic for an examination. Fortunately, it turns out that Kitty is very healthy.

However, because she does not have any certificates to show that she has been vaccinated, Alice has to get her some vaccines required by law even if she might have received them in the past year. Alice tells the veterinarian that Kitty is adopted from John's shelter and that he can register an account on John's shelter to update Kitty's records.

The veterinarian fills out a registration request and within minutes he is verified and registered on the platform. Upon performing the vaccination, the veterinarian updates Kitty's record to reflect the new vaccination records.

### UC-3

A snow storm damages an animal shelter in Collingwood. Due to this extensive damage, the centre will be closed for more than a year and the animals need to be relocated to another shelter. John receives a request from Collingwood for the transfer. He accepts the transfer request.

Once John receives the animals from the Collingwood centre he changes the ownership of the animals to his centre. The newly arrived animals are automatically added to the platform.

### UC-4

Alice's current lease is about to expire. She finds a new condo that has better amenities and is more affordable than her current condo. However, the new condo has a no pet policy. Luckily, for Alice, her current neighbour, Jane, offers to adopt Kitty. Alice gets her neighbour's information. Then she logs into the platform and changes the ownership to Jane. 

### Selected use cases

We have selected UC-1 and UC-2 to implement in this phase as they cover the essential features of the application. UC-3 and UC-4 are nice to have features that can be implemented at a later stage. In this document we outline all the functional and non-functional requirements based on the first two selected use cases. 

## Stakeholder Analysis

- Adoption center/employees:

    Allow employees of the adoption centre to register pet information that are at the centre. They can perform CRUD operations on the data. They can also assign and update pet owner information. 

- Veterinarians:

    Allows the veterinarian to create and update medical records of the pets. More specifically the vaccination records.  

- Pet owners/prospects:

    Allows the pet owners to view their current pet data and also to adopt new pets

## Requirements

- **Functional**

    **FR-1:** Pet owners/prospects register for an account.

    **FR-2:** Veterinarians can create a business account that need to be approved by the adoption centre. 

    **FR-3:** Each adoption centre can create an account. 

    **FR-4:** Each user need to log into the system with a unique username and password

    **FR-5:** Veterinarians can create and modify medical records for the pets. 

    **FR-6:** Any pet owner can transfer ownership to another prospect/pet owner 

    **FR-7:** Prospects/Pet owners can fill out adoption form for any given pet

    **FR-8:** Adoption centre can approve or deny adoption requests 

    **FR-9:** Prospects/pet owners can search through the pets

- **Non-functional**

    **NFR-1:** Access to data should take a least privilege approach.

    **NFR-2:** Application stack should be cloud compatible.

    **NFR-3:** All web traffic should be encrypted.

    **NFR-4:** Pet vaccination record should be immutable 

    **NFR-5:** Pet ownership information should be immutable 

    **NFR-6:** Application should be available 99.99% of the time

# High-level Design

---

## System Architecture

Based on the requirements of the system, we have identified three core modules and one module that may be completed at a future date. The four core modules are: database, REST API, and a web application. One additional module is the solidity contract that will be used to capture and store immutable data.

Using a multi-tier architecture each of these modules fall within one of three tiers. The data tier is responsible for storage and retrieval of the data. This tier includes the database module. The application tier is responsible for all the business logic, including authorization and access control. This tier is made up entirely of the REST API. The presentation tier provides an external interface for the system. This tier includes a responsive web application.

Each of the applications in the presentation tier communicates with the REST API in the application tier and the REST API communicates with both the database and solidity contract modules in the data tier.

This three tier approach assures that our design is scalable. It also provides necessary code separation so that we can maintain the code efficiently and various components can scale independently.

![pet adoption (2).png](Pet%20Adoption%20fd4193113e5748349fdbf1f865284e55/pet_adoption_(2).png)

## Database

Our database structure is not a complex structure. Therefore, we are confident that standard requirements for hosting a database will be sufficient for normal operations of our application. 

![PHOTO-2021-09-22-22-11-56.jpg](Pet%20Adoption%20fd4193113e5748349fdbf1f865284e55/PHOTO-2021-09-22-22-11-56.jpg)

## Rest API

### API Endpoints

[Untitled](Pet%20Adoption%20fd4193113e5748349fdbf1f865284e55/Untitled%20Database%205eeddd20113c4ffeb59b7319ad12203a.csv)

## Web Application

The front-end of the application will be written in React. The application will be divided into various self-contained modules. Since React uses virtual DOM, it is very efficient when handling and loading user data and various views. The application will be responsive to allow proper display of contents on mobile devices. We may decide to utilize Redux to handle states throughout our application.

To assure our compliance with the non-functional requirements, we will be using Amazon CloudFront for our content delivery network (CDN). This will assure a low latency and high transfer speeds for the application.

We will be using Amazon EC2 as our cloud infrastructure. This allows the application to fulfill the scalability and uptime requirements.

### User Journey

![User_Flow_Pet_Adoption.jpg](Pet%20Adoption%20fd4193113e5748349fdbf1f865284e55/User_Flow_Pet_Adoption.jpg)

# Conclusion

---

Throughout this project we have tried to utilize industry standard approaches to web application development. While, one may consider further improvements to this document, given the time constraint for the project, we have provided enough design considerations to allow a seamless development process for out pet adoption project. Since it is near impossible to anticipate all possible flaws in the design, if any unforeseen issues arise in the development phase the separation of concern considerations above will allow maximum flexibility in applying changes in this phase. We have created a project repository for the development phase which can be accessed by accessing the [Pet Adoption Project](https://github.com/YorkU-Blockchain-Cert/CSBC1k_Pet_Adoption) link. 

## References:

[https://uxplanet.org/petme-ui-ux-case-study-176655fcf864](https://uxplanet.org/petme-ui-ux-case-study-176655fcf864)

[https://blog.prototypr.io/designing-pet-adoption-app-case-study-44d97a656435](https://blog.prototypr.io/designing-pet-adoption-app-case-study-44d97a656435)

[https://www.behance.net/gallery/87781251/Pet-House-Pet-Adoption-Mobile-App-UX-Case-Study](https://www.behance.net/gallery/87781251/Pet-House-Pet-Adoption-Mobile-App-UX-Case-Study)

[https://bootcamp.uxdesign.cc/pet-adoption-case-study-febpets-for-you-ux-ui-928a454e365e](https://bootcamp.uxdesign.cc/pet-adoption-case-study-febpets-for-you-ux-ui-928a454e365e)

[https://medium.muz.li/pawtner-pet-adoption-app-concept-4e84868645ff](https://medium.muz.li/pawtner-pet-adoption-app-concept-4e84868645ff)

[https://aws.amazon.com/quickstart/architecture/mongodb/](https://aws.amazon.com/quickstart/architecture/mongodb/)

[https://aws.amazon.com/cloudfront/](https://aws.amazon.com/cloudfront/)