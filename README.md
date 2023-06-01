# About this project
As part of my internship at the university of Sherbrooke on Quantum Dot Autotuning using AI algorithm, I was tasked to 
fully understand the physics of quantum dots. In some stability diagrams, there is a so-called parasite dots that can
make the autotuning task more difficult.

The goal is to first understand how to correctly simulate a single electron transistor (SET) and then a double quantum
dot. Additionally, I had the opportunity to work on dopant detection in quantum dots. Their properties are well known in 
SET but analysis with machine learning of stability diagrams could make their characterisation easier.

# Available parameters
Several simulations parameters can be found in `modelsParameters.json`. Note that for  a large amount of data, json files
are not adapted. Here, to avoid too much complexicity, and useless database treatment, a json file is used to store all
the simulations parameters.

## Why JSON is unsuitable as a database?

1) JSON, quite simply, is not a database. It's not designed to be a data storage format, rather a way of transmitting data 
over a network. It's also often used as a way of doing configuration files for programs.

2) There is no redundancy built in to JSON. JSON is just a format, and Python has libraries for it like json and ujson 
that let you load and dump it, sometimes to files, but that's all it does, write data to a file. There is no sort of DBMS 
(Database Management System), which means no sort of sophistication in how the data is stored, or built in ways to keep it safe and backed up, there's no built in encryption either - bear in mind in larger applications encryption may be necessary for GDPR/relevant data protection regulations compliance.

3) JSON, unlike relational databases, has no way to store relational data, which is a very commonly needed way of storing
data. Relational data, as the name may suggest, is data that relates to other data. For example if you have a table of users and a table of servers, the server table will probably have an owner field, where you'd reference a user from the users table. [This is only relevant for relational data]

4) JSON is primarily a KV (key-value) format, for example {"a":"b"} where a is the key and b is the value, but what if 
you want to search not by that key but by a sub-key? Well, instead of being able to quickly use var[key], which in a 
Python dictionary has a constant return time (for more info look up hash tables), you now have to iterate through every 
object in the dictionary and compare to find what you're looking for. Most relational database systems, like MySQL, 
MariaDB, and PostgreSQL have ways of indexing secondary fields apart from the primary key so that you can easily search 
by multiple attributes.