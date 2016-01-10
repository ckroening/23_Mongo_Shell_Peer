Steps followed to address assignment tasks:

0. setup:  
terminal: mongod (mongoDB started)
new terminal tab: mongo (mongoDB shell)
in mongoDB shell: 
use challenge (challenge database created)
db.createCollection(“bios”)  (new bios collection created)
db.bios.insert(<document data copied & pasted from bios.bson file>)

1. file: queries.bson, created: 
db.createCollection(“queries”)
show collections
(queries is in the list)

2. 	a. find documents that have awards:
db.bios.find({"awards":{$exists:true}})
b. add found data to queries collection:
db.queries.insert({ haveawards: [{<data found from the above command separated by commas>},{},{}] })

3. 	a. find docs that don’t have awards:
db.bios.find({“awards”:{$exists:false}})
b. add found data to queries collection
db.queries.insert({ noawards: [{<data found from the above command separated by commas>},{},{}] })

4.	a. find docs with contribs for OOP or UNIX:
db.bios.find({“contribs”:”OOP”})
db.bios.find({“contribs”:”UNIX”})
b. add found data to queries collection:
db.queries.insert({ OOPUNIXcontribs: [{ <data> }, {}, {}] })

5.	a. find docs with “Turing Award” awards:
db.bios.find({"awards":{$elemMatch:{"award":"Turing Award"}}}).pretty()
b. add to queries collection:
db.queries.insert({ turingaward: [{},{},{}] })

6.	a. find docs with ID’s between 3 and 7:
db.bios.find( {_id: {$in: [4,5,6]}})
b. add to queries collection:
db.queries.insert({ ids: [{},{},{}] })

7.	a. find docs with awards before 2000:
db.bios.find({"awards":{$elemMatch:{"year":{$lt:2000}}}})
b. Add to queries collection: 
db.queries.insert({ awardbefore2000: [{},{},{}] })

8.	a. find docs with birth years, but no death years:
db.bios.find({“birth”:{$exists:true},”death”{$exists:false}})
b. add to queries collection:
db.queries.insert({ birthnodeath: [{},{}] })





