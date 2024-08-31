# Note Hub

Simple app for creating and saving Sticky Notes<br/><br/>
Try it out [here!](https://note-hub-rouge.vercel.app/)

## Features

- [x] **Create Notes:** Add any number of notes and re-arrange them on screen accordingly
- [x] **Data Saving:** All notes are stored in the database and can be retrieved at any time

## Tech Stack

- Javascript
- Vite
- React
- Appwrite

## Documentation

### Database Management API

This module provides a set of functions to manage documents in various collections using Appwrite's database service. Each collection is represented as an object with methods to create, update, delete, get, and list documents.

### Import

```
import { databases, collections } from "./config";
import { ID } from "appwrite";
```

### Collections

Each collection is dynamically added to the `db` object with the following methods:

### Methods
```create(payload, id = ID.unique())```
Creates a new document in the collection. <br/>

- **Parameters:**
    - `payload` (Object): The data to be stored in the document.
    - `id` (String, optional): The unique ID for the document. Defaults to a unique ID generated by Appwrite.
- **Returns:**
    - A promise that resolves to the created document.
<br/><br/>

```update(id, payload)```
Updates an existing document in the collection. <br/>

- **Parameters:**
    - `id` (String): The unique ID of the document to be updated.
    - `payload` (Object): The new data for the document.
- **Returns:**
    - A promise that resolves to the updated document.
<br/><br/>

```delete(id)```
Deletes a document from the collection. <br/>

- **Parameters:**
    - `id` (String): The unique ID of the document to be deleted.
- **Returns:**
    - A promise that resolves to the deletion result.
<br/><br/>

```get(id)```
Retrieves a document from the collection. <br/>

- **Parameters:**
    - `id` (String): The unique ID of the document to be retrieved.
- **Returns:**
    - A promise that resolves to the retrieved document.
<br/><br/>

```list(queries)```
Lists documents in the collection based on the provided queries. <br/>

- **Parameters:**
    - `queries` (Array): An array of query objects to filter the documents.
 - **Returns:**
    - A promise that resolves to the list of documents.

### Example Usage

```
const userCollection = db['users'];

// Create a new user
userCollection.create({ name: 'John Doe', email: 'john@example.com' })
  .then(document => console.log('Created document:', document))
  .catch(error => console.error('Error creating document:', error));

// Update a user
userCollection.update('unique-document-id', { email: 'john.doe@example.com' })
  .then(document => console.log('Updated document:', document))
  .catch(error => console.error('Error updating document:', error));

// Delete a user
userCollection.delete('unique-document-id')
  .then(result => console.log('Deleted document:', result))
  .catch(error => console.error('Error deleting document:', error));

// Get a user
userCollection.get('unique-document-id')
  .then(document => console.log('Retrieved document:', document))
  .catch(error => console.error('Error retrieving document:', error));

// List users
userCollection.list([{ key: 'name', value: 'John Doe' }])
  .then(documents => console.log('Listed documents:', documents))
  .catch(error => console.error('Error listing documents:', error));
```

## Acknowledgements

Special thanks to the developers of all tools and frameworks used during the development of this project.
