Adress-book
===========

Simple address book REST API developed using MongoDB and the express.js framework for Node.js 

Features: listing all contacts, adding new ones, modifying, deleting and finding by id and arbitrary string (matching name, surname or phone number)

---------------------
Using the application
---------------------

1. after installing start mongo server

mongod --dbpath <path> --smallfiles


2. starting our server

 node server.js 



3. testing the application

#using  cURL, a command line utility for transferring data with URL syntax

#list all
curl -i -X GET http://localhost:3000/entries

#find by <id>
curl -i -X GET http://localhost:3000/entries/<id>
(#eq.: curl -i -X GET http://localhost:3000/entries/543fff29130cc47257de6309)

#find by name,surname or phone number
curl -i -X GET http://localhost:3000/entries/find/John

#delete
curl -i -X DELETE http://localhost:3000/entries/<id>
(#eq. curl -i -X DELETE http://localhost:3000/entries/543fff29130cc47257de6309)

#add
curl -i -X POST -H 'Content-Type: application/json' -d '{"name": "Jelena", "surname": "Pantovic", "phone": "063559669"}' http://localhost:3000/entries

#update
curl -i -X PUT -H 'Content-Type: application/json' -d '{"name": "Jelena", "surname": "Pantovic", "phone": "0642003029"}' http://localhost:3000/entries/<id>
(#eq. curl -i -X PUT -H 'Content-Type: application/json' -d '{"name": "Jelena", "surname": "Pantovic", "phone": "0642003029"}' http://localhost:3000/entries/5440c5534812bef876004ac0)
