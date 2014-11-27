#Using MongoDB with KONA

First create an account at mongolab or other cloud mongodb provider.

- https://mongolab.com/
- https://www.compose.io/mongodb/
- https://www.mongosoup.de/

We prefer MongoLab.

Create the connector in KONA, go to KONA -> Services -> MongoDB add the mongodb credendials.

## Getting parameters from MongoLab

[Imgur](http://i.imgur.com/sIuHiLj.png)

and then in KONA we put the credentials

[Imgur](http://i.imgur.com/yusD754.png)

Now, you can test it, with this you can insert one objecto the the 'col1' Collection and see the result

```js
var test = function() {
    var db = kona.mongodb.open('prod');
    var coll = db.getCollection('col1');
    
    var obj = {name : "Kona"};
    var dbObj = toJson(obj); //this step it's important!
    return coll.insert(dbObj);
}

```
#MongoDB KONA Apis

This is the Java SDK with some important changes

## Connect

```js
var db = kona.mongodb.open('prod');
```

###Getting a List Of Collections
Each database has zero or more collections. You can retrieve a list of them from the db (and print out any that are there) :

```js
var colls = db.getCollectionNames();

for (String s : colls) {
    System.out.println(s);
}
```

###Getting a Collection
To get a collection to use, just specify the name of the collection to the getCollection(String collectionName) method:

var coll = db.getCollection("testCollection");

###Inserting a Document
Once you have the collection object, you can insert documents into the collection. For example, lets make a little document that in JSON would be represented as

```js
var myObj = {
   "name" : "MongoDB",
   "type" : "database",
   "count" : 1,
   "info" : {
               x : 203,
               y : 102
             }
}
```

**Important**

Create the db object to insert

```js
var dbObj = toJson(myObj);
```

Insert

```js
coll.insert(doc);
```

###Finding the First Document in a Collection Using findOne()
To show that the document we inserted in the previous step is there, we can do a simple findOne() operation to get the first document in the collection. This method returns a single document (rather than the DBCursor that the find() operation returns), and it’s useful for things where there only is one document, or you are only interested in the first. You don’t have to deal with the cursor.

```js
var myDoc = coll.findOne();
```

###Counting Documents in A Collection
Now that we’ve inserted 101 documents (the 100 we did in the loop, plus the first one), we can check to see if we have them all using the getCount() method.

```js
var count = coll.getCount();
```

###Using a Cursor to Get All the Documents
In order to get all the documents in the collection, we will use the find() method. The find() method returns a DBCursor object which allows us to iterate over the set of documents that matched our query. So to query all of the documents and print them out :

```js
var cursor = coll.find();
try {
   while(cursor.hasNext()) {
       var item = cursor.next();
   }
} finally {
   cursor.close();
}
```

###Getting A Single Document with A Query
We can create a query to pass to the find() method to get a subset of the documents in our collection. For example, if we wanted to find the document for which the value of the “i” field is 71, we would do the following ;

```js
var query = new kona.obj();
query.put("i", 71);

cursor = coll.find(query);

try {
   while(cursor.hasNext()) {
       System.out.println(cursor.next());
   }
} finally {
   cursor.close();
}
```

###Creating A Collection
There are two ways to create a collection. Inserting a document will create the collection if it doesn’t exist or calling the createCollection command.

An example of creating a capped sized to 1 megabyte:

```js
var obj = kona.obj("some,1);
db.createCollection("testCollection", obj);
```

###Dropping A Collection
You can drop a collection by using the drop() method:

```js
var coll = db.getCollection("testCollection");
coll.drop();
```

###Creating An Index
MongoDB supports indexes, and they are very easy to add on a collection. To create an index, you just specify the field that should be indexed, and specify if you want the index to be ascending (1) or descending (-1). The following creates an ascending index on the i field :

```js
coll.createIndex(new kona.obj("i", 1));  // create index on "i", ascending
```

###Geo indexes
MongoDB supports various geospatial indexes in this example we’ll be creating a 2dsphere index which we can query using standard GeoJson markup. To create a 2dsphere index specify the string literal “2dsphere” in the index document:

```js
coll.createIndex(new kona.obj("loc", "2dsphere"));
```

###Text indexes
MongoDB also provides text indexes to support text search of string content. Text indexes can include any field whose value is a string or an array of string elements. To create a text index specify the string literal “text” in the index document:

```js
// create a text index on the "content" field
coll.createIndex(new BasicDBObject("content", "text"));
```

more info at http://api.mongodb.org/java/current/index.html?_ga=1.51794153.1932745298.1411593922
