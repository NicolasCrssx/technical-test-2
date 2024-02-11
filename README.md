# Technical test

## Introduction

Fabien just came back from a meeting with an incubator and told them we have a platform “up and running” to monitor people's activities and control the budget for their startups !

All others developers are busy and we need you to deliver the app for tomorrow.
Some bugs are left and we need you to fix those. Don't spend to much time on it.

We need you to follow these steps to understand the app and to fix the bug : 
 - Sign up to the app
 - Create at least 2 others users on people page ( not with signup ) 
 - Edit these profiles and add aditional information 
 - Create a project
 - Input some information about the project
 - Input some activities to track your work in the good project
  
Then, see what happens in the app and fix the bug you found doing that.

## Then
Time to be creative, and efficient. Do what you think would be the best for your product under a short period.

### The goal is to fix at least 3 bugs and implement 1 quick win feature than could help us sell the platform

## Setup api

- cd api
- Run `npm i`
- Run `npm run dev`

## Setup app

- cd app
- Run `npm i`
- Run `npm run dev`

## Finally

Send us the project and answer to those simple questions : 
- What bugs did you find ? How did you solve these and why ? 
- Which feature did you develop and why ? 
- Do you have any feedback about the code / architecture of the project and what was the difficulty you encountered while doing it ? 

## My Answer

About the bugs :

- The Name field was disabled. At first I thought that it was intended, but after a quick look at the code,
I realized that 1. the users are fetched by their ids so it will not be a problem if two users have the same name, and 2.
two persons could have the same name. So i deleted the 'disabled' property on the field.
After that, there was still a problem : it was related to the fact that in the back-end Schema, the name is called 'name',
while in the front end it is called username on some places. So i decided to put the word 'username' by default. I had to change some things about that whenever the name was fetched from the api.

- Users informations cannot be updated : That was because the OnChange was used instead of the Onclick property.

- Then, the app crashed at two occurences : the first one is when using the search bar for users. It was related to the username problem and also, it was because 'filter.search' could be undefined, so I had to add a '?'.

- The second occurence was when trying to click on a project. It is simply because the api sent an array with one element, the project. But the front-end was develop so that the back-end only return the element that we want. That was due to the use of 'find' instead of 'findOne'. We search a project by its Id so we know that we will only find One. So we can stop at the first occurence and then simply send it back as a result of the request.


Some changes :

- I was not really sure about what a 'win feature' could mean but I added a simple functionnality : in the list of available users, there is a text on the top right saying how many users are available.

- Also, I realized that when the user changes its status, it is not updated in the users list. I added a page reload because I did it the simplest way, but the best way would be to fetch again the list of users, where the availability will have changed.

- I had a problem creating projects, I was getting errors and did not know why. When looking at the console, I realized that it was because the name already existed. So I added an error handling so that there is a toast saying that the project already exists.


About this project :

I was a bit confused at some times because I had no idea of the purpose of the app, and what could be the priorities or the constraints. Apart from that, It was really stimulating being on an app that has a lot of problems and having to correct the bugs by myself. I really liked this challenge, far more than the usual coding tests ! It really confronted me to what I would do everyday in a company like yours.
A little word about the architecture, it was okay, but the fact that the files had the same name in the back-end and in the front-end was a bit confusing.

Thank you for reading 😊
